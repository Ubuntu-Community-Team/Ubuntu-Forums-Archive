---
title: "I don't see a partition"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by thelugnut on 2007-11-23
I have set my partitions as follows:

sda1 for Windows XP

sda2 to be used for my data stuff

sda3 Ubuntu 7.10 (Gutsy)

On my desktop I see sda1 and sda3.

I cannot see or find sda2.

I have read the "similar threads" and didn't see anything like this.

> How to partition ubuntu onto a seperate partition, leaving backup partition untouched 
 	
Can I safely enlargen Linix partition on drive shared with a DOS partition? 
	
Used Partition Magic to resize Ubunut partition and Grub error 22 ensued after reload
 	
Windows corrupts linux ext3 partition when formatting other FAT32 partition 
	
Removing windows partition and allocating the free space to my ubuntu partition?

I have tried to edit  /etc/fstab but was unsuccessful. After adding sda3, I could not save it. I do not have permission to save it. I am the only user on this computer, so that is just one more thing I don't understand.

Can someone give me a hand here?

Thanks

---

### Post by kaklehona on 2007-11-23
I can at least help you with your problem about permission to do things. Whenever you get that message, try running the command/program as superuser instead. If you write like this in your terminal:

sudo command

and press enter, the computer will ask you for your password first and then you get to do whatever you wanted to.

I also have a partition I do not see unless I use the mount command and mount it. Unfortunatly I can not remember the exact syntax, since I do not often mount it (and when I do I just tell my nerdy husband to help me...)

---

### Post by conjur3r on 2007-11-23
Can you copy/paste the following:

# sudo fdisk -l

---

### Post by thelugnut on 2007-11-23
I appreciate the response and will search around a bit for the "mounting" command.

---

### Post by thelugnut on 2007-11-23
Hi conjur3r, Can I have a hint as to what this does? I know a little about "fdisk" from the MS OS. Is it the same here?

---

### Post by conjur3r on 2007-11-23
It lists all partitions of all of your hard disks.  From the man page: 

> 
       -l     List  the  partition  tables  for the specified devices and then
              exit.  If no devices are given, those mentioned in  /proc/parti&#8208;
              tions (if that exists) are used.


---

### Post by Cannaregio on 2007-11-23
> **conjur3r said:**
> Can you copy/paste the following:

# sudo fdisk -l

Yep, that's the first step to understand what's going on
So please post
```
[SIZE="5"][COLOR="Blue"]sudo fdisk -l [/COLOR][/SIZE] 
```

Also you don't need to ask for 'a hint at what it does': just use
```
 man fdisk 
```
to check what fdisk (or any other command) does by yourself.

---

### Post by thelugnut on 2007-11-23
I am late posting back, because we had an electrical outage in  my building and it bonked the computer. It took me all day to get things back up.

Anyway, thanks for the responses. I have the partition thing all sorted now. . 

I appreciate the replies from everyone.

:guitar:

---

