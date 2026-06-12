---
title: "Grub menu disappeared"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by mike23 on 2008-01-17
hey i have ubu7.10 and xp dual boot for games...
after xp became almost unusable due to viruses i decided to format the xp partition...
now it only boots into xp :S
help!! :(

ps: i got only one hdd


thanx!

---

### Post by cecure on 2008-01-17
try looking at this [http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")

---

### Post by dcstar on 2008-01-17
> **mike23 said:**
> hey i have ubu7.10 and xp dual boot for games...
after xp became almost unusable due to viruses i decided to format the xp partition...
now it only boots into xp :S
help!! :(

ps: i got only one hdd


thanx!

Do a forum search for "reinstall grub".

---

### Post by mike23 on 2008-01-17
hey cecure, thanx... 
This appears to be very simple:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

The thing is that i dont know my  harddisk + boot partition numbers.... :S
any ways to find that out?

---

### Post by cecure on 2008-01-17
Alrighty to find the hard drive and partition run the command in terminal,
```
sudo fdisk -l
```

if you need help deciphering it post the output here.

cheers

---

### Post by mike23 on 2008-01-17
ok this is what i get
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12749   102406311    7  HPFS/NTFS
/dev/sda2           12750       38913   210162330    f  W95 Ext'd (LBA)
/dev/sda5           12750       31871   153597433+   7  HPFS/NTFS
/dev/sda6           31872       38849    56050753+  83  Linux
/dev/sda7           38850       38913      514048+  82  Linux swap / Solaris

so my guess is that i shoud type:
grub  then
root (hd0,5)
and i get
Error 21: Selected disk does not exist

any ideas... ? i want my ubuntu back :(

---

### Post by cecure on 2008-01-17
Alright,
you have the right root (hd0,5),

your problem is (I think) that your hard drive is mounted.  What you need to do is use the live cd and make sure that the disk is unmounted.

Try this:
Boot into the live cd and go to a terminal enter:
```
sudo umount /dev/sda
```

and then try the reinstall procedure

good luck

---

### Post by mike23 on 2008-01-17
im on it right now

thanks very much....

---

### Post by mike23 on 2008-01-17
ubuntu@ubuntu:~$ sudo umount /dev/sda
umount: /dev/sda: not mounted


still get the error:(:(

---

### Post by cecure on 2008-01-17
I tried my last step just for fun and it didnt work for me, so I got back on it and found a way that works on my laptop i forgot to tell you to use sudo privileges.

Goto a terminal and try this:
```
sudo -s
grub
find /boot/grub/stage1

```

this will return a value, probably (hd0,5).

then use 
```
root (hd0,5)
setup (hd0)
```

reboot and cross your fingers

---

### Post by mike23 on 2008-01-17
!!!! success  
im now into my ubuntu os....
i just cant thank u enough cecure... :):)

i'll keep these commands somewhere safe for future reference :)

---

### Post by jarelkamar on 2008-01-27
worked for me also , thx very very much cecure .

---

