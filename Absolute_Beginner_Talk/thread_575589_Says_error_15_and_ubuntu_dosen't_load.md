---
title: "Says error 15 and ubuntu dosen't load"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by fastfinger on 2007-10-14
When i boot up, it's says Loading Grub then in next line it says Error 15
I am currently booting from live cd, can this be fixed? if not, is there any way for me to save the files?
I have tried fsck
u# fsck /dev/hda1
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Superblock has an invalid ext3 journal (inode 8 ).
Clear<y>?

that is what i get, i think i have already messed up something trying to fix  :<
HALP!!

---

### Post by forestpixie on 2007-10-14
this is what the error mean's I believe, from [here]("http://users.bigpond.net.au/hermanzone/p15.htm#15")
> 
15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

can you post your menu.lst first

```
cat /boot/grub/menu.lst
```

---

### Post by fastfinger on 2007-10-14
# cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

From what i can see, there is no grub folder at all

:/boot# ls -al
total 9358
-rw-r--r-- 1 root root  266735 2006-08-03 05:09 abi-2.6.15-26-386
-rw-r--r-- 1 root root   69903 2006-08-03 02:49 config-2.6.15-26-386
-rw-r--r-- 1 root root 7007887 2006-08-05 23:36 initrd.img-2.6.15-26-386
-rw-r--r-- 1 root root   94760 2005-10-25 10:32 memtest86+.bin
-rw-r--r-- 1 root root  726461 2006-08-03 05:09 System.map-2.6.15-26-386
-rw-r--r-- 1 root root 1414781 2006-08-03 05:09 vmlinuz-2.6.15-26-386

---

### Post by 001100 on 2007-10-14
try reburnung the live cd at 4x then try again

---

### Post by forestpixie on 2007-10-14
I guess you need to restore grub - although not too sure where it's all gone

have a look at these

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

or you could burn [supergrub]("http://supergrub.forjamari.linex.org/?section=download") and try that, works easily and well, usually :)

---

### Post by fastfinger on 2007-10-14
The cd i am using was shipped to be. Is this a cd problem? I have another cd as well, but i don't think it's a cd problem.

---

### Post by alienexplorers on 2007-10-14
Had the same error and ended up reinstalling everything.  I did though mount my /home folder in the live-cd and made a DVD with all my information on it.  Really saved my a**.  I thought I was going to loose everything.  Reloaded Ubuntu this time with 7.10 and everything is working again.

---

### Post by fastfinger on 2007-10-14
alienexplorers , can you tell me how and what exactly you did? If i can save some of my files, i don't mind reinstalling at all

---

### Post by woaiwojia on 2007-10-14
Try to use  another edition  disk

---

### Post by fastfinger on 2007-10-14
I don't have another edition disk and will be almost impossible to get one, I still have no idea about what or how I am supposed to do? :<

---

### Post by fastfinger on 2007-10-14
grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

I remember it's (hd0,0) because I have done this before ( i think) but i seem to have no grub what so ever and this is where i used to find it... So any way to make grub rather then fix it?

---

### Post by forestpixie on 2007-10-15
did you try to use supergrub

---

### Post by fastfinger on 2007-10-30
Okey, osmeone who screws up fsck and reads this post.
leave the partition, install ubuntu in a different partiiton, mount it and recover from lost+found. This is what i am basically doing. After then, always have you root and home on different partition :(
I mate a temp dir and mounted my corrupted drive there
mkdir temp
mount /dev/sda1 /temp

then the temp has lost+found which has all the dir's and files names as #454 etc etc
ls #456 had the name of users and hence realised it was old /home and so forth. Just google up mount and recover lost+found

---

