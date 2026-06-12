---
title: "Awk question"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by opticsnake on 2006-10-19
Beating my head against the wall for an hour now trying to figure out what's wrong with this bit of script:
```
		awk 'BEGIN{FS=","\
			format = "%-13s%-13s%-30s%-13s\n"}\
			key\
			{printf(format,$2,$4,$10,$11)}\
			END{print "Total matches = " NR}' $fileloc

```

The code is supposed to search a csv file ($fileloc) and print out every line that has the string "key" in it (which is a string variable assigned at the beginning of the script  by **set key = $1**.  Instead of printing only those lines matching the key, however, it prints all records in the file.  Any idea what I'm doing wrong?  I know that it's simply a syntax error somewhere but I can't find what I'm doing wrong.  (BTW, this is written for a C shell)

Edit:
OK, changed the code to read as follows:
```

		awk 'BEGIN{FS=","\
			format = "%-13s%-13s%-30s%-13s\n"}\
			/'"$key"'/\
			{printf(format,$2,$4,$10,$11)}\
			END{print "Total matches = " NR}' $fileloc

```
So now it does a proper search and identifies that particular record.  Unfortunately, it still prints out all of the records from the file but now it treats the particular record that I'm searching for differently.  As you can see in the **printf** above, the output should simply be the 2nd, 4th, 10th, and 11th fields from each file but when it reaches any record with a **$key** match, it prints ALL of the fields from that record.

Edit (again):
OK, managed to solve my own problem after another 2 hours.  My problem with the second set of code turned out to be the line breaks.  After placing the **printf** action on the same line as **$key** the additional lines were filtered out and the lines that matched the key were formatted properly in the output.  Final code:
```

		awk 'BEGIN{FS=","\
			format = "%-13s%-13s%-30s%-13s\n"; printf(format,"First Name","Last Name","Email Address","Phone Num")}\
			/'"$key"'/ {printf(format,$2,$4,$10,$11);ttl++} END{print "Total matches = " ttl}' $fileloc

```

I also had to change the use of **NR** to an incremented total and added a header for the output format.

---

