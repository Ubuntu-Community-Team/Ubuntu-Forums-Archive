---
title: "disc check on every single boot"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by mitch707 on 2007-03-14
on every single boot i get a disc check it checks some files and freezes for 20 minutes and goes to a black screen. I have tried several fresh installs and wiping my hard disk and installing

specs

AMD 64 

1 GB of RAM

nvidia 7300 le card

KN1 SLI lite

200 GB MAXTOR HARD DRIVE

---

### Post by mitch707 on 2007-03-14
help please

---

### Post by mitch707 on 2007-03-14
on every single boot i get a disc check it checks some files and freezes for 20 minutes and goes to a black screen. I have tried several fresh installs and wiping my hard disk and installing

specs

AMD 64

1 GB of RAM

nvidia 7300 le card

KN1 SLI lite

200 GB MAXTOR HARD DRIVE
Edit/Delete Message

---

### Post by annda on 2007-03-14
are you using the regular install or alternate? i believe 64bit AMD processors require the alternate install CD...

---

### Post by ComplexNumber on 2007-03-14
although i don't know for definite, it appears that it may be that ubuntu isnt playing well with 1 or more parts of your hardware. i may be wrong.

---

### Post by mitch707 on 2007-03-14
im using the alternate 64bit and it worked recently until i did a reinstall

---

### Post by v8YKxgHe on 2007-03-14
Perhaps you're hard drive has given up and it's time for a new one?

---

### Post by mitch707 on 2007-03-14
nope only bought it a month ago would reinstalling windows and installing ubuntu over it help ?

---

### Post by MikeSz on 2007-03-14
Thats how ive done it, but then again, I had no end of problems installing Ubuntu from scratch, dont think it liked my graphics card as I got a stream of lines accross the screen.  dont think my problem is related but if you installed windoze it might at least help you establish if there is anything wrong with your hardware, then you can move on to tackling reasons why your install wont work.  

p.s. you havent changed any of your bios settings recently have you? just in case thats caused a change?

---

### Post by igknighted on 2007-03-14
Mitch, we are all volunteers helping on this forum because we love linux.  We are not M$ tech support that you can call and vent at.  We have knowledge that we would like to share with you, but in turn all we ask for is a little respect (for our OS and for the fact that we are volunteering our time to help you) and patience.  Many times your post is not responded to in the first few hours, but eventually someone with some experience comes by and sees it.  The best way to get a quick response is to be as detailed as possible.  Even this thread is rather vague about you problem.

For your current conundrum, I would recommend deleting the "silent" and "splash" lines fro your GRUB boot options (hit 'e' over the menu entry to edit it).  This will tell you exactly what is going on.  Then post back with the *exact* error message you get (or the last thing it does before the screen goes back.  If it is fsck, you can boot into recovery mode (or the live CD) and edit you /etc/fstab file, making the last number in each row a zero to turn off fsck.  This is only a temporary fix, but it should let you boot.

EDIT: Mitch, try the 32 bit version perhaps, 64bit is still new/buggy at times.

---

### Post by nonpareilpearl on 2007-03-14
> reinstalling windows and installing ubuntu over it help

In order to install Ubuntu and Windows on the same machine you *must* install Ubuntu second. The reason for this is how Windows handles dual boots and etc.

Since laptops are manufactured en masse these days, the install disk that they come with isn't usually just Windows XP (or Vista, etc.) but also includes the drivers (same with mass produced desktops such as HP/Gateway/Dell/etc.). When you build your own computer the necessary drivers come separately and some have Linux compatibility. For my desktop, which I built, this is the case. However for my laptop all the drivers are on the "Windows Install" disk, so if you have a computer of this sort you will need Windows (even if only a small partition) on your computer to guarantee that the drivers will be there.

That said I'm sure there are work arounds, so I probably shouldn't make it sound as though this is the *only* way, however it is the simplest and most direct (I think).

---

### Post by mitch707 on 2007-03-14
thanks for all your help i understand you probably do this on your spare time for free. But i have been posting for the past week and hav got no help but no i have and im happy :) so i will try what you said but could this be the problem my mobo has an overclocking program so i loaded the optimized settings

---

### Post by bapoumba on 2007-03-15
@ mitch707: merged in your similar thread.

---

### Post by mcduck on 2007-03-15
Could you post the outputs of 'sudo fdisk -l' and 'cat /etc/fstab' in here? There might be something wrong with your fstab file that causes fsck to run on every boot..

---

### Post by xyz on 2007-03-15
To set check disk number option, run (with all due politeness):
```
sudo tune2fs -c 50 /dev/hdx@
```
Change  50  to however number of times you want disk checked
Change  x  to whatever your partition is.

---

### Post by mcduck on 2007-03-15
> **xyz said:**
> To set check disk number option, run (with all due politeness):
```
sudo tune2fs -c 50 /dev/hdx@
```
Change  50  to however number of times you want disk checked
Change  x  to whatever your partition is.

Remember that this only works for Ext2/Ext3 partitions..

---

