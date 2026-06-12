---
title: "need help on shell scripting....."
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-05-31
hi,

i have been trying to find duplicate data in a string



for e.g.:

> 
a="sam,day,sun,moon"


i need a program in **Unix/ Linux shell scripting** which will compare the data seperated by commas and see if any duplicate exists.


in the above example **sam,sun,moon,day** are all different texts so the program should return as **"no duplicates"** something like that. and



in case 



for e.g.:

> 

a="sam,sun,ram,sam"



the program should find the duplicate string as **"sam"** and return the same with **"repeated 2 times"**, something like that . if more that one duplicate exists also it should return them 



for e.g.:


> a="sam,san,sam,san,sam"



it should return **"sam duplicate 3 times found and san duplicate 2 times found" ** something like that.

one more thing is this should work for **any number of texts** in the same string...


pls help.....

---

### Post by freebird54 on 2007-05-31
Odd sort of problem.  I am not sure I would try this in a shell script - but perhaps someone more familiar with it would know how.  Personally I would probably fire up the C compiler  :)

Essentially you need to read the string, parse the first substring, and count dupes found, then pick up the second substring, and count its dupes - loop until no more substrings.  Without thought, though, I am not sure whather I would remove the dupes(in the working memory copy) as I find them - so as not to find them again.....  Hmmmm

How long would (could) this string get?  Is it workable in memory, or keep it as a file?

---

### Post by kevdog on 2007-05-31
Im not going to write the shell script for you but it would require the use of associative arrays (awk).

Create a map, with the keys as each values of the elements in the array and the key's associated value as the number of times that value is seen in the array.

You could then print the associate array giving you the count of each key in the array.  Some filtering (conditional statements) could be used to make sure that only keys with values with > 1 are printed.

Just a thought!

---

### Post by sankarv on 2007-05-31
i got it. its easy..


suppose this is the string 


> a="s@S,y@y,s@s,g@g,d@d,G@G"



i can get the duplicates and their count using this command

> echo $a|tr "," "\n" | tr "[A-Z]" "[a-z]" |sort|uniq -cd


The output is:


 > 2 g@g
 2 s@s



i can just format the o/p of my desire after this....


neway thx for the help.....

---

