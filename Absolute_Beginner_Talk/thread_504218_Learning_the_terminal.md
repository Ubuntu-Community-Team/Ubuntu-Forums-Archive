---
title: "Learning the terminal"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by CaptainWookiee on 2007-07-18
Hi everyone.  I am a new ubuntu user, and I love it.  However, I'm still not very comfortable with the command line.  I recently bought a book, "Moving to Ubuntu" (excelent read for new users), which contains some command line uses.  It doesn't really explain, however, to do things like extracting tarballs and cd'ing to directories.  Is there any other resource out there that can explain things like this to me?

thanks a lot

---

### Post by kevdog on 2007-07-18
Im not the best person to give advice, but your obviously trying Ubuntu because you have some interest in computers.  The best tutorial is "doing".  You can read commands from a book all day but you probably will not remember anything, although it is a good reference.  Start by making your own reference

ls - list directory
cd - change directory
tar zxvf - extract .tar.gz file
mv - move 
rm - remove or delete
cp - copy


Thats about all.  For each command there is a manual page. At command line type
man ls
for example.  Man pages are usually very boring but do give very helpful insights into various switches you can use with each command.

---

### Post by RomeReactor on 2007-07-18
Hi. You may find [LinuxCommand]("http://www.linuxcommand.org/") a good site to learn the command line.

---

### Post by aysiu on 2007-07-18
Extract most tarballs: ```
tar -xvzf *filename*.tar.gz
``` Change directory to a subdirectory of your current directory: ```
cd path/to/nested/directory
``` Change directory to a directory specified from the root directory all the way down: ```
cd /from/toplevel/down/to/directory
``` Move up one directory: ```
cd ..
``` Move back to your /home/*username* directory: ```
cd
```

---

### Post by machoo02 on 2007-07-18
Also check out Chapter 12 from the [Linux Newbie Guide]("http://www.linuxnewbieguide.org/chap12.php")

---

### Post by trak87 on 2007-07-18
The most important command at the command line is 'ls', which is for listing the contents of the directory. So get used that one first. But it's even more helpful to use some of the options of ls, like "ls -l". The -l (the letter L) says give me a longer (more detailed) listing of the directory contents. And "ls -lSr" means give me a long listing that is sorted by file size. There are lots more. 

The point here is even if you want to change into a directory, you will most likely need to type 'ls -l' first to see what directories are there.

If you want to learn about any command line command, just type "man <command>". "man" stands for MANual. So try 'man ls' and it will give you all the options for ls. To exit the man page, press q.

---

### Post by Vague on 2007-07-18
This thread has a lot of good resources in it, too:  [http://ubuntuforums.org/showthread.php?t=171507](http://ubuntuforums.org/showthread.php?t=171507)

---

### Post by CaptainWookiee on 2007-07-18
When I try to extract this tarball, this is the message I get:

austine@ubuntu-desktop:~$ tar -xvzf hplip-2.7.6.tar.gz
tar: hplip-2.7.6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
austine@ubuntu-desktop:~$

---

### Post by trak87 on 2007-07-18
> **CaptainWookiee said:**
> When I try to extract this tarball, this is the message I get:

austine@ubuntu-desktop:~$ tar -xvzf hplip-2.7.6.tar.gz
tar: hplip-2.7.6.tar.gz: Cannot open: **No such file or directory**

The file isn't found. Do a 'ls -l' and see if you misspelled it. Or perhaps that file doesn't exist in the current directory.

---

### Post by wana10 on 2007-07-18
linux is case sensitive, make sure you have all the letters in their correct cases.

---

### Post by Nythain on 2007-07-18
tab auto completetion is a godsend in the world of ridiculously long filenames... type the first few letters, and hit tab, it should fill out the rest for your, if the file exists in the directory you are in

---

### Post by cv_zero on 2007-07-18
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

I found this BASH guide quite helpful!

---

### Post by herrdoktor330 on 2007-07-26
> **RomeReactor said:**
> Hi. You may find [LinuxCommand]("http://www.linuxcommand.org/") a good site to learn the command line.


Correction: This is a GREAT Site to learn the quick fundamentals of linux. I found this to be very informative and should be a sticky reference for anyone that wants to use Ubuntu and start to make heads or tails of it.

The first chapter alone explained everything you need to know about linux in a way that an intermediate Windows PC user can understand.

Thanks to RomeReactor for putting this on the forums.

---

### Post by por100pre1 on 2007-07-26
> **CaptainWookiee said:**
> When I try to extract this tarball, this is the message I get:

austine@ubuntu-desktop:~$ tar -xvzf hplip-2.7.6.tar.gz
tar: hplip-2.7.6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
austine@ubuntu-desktop:~$

The question here is where is hplip-2.7.6.tar.gz?

If it is in your desktop try this:

```
cd Desktop

tar -xvzf hplip-2.7.6.tar.gz
```

---

### Post by MQMike on 2007-07-26
Tuxfiles:   [http://www.tuxfiles.org/](http://www.tuxfiles.org/)
Psychocats:   [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) 

Excellent for beginners or s refresher.  
Start with Tuxfiles for command-line basics.
Easy and fun to read.

---

