---
title: "computer not working after installing ubuntu"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2006-11-26
I have windows XP on a 9.54 GB hard drive.  I recently put in a Maxtor 14.25 GB hard drive, which I used for data storage but I now plan to install Ubuntu on it.  The installation worked fine on the new hard drive, but when I tried to boot from the hard drive, it tried to load GRUB, then it displayed "Error 21", without loading.  Fortunately, I can still boot from the cd.:)  

Can someone please help me fix the computer?

---

### Post by bodhi.zazen on 2006-11-26
> **purplearcanist said:**
> I have windows XP on a 9.54 GB hard drive.  I recently put in a Maxtor 14.25 GB hard drive, which I used for data storage but I now plan to install Ubuntu on it.  The installation worked fine on the new hard drive, but when I tried to boot from the hard drive, it tried to load GRUB, then it displayed "Error 21", without loading.  Fortunately, I can still boot from the cd.:)  

Can someone please help me fix the computer?

You need to install GRUB into the MBR on the first HD.

[Restore grub](http://doc.gwos.org/index.php/Restore_Grub)

You can also do this from the live CD via the CLI (terminal):

To install GRUB to the MBR:

First boot the live CD

In a terminal type: ```
sudo grub
```

You will get a grub prompt

grub>>     GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub>

At the GRUB prompt type:```
root (hd1,0)
setup (hd0)
quit
```

Re-boot (without the live CD) and you should be good to go....

---

### Post by purplearcanist on 2006-11-26
I tried reinstalling GRUB but I still get error 21.

---

### Post by bodhi.zazen on 2006-11-26
Pleas post the output of:

sudo fdisk -l

Where and how did you install grub ?

---

### Post by gn2 on 2006-11-27
This may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

I would suggest you run fixmbr from recovery on your Windows CD then re-install Ubuntu and Grub to the second drive using the method described in the link.

---

