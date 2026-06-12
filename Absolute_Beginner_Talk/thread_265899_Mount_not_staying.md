---
title: "Mount not staying"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by white on 2006-09-26
I have a 250GB Maxtor Sata drive that I'm trying to use for storage, I've made a partition in it (**sda5**) and mounted that to *~/Storage*.

In fstab I added it also.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda5       ~/Storage       ext3    user,auto       0       0
```

I gave myself permission (at least I think) to access it with:
```
sudo chown ti ~/Storage
```

However, on restart I keep having to mount it and give myself permissions, obviously somethings wrong. :( Theres an easier way of doing this I know. lol

---

### Post by raphha on 2006-09-26
Hi,

looks not too bad. Did you change the directory permissions after mounting sda5? (If not try that). And, you should replace "~/Storage" by "/home/ti/Storage". (The mount -a command is run as root, so "~" means "/root" in this context. If you don't have a directory "/root/Storage", the mount command will fail at boottime. Check you logfiles /var/log/messages or /var/log/syslog for hints)

best regards,
raph

---

### Post by white on 2006-09-26
Ahh, changing it to **/home/ti/Storage** did the trick, thanks raphaa!

:)

---

### Post by white on 2006-09-26
Ok, now my permissions have stopped, I'm only allowed to read to /home/ti/storage. An hour ago it was perfectly fine, I could read/write.
Below is an SS.

I can't figure out why it changed the file group to root instead of keeping it as ti.

---

### Post by JNowka on 2006-09-26
Looks like the owner is root.
 
I would try this:
[LEFT]sudo chown ti ~/Storage[/LEFT]

---

### Post by raphha on 2006-09-27
Why, this looks alright to me. Check your permissions carefully:
You have rwxr-xr-x, meaning,
[LIST]
[*]the owner can r(ead)w(rite)(e)x(ecute)
[*]the group members can r and x
[*]everyone else can r and x
[/LIST]

This is as expected, since you only changed the user with the chmod command. you could have used "sudo chown ti.ti storage" or the chgrp command, check the man-pages for details.

Anyways, for you changing the group doesn't make any difference, since you are ti and you have full permissions rwx, don't you?

raph

---

### Post by JNowka on 2006-09-27
The problem is that the owner of the folder is root.  You using the login ti are not root, you are ti.  The group for ti isn't even root, it is ti.  And as such you will follow the permissions for others.  if you use chown command you will make the folder belong to you.  Only the ti account and the root account will be able to access the folder with full permissions.

---

### Post by raphha on 2006-09-27
JNowka, why do you think the owner is root? :-k 

Did you check the screenshot? After all I can see, it says "File Owner: ti - Devon" and then "File group: root". Since ti is ti and (s)he's the owner of the file and all access bits are set for him/her, I don't see no problem. :cool: 

Furthermore, this is the expected result after an initial situation where the folder belongs to (root.root rwxr-xr-x) and then applying a "chown ti".

raph

---

### Post by JNowka on 2006-09-27
Im am sorry, you are right, my monitor isn't exactly up to spec, and all I could see is root.  The pic seems to be a little fuzzy. 
 
On second glance of the fstab would it help if he changed his options to default? Instead of user,auto Since his home drive is protected, wouldn't it prevent the drive from being seen by anyone else?

---

### Post by raphha on 2006-09-28
I think, the defaults are used anyways, except for the user option. However, since the drive is mounted automatically at boot time as user root, the user option doesn't make any difference in this situation, so he could use "defaults" and nothing would change.

Now, about accessibiliy for others: With the standard (k)ubuntu setup, everyone can enter any other users home directory with r-x perms, and since the drive has 755 perms, everyone can access the storage. Changing the mount options, again, doesn't make any difference in this case. The user(s) options only control who can mount/unmount the drive, not who can access it.
That answers your question?

---

