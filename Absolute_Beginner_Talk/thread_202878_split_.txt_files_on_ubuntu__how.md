---
title: "split .txt files on ubuntu ? how ?"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by St0neD_JunioR on 2006-06-24
I have been searching for quite some time now, and cant find a suitable answer anywhere. :-|  i need to split a big .txt file into smaller .txt pieces so that i can view them without the need to rejoin the files.. any help is appreciated.
Thanks.

p.s. sorry for da n00b questions.just installed ubuntu a week ago.

---

### Post by lamego on 2006-06-24
You have the split command for that.
Read how to use it with:
```
man split
```
Then you can read the text with 
```
cat *.txt
```

---

### Post by St0neD_JunioR on 2006-06-24
im really sorry , but i cat get it working :(  can you tell me the whole procedure step by step ? 
lets say the example file is Example.txt
what do i do next ? please explain it so that you dont have to explain it to someone else next time ;) 

once again sorry for da n00b questions.

---

### Post by IYY on 2006-06-24
[QUOTE=St0neD_JunioR]im really sorry , but i cat get it working :(  can you tell me the whole procedure step by step ? 
lets say the example file is Example.txt
what do i do next ? please explain it so that you dont have to explain it to someone else next time ;) 

once again sorry for da n00b questions.[/QUOTE]

```
split -l100 Example.txt
```

(that l is a lower case 'L')

100 is the number of lines per file. You can, of course, pick any number.

---

### Post by St0neD_JunioR on 2006-06-24
[QUOTE=IYY]```
split -l100 Example.txt
```

(that l is a lower case 'L')

100 is the number of lines per file. You can, of course, pick any number.[/QUOTE]




this is what i get =/

