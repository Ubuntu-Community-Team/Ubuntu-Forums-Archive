---
title: "How to copy multiple directories in one cp"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2007-02-13
I checked man cp but it wouldn't give me the command to cp several directories (that are all in the same subdirectory) to another directory in one copy.

I also saw various posts on this site but it was for copying multiple files (*.jpg for example) but not directories.

Is there a wildcard for directories like cp *.* /s or something. 

Thanks a million for any help. It sure beats typing cp dir1 /final/desination, cp dir2 /final/desination, cp dir3 /final/desination, etc. :)  

One other thing, if I want to make a script for tar let's say so that I don't have to type it out each time, do I just end the file in .sh? (example: backup.sh)?

Thanks again.

---

### Post by Crooksey on 2007-02-13
```
sudo  cp -r /source/folder /destination/folder/
```

That will do all files/folders/subfolders

I think cp -a will also work.

---

### Post by bruenig on 2007-02-13
For the second question. The file extension doesn't matter. Just make sure that the script is executable and works.

---

### Post by JohnnyAvocado on 2007-02-13
> **Crooksey said:**
> ```
sudo  cp -r /source/folder /destination/folder/
```

That will do all files/folders/subfolders

I think cp -a will also work.


Crooksey, thanks for your help. To clarify my situation is this:

/
   |
   |
Home dir
   |
   |
dir1 dir2 dir3 dir4.....

I would need to copy these directories (and the subdirectories within dir1,dir2,dir3 to the root of "home" dir. I can copy them by:
```
cp dir1 /home
```
```
cp dir2 /home
```
etc
But would like to know if there was a switch I could use to make it just grab all the directories (equivalent to a windows *.* /s command.)

Thanks again.

Johnny

---

### Post by Arndt on 2007-02-13
> **JohnnyAvocado said:**
> Crooksey, thanks for your help. To clarify my situation is this:

/
   |
   |
Home dir
   |
   |
dir1 dir2 dir3 dir4.....

I would need to copy these directories (and the subdirectories within dir1,dir2,dir3 to the root of "home" dir. I can copy them by:
```
cp dir1 /home
```
```
cp dir2 /home
```
etc
But would like to know if there was a switch I could use to make it just grab all the directories (equivalent to a windows *.* /s command.)



Can you really do "cp dir1 /home"? It doesn't work for me. But "cp -r dir1 /home" does, and you can mention all in one command: "cp -r dir1 dir2 dir3 /home".

---

### Post by ComplexNumber on 2007-02-13
> **JohnnyAvocado said:**
> I checked man cp but it wouldn't give me the command to cp several directories (that are all in the same subdirectory) to another directory in one copy.

I also saw various posts on this site but it was for copying multiple files (*.jpg for example) but not directories.

Is there a wildcard for directories like cp *.* /s or something. 

Thanks a million for any help. It sure beats typing cp dir1 /final/desination, cp dir2 /final/desination, cp dir3 /final/desination, etc. :)  

One other thing, if I want to make a script for tar let's say so that I don't have to type it out each time, do I just end the file in .sh? (example: backup.sh)?

Thanks again.
the following  works:
[B] cp -R path-to-directory1[COLOR=White].....[/COLOR]path-to-directory2[COLOR=White]......[/COLOR]path-to-directory3[COLOR=White].....[/COLOR]path-to-directoryX[COLOR=White]......[/COLOR]destination-directory


[/B] 
NOTE: remember to use the "-R"(or "-r") switch when copying directories. if you use the mv command instead of the copy command, you can move whole directories. the -R switch means to copy recursively (ie the directory and everything within the directory)

NOTE 2: if you are copying files to an area that needs root privileges(ie anywhere outside of your home directory), you need to preced the cp command with sudo. if you are moving files to *or from* an area that needs root privileges, you need to preced the mv command with sudo.

---

### Post by JohnnyAvocado on 2007-02-13
Complex,

Thank you so much. I will give that a try.

---

