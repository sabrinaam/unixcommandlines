## Miscellaneous commands I've been using for file editing and more.

Some commands might be repeated, I'm using this repository to store everything I'm using and may use again in the future.

##### Many thanks to Dr. Fernando Baldi, Dr. Gota Morota, Dr. Sabrina Kluska, Dr. Daniela Lourenco, and so many others that shared their knowledge with me.


### 1. Change comma separation to TAB
 ```
 sed -e 's/,/\t/g'  input > output
```
### 2. Separate a file by columns
```
column -t filename > output
```
### 3. Cut the first 10 columns of a file 
```
cut -d$'\t' -f 1-10 NAMEOFFILE.txt > NAMEOFFILE2.txt 
```
### 4. Makes the last line the header
```
sed '1h;1d;$!H;$!d;G' nameoffile 
```
### 5. remove ^M from files edited on Windows and uploaded to Linux.
```
sed -e "s/^M//" filename > newfilename 
```
__OBS__: To enter ^M, type CTRL-V, then CTRL-M. That is, hold down the CTRL key then press V and M in succession.

### 6. Remove the first 5 characters from any line in a file
```
sed 's/^.....//'  input>output  
```
### 7. Remove last character from any line in a file
```
sed 's/.$//' 
```
### 8. Change space separation to TAB
```
sed 's/ /\t/g' input>output  
```
### 9.  Count columns
``` 
awk '{print NF}' input>output 
```
### 10. Join the header file with the data file, one under the other
```
cat HEADERCFILE FILEWITHNOHEADER > output 
```
### 11. Sort file by the 1st column
```
sort -k1 input > output 
```
### 12. Creating a new file with columns 2, 1 and 3 from another file
```
awk '{print $2,$1,$3}' input>output 
```
### 13. Join two files into a new file just by pasting one next to the other
``` 
paste input1 input2 > output 
```
### 14. Open a very large file on linux
```
less -S nameoffile 
```
### 15. Cut the first line of a file
```
sed 1d input > output 
```
### 16. Cut the first column of a file
```
cut -‐f1 -‐d" " input>output 
```
### 17. Cut the first column and create a new file from the second column to the last.
```
cut -d " " -f 2- input>output 
```
### 18. Take only the first 11 lines of a file
```
awk 'FNR>=1 && FNR<=11' input>output 
```
### 19. Remove header
```
echo "$(tail -n +2 input)" > output 
```
### 20. Run a command that will take a while to complete without stopping in a server
```
nohup ./command_that_will_take_forever_to_complete & 
```
### 21. Find out if two files have non-matching animals
```
grep -vwF -f id1.txt id2.txt > id3.txt 
```
- This file contains the animals that are not in common... that is, animals that have a phenotype.

__OBS__: print strings that are not common when comparing two different files. the output will be all the different values/animals/sentences between the two files. In the example above, I wanted to know which animals had phenotype and not genotype (the number of animals genotyped was lower). I just wanted to work with phenotyped animals that had a genotype, that is, to exclude individuals without genomic information.

### 22. Join files by column
```
join  -1 1 -2 1 <(sort -k1 input1) <(sort -k1 input2) > output 
```
### 23. Change file permissions
```
chmod u+x nameofexecutable 
```
### 24. Add a column named fernando (fernando all the way down the file)
```
awk '{print $0, "Fernando"}' input>output 
```
### 25. Count lines in a file
``` 
wc -l nameoffile 
```
### 26. Choose rows above a given value in the 9th column
```
awk '{if($9>=1.0)print;}' input> output 
```
### 27. Prints lines from a file that contains a pattern.
```
grep 'pattern' file1
```
### 28. Returns the first lines of the file
```
head -n nameoffile 
```
### 29. Returns the last lines of the file
```
tail -n nameoffile 
```
### 30. Join 2 files by identical animal IDs
```
join  -1 1 -2 1 <(sort -k1 id_GENO.txt) <(sort -k1 P120_Genotipados.txt) > P120_FINAL.txt
```
__OBS:__ id_GENO: is a file with IDs for genotyped animals. In this case, the output is a phenotype file for animals that have genotypes. 

