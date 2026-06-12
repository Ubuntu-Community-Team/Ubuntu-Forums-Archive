---
title: "how do i delete *.zip ??"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-11-25
i have a ton of zip files to delete.

if i type in 
del *.zip

i get this error 

bash: del: command not found

if i type this

delete *.zip

i get this error

bash: delete: command not found


what am i doing wrong???

---

### Post by zionvier on 2007-11-25
the command is   rm

so:

rm *.zip 

should do it.

---

### Post by akiratheoni on 2007-11-25
The command to delete files is rm.

It stands for remove :)

So 

```
rm *.zip
```

should delete all zip files in that folder.

---

### Post by zionvier on 2007-11-25
I guess I should give a little more information so if someone finds this thread later asking a similar thing....

rm is remove;  so if you want to remove a file or group of files you can use:
*rm *.zip *     = remove all files ending in .zip
*rm la* *        = remove all files that start with la

some other commands that are useful (and/or dangerous)

*rm -rf folder*    = remove the directory called folder and all files/directories within it.  (**_NEVER_** do *rm -rf /*    that would be VERY VERY bad!)

*rmdir folder *    = remove a directory, but it has to be empty, so if it's not and you know you want everything gone use *rm -rf folder* instead

---

### Post by akiratheoni on 2007-11-25
Just to re-iterate:

I'm guessing by your sig that you know what rm -rf / does, but just to make sure, DON'T USE THAT COMMAND! Never can be too safe :)

---

### Post by stinger30au on 2007-11-26
awesome!!!

thanks.

just learnt something new.

---

### Post by stinger30au on 2007-11-26
> **zionvier said:**
> 
*rm *.zip *     = remove all files ending in .zip
*rm la* *        = remove all files that start with la


can i combine both commands to remove all files starting with la and end in zip and have a command like this

rm la*.zip

is this possible?

---

### Post by The Cog on 2007-11-26
Yes that is possible. 
And very useful. If you wanat to be sure what files you are about to delete, do 
**ls la*.zip**
first, just to list them.

---

### Post by sisco311 on 2007-11-26
In addition to the asterix, the shell also interprets a question mark as a special character.  A question mark will match one, and only one character.
```
ls ??
```will display all two letter  files.
[more...]("http://www.tuxfiles.org/linuxhelp/wildcards.html")

---

### Post by stinger30au on 2007-11-26
WOW!!!

thats for the info guys. Really appreciate it

---

