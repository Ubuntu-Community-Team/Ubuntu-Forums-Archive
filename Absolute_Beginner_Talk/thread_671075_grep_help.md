---
title: "grep help"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by hank__ on 2008-01-18
I need some help with grep and a regular expression. I need to search for the number of times words appear in files in all directories.

So, word1 word2 and word3 appear x times in ALL directories. Please help, all I can do so far is 
grep -c word *

which only searches the directory its in and only allows one possible word.

---

### Post by hank__ on 2008-01-18
ok i've now tried:
grep -c 'word1|word2' */*/*/*/*/

Kind of works but I don't really know how many sub-directories there are, plus it doesn't give me a total number of instances at the end.

---

### Post by hank__ on 2008-01-18
*bump* - Any help please.

---

### Post by SOULRiDER on 2008-01-18
Im not 100% sure of this will work but you could do 
```
ls -R | grep word | wc -l
```
lss -R will list all files and directories, grep word filters those that ahve the word you want and wc -l counts the lines. The thing is this will cound the times the reg expression appears in a directory name so say you want to look for the word foo and you have a directory called foobar with 2 files, foobar.h and foobar.cpp it will count 3 instead of two.

What you could do is do
```
ls -R -o | grep word | grep username | wc -l
```
That will show the owner of each file, so if youre the owner if all the files in the sub-directories you can filter the directories containing the files since they wont have your username (or probably wont)

Thats just a seuggestion, theres probably a much better wa to do it..

---

### Post by hank__ on 2008-01-18
ls -R -o | grep word -i | wc -l
That works fine (I think it ignores case) but if I try something like:
ls -R -o | grep 'word -i | grep this is some more text -i | wc -l

it doesn't like the second grep  which would bring back

grep: is: No such file or directory 
grep: some: No such file or directory 
grep:more: No such file or directory 
grep:text: No such file or directory 

(obviously I'm not searching for those words.)

How can I add a 2nd  (or possibly more) expressions?

ls -R -o | grep word -i | grep word2 -i | wc -l
brings back 0 even though
ls -R -o | grep word -i | wc -l
brings back 8.:confused::confused:

---

### Post by SOULRiDER on 2008-01-18
In 'ls -R -o | grep 'word -i | grep this is some more text -i | wc -l' add a \
 to the spaces. 

In 'ls -R -o | grep word -i | grep word2 -i | wc -l' results will appear only if word AND word2 are present.

---

### Post by hank__ on 2008-01-18
ls -R -o | grep This\ is\ some\ text\ -i | wc -l

I've tried different combination's of the \ with the white space but returns with 0
And I know the text is in one of the files, so there should at least be 1 printed to the screen.

---

### Post by SOULRiDER on 2008-01-18
Try with grep "this is some text"

---

### Post by hank__ on 2008-01-18
ls -R -o | grep here\ is\ some\ text -i * | wc -l

This works, but doesn't search all directories.

---

### Post by SOULRiDER on 2008-01-18
It does, its recursive, unless you want tos tart from /, then change ls -R -o to ls -R -o /

---

