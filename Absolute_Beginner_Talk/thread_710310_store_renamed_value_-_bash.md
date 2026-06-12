---
title: "store renamed value - bash"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by chelfc on 2008-02-28
hey, I've stored a filename in a variable, lets call it filename. I want to move that to another directory, but if that file exists in that directory, rename the current file by adding a number at the end of it, and so on.

this is what I have done,

I've created a variable with a number 1 in it
create a variable with filename in it
while there is a file with the same name in the directory I wish to move it to
filename=`mv $filename $filename$number`
increment number by 1.

so if it goes back, and there is a filename in that directory, with the number at the end of that number, it will rename the current file by making the number at the end of it 2 instead of 1, and try again. 

however, when I try to run this code, it gives me this error

```
mv: missing destination file operand after 659
```

the number 659 is incremented by 1 and runs in an infinite loop, i have to ctrl+c the shell to stop the program.

---

### Post by Oldsoldier2003 on 2008-02-28
if you are not moving the files out of the source dir you are likely going to loop and rename the same files over and over. just my first impression based on your post.

---

### Post by justleen on 2008-02-28
filename=`mv $filename $filename$number`

if thats you code you use, it wont work.
Your now assign the comman`mv` to the variable filename. your not actually moving it..

just do a mv $file $file$number, and get the filename again afterwards.


think i would do somehing along the lines of:
```

check if file exist
get he file extension 
if extension != number, add number
if == number, add 1 to numer
mv file to file$extension

```
that way you dont care what the file name actually is, you just check the extension.
Offcourse, your files need a "universal" extension to gebin with..



if its just for version management of your files, i would bother would an increment, just use 'date +%s, add it to your file, et voila: unique files

---

### Post by chelfc on 2008-02-28
but I thought that if I renamed the file (variable filename) to a filename with the appended number, like I did above, the while loop will check if the file in the directory I wish to copy to already exists (i.e if a file with the new filename is already in there), if it isn't it will break out of the loop and move the file into the new directory. 

e.g
store a filename called, text.txt in variable filename
store a number 1 in variable 1
while a file called text.txt exists in the directory i wish to move it to
rename text.txt to text.txt1
increment number by 1

if a file called text.txt1 exists (will be checked by while loop above)
rename text.txt1 to text.txt2 
increment number by 1, 
etc until there isn't a text.txt<number> in the directory I wish to move it to.

---

### Post by Oldsoldier2003 on 2008-02-28
> **justleen said:**
> filename=`mv $filename $filename$number`

if thats you code you use, it wont work.
Your now assign the comman`mv` to the variable filename. your not actually moving it..

just do a mv $file $file$number, and get the filename again afterwards.



good catch... i think i need more cofee! lol

---

### Post by justleen on 2008-02-28
Yea, that is the idea :)
 but the way your trying to doing it now, its actually creating the file your checking for.. you will have to check again for the file name..

---

### Post by justleen on 2008-02-28
> I've created a variable with a number 1 in it
create a variable with filename in it
while there is a file with the same name in the directory I wish to move it to
filename=`mv $filename $filename$number`
increment number by 1.

you should try something like 
```
I've created a variable with a number 1 in it
create a variable with filename in it
while there is a file with the same name in the directory I wish to move it to[B]
newfilename=$filename$number
mv $filename $filename$number[/B]
increment number by 1.



edit:
lets just say i was intrigued, but i just wrote this :)
[CODE]#!/bin/bash
DESTDIR="target/"       # where it should go
filename=$1             # grap file name of CMDLN


if [ ! -e  `echo $DESTDIR$filename.0`  ]  #if filename.0 doenst exist -> its a firstimer
then
        echo "moving $filename to $filename.0"
        mv $filename "$DESTDIR$filename.0"

else
       # do a ls on filename*, grep everthing after the ., sort numerical, and grab last line
        lastnum=`ls -1 $DESTDIR$filename* |awk -F '.' '{print $2}' |sort -n |tail -1`  

        newnum=`echo $lastnum + 1|bc `
        if [ -e "$DESTDIR$filename.$lastnum" ] 
        then 
                echo "echo $filename.$lastnum exists, moving to $filename.$newnum"
                mv $filename $DESTDIR$filename.$newnum
        fi
fi
```

by doing the ls, grab and sort your sure your latest files gets the highest number..(i think i;d still prefer to date base this with an ls -1tr |tail -1 to get the last file.. but thats me)

---

### Post by chelfc on 2008-02-28
awesome thanks :D

---