[http://img232.imageshack.us/img232/5656/screenshot14xn.png]("http://img232.imageshack.us/img232/5656/screenshot14xn.png")

and i cant open those files ...... :(

---

### Post by siccness on 2006-06-24
```

sicc@thebeast:~/testing$ dir
sessionplan.txt
sicc@thebeast:~/testing$ split -l 10 sessionplan.txt
sicc@thebeast:~/testing$ dir
sessionplan.txt  xaa  xab  xac  xad  xae  xaf  xag  xah  xai  xaj  xak  xal  xam  xan  xao  xap  xaq
sicc@thebeast:~/testing$ vi xaa

```


Now, follow what I've done. First command I typed was dir (to show a listing), as you can see, only the one file - the file I want to split.
second command is to split the file up, every 10 lines.
third command, again is directory command (to show listing)..now you can see about 18 files. xaa is the first 10 lines of sessionplan.txt, xab is the next 10 lines, xac is the next 10 lines and so forth.

The last command, vi xaa, was just me opening the xaa file in vi editor (to see if it had worked)

---

### Post by St0neD_JunioR on 2006-06-24
[QUOTE=siccness]```

sicc@thebeast:~/testing$ dir
sessionplan.txt
sicc@thebeast:~/testing$ split -l 10 sessionplan.txt
sicc@thebeast:~/testing$ dir
sessionplan.txt  xaa  xab  xac  xad  xae  xaf  xag  xah  xai  xaj  xak  xal  xam  xan  xao  xap  xaq
sicc@thebeast:~/testing$ vi xaa

```


Now, follow what I've done. First command I typed was dir (to show a listing), as you can see, only the one file - the file I want to split.
second command is to split the file up, every 10 lines.
third command, again is directory command (to show listing)..now you can see about 18 files. xaa is the first 10 lines of sessionplan.txt, xab is the next 10 lines, xac is the next 10 lines and so forth.

The last command, vi xaa, was just me opening the xaa file in vi editor (to see if it had worked)[/QUOTE]


yes ! thank you it had worked. but do i view the files via the terminal only ? that is not comfortable at all , srolling down line by line when there is 1,000,000+ lines... and how do i search for keywords ? is there any way for me to view it in an easier way ?

---

### Post by siccness on 2006-06-24
Yeah, you should be able to right mouse click the file(s) in Nautilus (File Manager) and choose to open the file in a program like gedit, openoffice, or whatever other document programs you have installed.

If not, the other ways of doing so:
Open your document editing program (gedit, openoffice word processor etc..), and select the files (xaa, xba etc..[or whatever they're called])

OR, the terminal-way

```
gedit filename
```

---

### Post by IYY on 2006-06-24
[QUOTE=St0neD_JunioR]yes ! thank you it had worked. but do i view the files via the terminal only ? that is not comfortable at all , srolling down line by line when there is 1,000,000+ lines... and how do i search for keywords ? is there any way for me to view it in an easier way ?[/QUOTE]

These are regular text files. You can view them in any editor. 

> and how do i search for keywords ? 

The command line tool "grep" is for that. For example:

grep "somekeyword" file.txt

or if you want to search all files in a directory:

grep "somekeyword" *

---

### Post by St0neD_JunioR on 2006-06-24
[QUOTE=IYY]These are regular text files. You can view them in any editor. 



The command line tool "grep" is for that. For example:

grep "somekeyword" file.txt

or if you want to search all files in a directory:

grep "somekeyword" *[/QUOTE]


no i can view them ! 

omg thank you ppl. all i have to do , to be able to view them... was to rename it to xaa.txt ! :D thanks again ! i will be coming here more often to ask some questions. i dont think i can help anyone yet.well now i can :P teach ppl how to split files. THanks again !

Regards

---

### Post by St0neD_JunioR on 2006-07-14
hi there , i didnt want to open a new topic , so i thought i might as well ask here , cos it is quite messy.. 

anyway , 

i wanted to know how i can extract lines containing the word i search for , so for example im seacrhing for "blahblah" and i need the whole line extracted. the .txt files are big(~20-50mb) and i need to extract all the lines containing that word. plz let me know if you can help...

Regards.

---

### Post by aysiu on 2006-07-14
Let's say you're looking for the phrase *blahblah* in your home directory. Try this: ```
grep -inr blahblah ~/ > extracted.txt
```

---

### Post by St0neD_JunioR on 2006-07-15
ok thanks for that , i tried it , and all i got was an empty file called extracted.txt , how do i choose the file to extract from ? 
thanks .. sorry for n00b questions.


Regards.

---

### Post by St0neD_JunioR on 2006-07-15
> **St0neD_JunioR said:**
> ok thanks for that , i tried it , and all i got was an empty file called extracted.txt , how do i choose the file to extract from ? 
thanks .. sorry for n00b questions.


Regards.


this is what happens now , i get the file extracted but all that is inside , Binary file /home/admin/myfile.txt matches
and no matches ! although they are there 100% sure !

any suggestions ?

---

### Post by aysiu on 2006-07-16
Can you copy and paste (do not retype, describe, or post a screenshot of) the exact command you're typing in and the exact output of this command? ```
cat myfile.txt
``` or ```
cat extracted.txt
```

---

### Post by St0neD_JunioR on 2006-07-16
this is the command i used 

admin@admin:~$ grep -inr blabla myfile.txt > extracted.txt

and this is what i get in the extracted file 

[http://img118.imageshack.us/my.php?image=screenshotcq2.png]("http://img118.imageshack.us/my.php?image=screenshotcq2.png")

any suggestions ?

---

### Post by St0neD_JunioR on 2006-07-16
up

---

### Post by aysiu on 2006-07-16
So you're trying to extract the word *blabla* from the text file *myfile.txt*?

Can you post the output of this command, then? ```
cat myfile.txt
``` so I can see what the contents of *myfile.txt* are?

---

### Post by St0neD_JunioR on 2006-07-16
lol , its 20mb of text...

---

### Post by aysiu on 2006-07-16
I wonder why grep seems to think it's a binary file instead of ascii...

---

### Post by St0neD_JunioR on 2006-07-16
well i cant open the file with gedit ,cos it says that the characters are different or some similar error , so i open the files with my internet browser. maybe thats the reason ?

---

### Post by aysiu on 2006-07-16
Yeah, if it can't be opened with Gedit, Ubuntu must think it's a binary (to-be-executed) file instead of an ascii (to-be-read-as-text) file.

Not sure how to fix that, though.

---

### Post by St0neD_JunioR on 2006-07-16
well thanks for trying ;) 


anyone else have an idea or two ?

---

### Post by Thenotsowyzewun on 2006-07-16
Maybe this? [http://www.redhat.com/docs/manuals/cert-system/tools/7.1/btoa.html](http://www.redhat.com/docs/manuals/cert-system/tools/7.1/btoa.html)

I'm no expert :P. Reading with interest tho :).

---

### Post by St0neD_JunioR on 2006-07-16
i think redhat is different to ubuntu :-|

---

