---
title: "How to copy all hidden files in one directory to another?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-12
I want to copy a few hidden files from one directory to another but it doesn't seem to work with the following cp command:

# cp /etc/skel/.* ./
cp: omitting directory '/etc/skel/.'
cp: omitting directory '/etc/skel/..'

There are two hidden files in /etc/skel but they are not copied into my current directory.

Any help would be deeply appreciated!

Thanks.

---

### Post by codejunkie on 2006-03-12
[QUOTE=Akhran]I want to copy a few hidden files from one directory to another but it doesn't seem to work with the following cp command:

# cp /etc/skel/.* ./
cp: omitting directory '/etc/skel/.'
cp: omitting directory '/etc/skel/..'

There are two hidden files in /etc/skel but they are not copied into my current directory.

Any help would be deeply appreciated!

Thanks.[/QUOTE]
```
cp -R .* /etc/copyfrom /home/username/copyto
``` and if your copying files to anywhere but your home folder you need to add sudo in front of the command to get root access like
```
sudo cp -R .* /etc/foldertocopyfrom /etc/foldertocopyto
```
hope this helps.

---

### Post by Zelut on 2006-03-12
you could do 
> ls -al
inside that directory, showing the hidden files & then copy them by name.. worth a try.

---

### Post by IYY on 2006-03-12
It's the **-r** you're missing. Stands for 'recursive'. You should always use it when moving directories.

---

### Post by Lurid Revenant on 2006-03-12
>>I want to copy a few hidden files from one directory to another but it >>doesn't seem to work with the following cp command:

>># cp /etc/skel/.* ./
>>cp: omitting directory '/etc/skel/.'
>>cp: omitting directory '/etc/skel/..'

try [cp -v /etc/skel/.* ./]
and see what it says when it trys to copy the 2 files..
and I have to ask, are you talking about the /. and /.. because those are not files.  Sorry.. had to ask.

what files are they, that are not getting copied?

try an [ls -l] and make sure u have permission

hope this helps..

---

### Post by AtinLango on 2006-03-12
[QUOTE=kuyaedz]you could do 

inside that directory, showing the hidden files & then copy them by name.. worth a try.[/QUOTE]

Why copy by name? Supposing they are 100 files?

---

### Post by Akhran on 2006-03-12
What I have in /etc/skel are 

/etc/skel/.
/etc/skel/..
/etc/skel/.bashrc
/etc/skel/.bash_profile

If I use -r, will cp copy files in ../ folder too?

Thanks for all the replies !

[QUOTE=Lurid Revenant]>>I want to copy a few hidden files from one directory to another but it >>doesn't seem to work with the following cp command:

>># cp /etc/skel/.* ./
>>cp: omitting directory '/etc/skel/.'
>>cp: omitting directory '/etc/skel/..'

try [cp -v /etc/skel/.* ./]
and see what it says when it trys to copy the 2 files..
and I have to ask, are you talking about the /. and /.. because those are not files.  Sorry.. had to ask.

what files are they, that are not getting copied?

try an [ls -l] and make sure u have permission

hope this helps..[/QUOTE]

---

### Post by Zelut on 2006-03-12
I suggested just by name because he mentioned there were two files he was looking for.  That would just take a second.  Otherwise, as above, the -r recursive definitely does the trick.

---

