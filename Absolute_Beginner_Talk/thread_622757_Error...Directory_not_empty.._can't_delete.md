---
title: "Error...Directory not empty.. can't delete"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by ghanu on 2007-11-25
I have had this problem all of a sudden ..i donno how I got this..
if i navigate into the directory in terminal and ls ....this is what i get as output..

[SIZE="3"][B]ls -a
.  .  ..[/B][/SIZE]

its in my first partition...pls can anyone help me....:(

---

### Post by Bothered on 2007-11-25
Try the command (run in the problem directory):

```
ls -Al
```

and see if that shows any files

EDIT: To explain this command: This will list all files in the directory except for "." and "..", and will show detailed information about them.

---

### Post by Martin Witte on 2007-11-25
. is the curent directory, .. is the parent directory. if you only these you should be able to delete that directory given you have sufficient rights
```
martin@toshibap200:~$ mkdir tmp
martin@toshibap200:~$ cd tmp
martin@toshibap200:~/tmp$ ls -a
.  ..
martin@toshibap200:~/tmp$ cd ..
martin@toshibap200:~$ pwd
/home/martin
martin@toshibap200:~$ 
```

---

### Post by ghanu on 2007-11-26
thanx Bothered n Martin., 

 ls -Al 
 gives an output as
 total=0

n even as root i can't delete the directory....a weird problem though...:confused:

```

ls -al 
```
gives an output as 
```

total 24
drwxrwx---  3 root plugdev 8192 2005-11-15 07:59 .
drwxrwx---  3 root plugdev 8192 2005-11-15 07:59 .
drwxrwx--- 12 root plugdev 8192 2007-10-24 19:13 ..
```

plz help....

---

### Post by Bothered on 2007-11-27
Are you trying to delete a device file, in /dev? Files in the plugdev group tend to be hot-plugged media.

---

### Post by ghanu on 2007-11-27
> **Bothered said:**
> Are you trying to delete a device file, in /dev? Files in the plugdev group tend to be hot-plugged media.

no its located in my windows partition (C drive) , n accidentally i had changed the group to plugdev ..i donno how it got created :(

---

### Post by lvleph on 2007-11-27
if you want to delete the directory
```
rm -r /directory/you/want/deleted
```
should work.

---

### Post by nick_h on 2007-11-27
> total 24
drwxrwx---  3 root plugdev 8192 2005-11-15 07:59 .
drwxrwx---  3 root plugdev 8192 2005-11-15 07:59 .
drwxrwx--- 12 root plugdev 8192 2007-10-24 19:13 ..

It is interesting that the current directory "." appears twice in this listing.  I don't know how this can happen.

---

### Post by Martin Witte on 2007-11-27
It is also good to check the content of /etc/fstab, probably your windows partition is a ntfs filesystem mounted as read only. As you're on 7.04 maybe this helps: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Bothered on 2007-11-27
It looks like (as mentioned in the last post) you're trying to delete a file from a volume that is mounted read only. Windows partitions are typically NTFS, which are mounted as read-only by default. To make the partition writable you need to change the type for the partition for the entry in /etc/fstab corresponding to the partition (from "ntfs" to "ntfs-3g").

---

### Post by ghanu on 2007-11-28
> **nick_h said:**
> It is interesting that the current directory "." appears twice in this listing.  I don't know how this can happen.

thats right nick_h, its quite puzzling how a directory can list "." twice ..I think thats the reason why I can't delete the folder. It perceives both as current directory. 

Its located on a fat filesystem n mounted with read-write permissions.:confused:

---

### Post by nick_h on 2007-11-28
What is the output of:
```
ls -ial
```
?

---

### Post by ghanu on 2007-11-30
> **nick_h said:**
> What is the output of:
```
ls -ial
```
?

```
 ls -ial
total 24
7960 drwxr-xr-x  3 root root 8192 2005-11-15 07:59 .
7960 drwxr-xr-x  3 root root 8192 2005-11-15 07:59 .
7959 drwxr-xr-x 11 root root 8192 2007-11-28 18:50 ..

```


nick, this is what I got...........thanx

---

### Post by wormser on 2007-11-30
> **Bothered said:**
> It looks like (as mentioned in the last post) you're trying to delete a file from a volume that is mounted read only. Windows partitions are typically NTFS, which are mounted as read-only by default. To make the partition writable you need to change the type for the partition for the entry in /etc/fstab corresponding to the partition (from "ntfs" to "ntfs-3g").

Bothered, has a good point.  Do you have ntfs-3g installed?  I cannot remember if it is installed by default in Gusty.

```
sudo apt-get install ntfs-3g ntfs-config
```

Applications> System Tools> NTFS Configuration Tool.

Having two . (current directories) could also be the root of the problem.  That would take some investigating if that is the case.  If push comes to shove you can always log into Windows and delete it there.

---

### Post by ghanu on 2007-12-01
as I said b4 its on a fat filesystem drive. And even with windows the same problem exists. two instances of "." is the problem or one of them could b a period followed by a space ie ". " I fear whether I would be able to format the drive atleast.

---

### Post by ghanu on 2007-12-12
Thanx to all those who posted..I just formatted my c: drive and reinstalled Windozz..now no such problems..........thanx ..have got 2 use Windoz just for nokia pc suite and those games...neway thanx :)

---

