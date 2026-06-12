---
title: "[SOLVED] fstab read-only"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by darco on 2007-10-14
I made a change to my fstab so on boot up I can no longer get to the desktop. In recovery mode I run  sudo nano -w /etc/fstab, make my change but  I get an error that its read-only. Please help!

thxs
darco

---

### Post by wormser on 2007-10-14
Check the permissions on the file with **ls -l**.

```
ls -l /etc/fstab
-rw-r--r-- 1 root root 538 2007-07-18 22:13 /etc/fstab
```

If is does not look like my results above then try:

```
sudo chmod 644 /etc/fstab
```

---

### Post by darco on 2007-10-14
> **wormser said:**
> Check the permissions on the file with **ls -l**.

```
ls -l /etc/fstab
-rw-r--r-- 1 root root 538 2007-07-18 22:13 /etc/fstab
```

If is does not look like my results above then try:

```
sudo chmod 644 /etc/fstab
```

I ran the first command and it shows exactly your output.
I also tried chattr -t /etc/fstab but no luck....

dr

---

### Post by wormser on 2007-10-14
> **darco said:**
> I ran the first command and it shows exactly your output.
I also tried chattr -t /etc/fstab but no luck....

dr

Well, chattr was going to be my other idea to check.  I would then recommend booting into a LiveCD and making the changes that way.

---

### Post by bodhi.zazen on 2007-10-14
Can you elaborate on the changes you made and error message you are getting on booting ? Is mounting / giving you errors -> re-mount as read only ?

editing from a live CD is not a bad idea.

---

### Post by darco on 2007-10-14
I was able to use the Knoppix Live CD but I am still unable to edit the fstab file...
I may be going at this wrong...This is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=df1b04b8-bd61-4867-81aa-b0dad1c5c24a /               ext3    defaults,[COLOR="Red"]errors =remount-ro,data=writeback,noatime 0 [/COLOR]
# /dev/hda5
UUID=edc3ca0c-0941-44a1-88dd-0756e5c307d4 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5               /mnt/win             ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser,data=writeback 0 1              
/dev/hdb7               /mnt/xp               ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser,data=writeback 0 1

I believe  (hda1) the error  is the space between "errors =remount".  Once I load the LiveCD, I navigate to media/hda1 where I see all my Ubuntu files but again when I try to edit the fstab I get an error saying its read-only?
dr

---

### Post by darco on 2007-10-14
Ok, chalk that up as another learning experience. After booting up Knoppix, I was able to change permissions of the fstab file after numerous tries...I am good to go....
darco

---

### Post by bodhi.zazen on 2007-10-14
\o/

---