### 31. Change TAB to space separation
```
expand -t 1 filename > output
```
### 32. Replace NA for 0
```
sed 's~NA~0~g' pheno5.txt >pheno6.txt 
```
### 33. ZIP a directory
```
tar -zcvf archive.tar.gz directory/  
```
### 34. Copy a whole directory 
```
cp -r /work/course2022/week2/day10/ .
```
### 35. Append content at the end of the file
```
cat file3 >> output_file2
```
### 36. Merge files line by line with a space delimiter 
```
paste -d " " input1 input2 > output
```
### 37. Sorts a file in alphanumeric order (ex: sort -k 2,2)
```
sort -k startfield,endfield filename > output 
```
### 38. Sorts a file in numeric order
```
sort -nk startfield,endfield filename > output
```
### 39. Sorts a file in reverse numeric order
```
sort -nrk startfield,endfield filename > output 
```
### 40. Sorts based on column 1 then column 2
```
sort -k1,1 -k2,2 filename > output
```
### 41. Merge two files buy column 1 but suppress the joined output lines. Good for find who is not in one of the files
```
join -v1 phenotypes.txt pedigree.txt > output
```
### 42. Shows all lines that do not match the pattern
```
grep -v PATTERN filename 
```
### 43. Substitution of a pattern 
```
sed -e 's/UGA/SA/g' pedigree.txt > SA_pedigree.txt 
```
__OBS:__ replaces UGA with SA in the pedigree file.

### 44. Change the pattern on a specific line 
```
sed -e '24s/UGA/SA/' pedigree.txt > SA_pedigree.txt 
```
__OBS:__ In this case, line 24.

### 45. Remove a pattern from a file
```
sed -e '/pattern to match/d' file > output
```
### 46. Print column 1 and last column of a file
```
awk '{print $1,$NF}' filename>output 
```
### 47. Print all columns
```
awk '{print $0}' filename>output
```
### 48. Print column 1 based on occurrence in column 2
```
awk '{if ($2==2) print $1}' filename>output
```
### 49. Print columns 3 and 4 skipping the first 1000 lines
```
awk '{if (NR>1000) print $3, $4}' filename>output 
```
### 50. Print length of column 2 from line 1 (count how many SNPs we have)
```
awk '{if (NR==1) print length ($2)}' filename
```
### 51. Counts how many entries there will be for an animal
```
awk '{print $2}' filename |sort| uniq -c >output 
```
__Example:__ How many progenies an animal has. In this case, the sire was column 2.

### 52. Check how many animals in a column has a certain genotype code

In this code, reference allele is __A__.

- Missing genotypes (coded as __5__):
```
awk '{print substr ($2, 7, 1)}' genot_pic.txt | awk '$1==5' | wc -l 
```
- AA (coded as __2__):
```
awk '{print substr ($2, 7, 1)}' genot_pic.txt | awk '$1==2' | wc -l  
```
- Aa (coded as __1__):
```
awk '{print substr ($2, 7, 1)}' genot_pic.txt | awk '$1==1' | wc -l  Aa 
```
- aa (coded as __0__):
```
awk '{print substr ($2, 7, 1)}' genot_pic.txt | awk '$1==0' | wc -l  
```
### 53. Calculate allele frequency
```
awk '{print substr ($2, 7, 1)}' genot_pic.txt | awk '{sum=sum+$1} END {print sum/(2*NR)}'
```
### 54. Copy a file from a server to your local direcoty
```
scp serveraddres:work/ads-guest37/.day12/pheno.dat /pathinyourlocaldirectory
```
### 55. Calculate the average of a column using awk
```
awk '{sum+=$5} END { print "Average = ",sum/NR}' nameoffile
```
- Note: In this case, the column I wanted the average was column 5, represented as $5.

## 56. Print the header from a file in an output with the header displayed as columns

```
 head -n1 nameoffile | tr , '\n' > output
 ```
 
 ## 57. Convert tab to spaces
 
 ```
 expand -t 1 input>output
 ```
 
## 58. Send a file from yout Desktop to a server

```
scp -P 22 file  sabrina@server_number:~/ 
```

## 59. Create a column with a constant number

```
awk -F '\t' -v OFS='\t' '{ $(NF+1) = NUMBERYOUWANT; print }' infile >outfile
```
