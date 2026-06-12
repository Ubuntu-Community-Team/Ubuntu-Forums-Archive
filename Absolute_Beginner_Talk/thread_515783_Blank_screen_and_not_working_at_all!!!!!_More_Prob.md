---
title: "Blank screen and not working at all!!!!! More Problems than Windows"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Redd Ryder on 2007-08-02
Ok....may as well start here....I have a 2.8Ghz  Intel Dual core comp with 2 320G HD, 3G of Ram, Radeon X1950Pro Graphics Card ...a typical gamers computer... I have installed Windows XP on one hard drive and Linux Ubuntu on the other.....windows works flawlessly as usually....however...Ubuntu only worked once....now I get the blank screen with a busy mouse symbol....the user name screen does not pop up....I try and re-boot in the recovery mode to see if there are any problems....i get this error code
mount: special devices/dev/dist/by-uuid/BA76E7D776E79305 does not exist
I also performed the function 
sudo dpkg-reconfigure xserver-xorg
do all the configurations....however does not recongonize any of my equipment
I forgot to write down the error I get but i believe it was an I/O error 104
I thinking it was a mistake to have this OS....hopefully someone can help me and change my mind
Thanx

---

### Post by apswartz on 2007-08-02
Redd,
I found this thread on LinuxQuestions.org...
[http://www.linuxquestions.org/questions/showthread.php?t=11204](http://www.linuxquestions.org/questions/showthread.php?t=11204)

Perhaps it may be of some help. Let us know one way or the other.

---

### Post by Raineer on 2007-08-02
Doesn't really sound like you want Ubuntu anyways, you might try to open your mind a little and work the problem.  

You say ubuntu has had "more problems than XP", and since you've had ONE ubuntu problem I think you should stay with Windows since it's flawless.

---

### Post by Redd Ryder on 2007-08-02
> **Raineer said:**
> Doesn't really sound like you want Ubuntu anyways, you might try to open your mind a little and work the problem.  

You say ubuntu has had "more problems than XP", and since you've had ONE ubuntu problem I think you should stay with Windows since it's flawless.

Well thanx.....very open....however....this is now the 10 problem in my series of Ubuntu in 3 days...and managed to get it going up to here....however....it is very sad I have to go to Windows to post my problem ...

---

### Post by apswartz on 2007-08-02
Okay, everybody is frustrated ;-)

Redd, did you get a chance to look at the earlier thread I posted? If so, does it seem to relate to your problem?

Your best bet at this point (since you are having so many problems) may be to do a complete reinstall.

---

### Post by Raineer on 2007-08-02
Well I made my post because griping about unecessary things won't get your problem solved any faster.  Stay on topic and people will be more willing to help you through it. aps was nice enough to post an idea, let us know if that pans out.

I do wish you good luck with whatever system you stay with.  I also agree starting fresh would be a good idea. If a fresh install works and *then* breaks after adding pieces to it then we at least have a starting point.

---

### Post by Redd Ryder on 2007-08-02
> **apswartz said:**
> Okay, everybody is frustrated ;-)

Redd, did you get a chance to look at the earlier thread I posted? If so, does it seem to relate to your problem?

Your best bet at this point (since you are having so many problems) may be to do a complete reinstall.

I have installed the Ubuntu 3 times already.....all with the same problems, I have even downloaded the program and copied it onto 3 different disks.....I have looked at the thread however....it didn't seem to go anywhere....it had talked about video drivers.....but never really got an answer out of it...

---

### Post by Redd Ryder on 2007-08-02
> **Raineer said:**
> Well I made my post because griping about unecessary things won't get your problem solved any faster.  Stay on topic and people will be more willing to help you through it. aps was nice enough to post an idea, let us know if that pans out.

I do wish you good luck with whatever system you stay with.  I also agree starting fresh would be a good idea. If a fresh install works and *then* breaks after adding pieces to it then we at least have a starting point.

Well griping but un-neccessary things!!!!!....You think blank screen on Linux is unneccessary problem.....hmmmm......I work with many comp in my field....838 comp.....65 different networks all running either windows NT or XP....also a few MACs.....I'm trying to get our company to go over to Linux for our networking....if I can't get this system to work.....I will not be able to talk anyone else into buying this system....So please...I just want a little help.....unfortunately if you found my statement to be an injustice to the sys....well I apologize....

---

### Post by apswartz on 2007-08-02
> **Redd Ryder said:**
> ...I have looked at the thread however....it didn't seem to go anywhere....it had talked about video drivers.....but never really got an answer out of it...

Hmmm....
The reason I posted it was because of your Error message. It seemed to be the most likely candidate. Do you think the error message maybe coming from another program? If so, do you think you know which one?

Are you able to boot in safe mode?

If not, can you boot off of a LiveCD?

If so, are you able to access your Linux harddrive from it?

---

### Post by Raineer on 2007-08-02
Well for as much crap as I'm giving ya I'm trying to resolve the problem as well ;)  Just stating that comparing it to Windows isn't buying you much...that's what I meant by unnecessary.

Ok, so with the message mount: special devices/dev/dist/by-uuid/BA76E7D776E79305  this means your system is trying to mount something that it can't find or doesn't need to be mounting.

If you can boot from the Live CD can you take a look at /etc/fstab and see if that "uuid" shows up in the list?  The 'uuid' is BA76E7D776E79305, and we need to find out why the machine is looking for it.

You can look at the file via ```
nano /etc/fstab
```, if we edit it you'll have to add "sudo" to the beginning.

---

### Post by Redd Ryder on 2007-08-02
[QUOTE=apswartz;3122242]Hmmm....
The reason I posted it was because of your Error message. It seemed to be the most likely candidate. Do you think the error message maybe coming from another program? If so, do you think you know which one?

Are you able to boot in safe mode?

If not, can you boot off of a LiveCD?

If so, are you able to access your Linux harddrive from it?[/QUOte

Good question...but no I don't.....however when I try to boot in recovery mode...i get this message
mount: special devices/dev/dist/by-uuid/BA76E7D776E79305 does not exist

I can boot off my Live CD however having some difficulty access my drive with Ubuntu on it....I can probably can...but what should I be looking for

---

### Post by Redd Ryder on 2007-08-02
ok....Live cd is working.....I typed in the ternimal....the nano command and this is what I get
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0
/dev/sdb5 swap swap defaults 0 0

---

### Post by Redd Ryder on 2007-08-02
Something weird happened.....I started my computer...I do have dual boot....need to get to my work files but didn't push the button to boot windows fast enough and my Ubuntu loaded up....but the wrong one.....I'll explain....when I first loaded Ubuntu....I had partioned my first hard drive and Ubuntu 16 won't load.....so I decided to make my second hard drive totally Linux....I thought this is what I should have done in the beginning.....however....the new hard drive with the full Linux system won't load either....but my Ubuntu 15 loads from first hard drive......is there something I missed or a step I didn't take....should I now re-format my second drive......now I'm confused!!!!

---

### Post by apswartz on 2007-08-02
Maybe you should share your grub entries here. Do you use grub as your bootmanager, or something else?

---

### Post by Redd Ryder on 2007-08-02
You'll have to forgive me....but not sure what grub is....and not sure what bootmanager I'm using...is there a way to tell....I just assumed whatever was on the disk was your usual boot system

---

### Post by apswartz on 2007-08-02
When you boot up you should get a bootmanager -- a menu that lets you select which operating system you wish to boot up. Grub identifies itself as grub.

Question. What is the order in which you installed all of your OSs?

---

### Post by Redd Ryder on 2007-08-02
ok...then I am using boot manager as I can pick which OS I want.....the computer orginally came with Windows XP.....I had the comp for about 3 weeks....then I decided to try the Ubuntu....I partitioned the hd and loaded Linux....worked for one 1 day.....then I decided to delete the partitions and start fresh on my second hard drive...

---

### Post by Redd Ryder on 2007-08-02
I should also say this is what my screen kinda looks like

Generic 15.0.0
Generic 15.0.0 (recovery mode)
memtest 83 or something like it
Windows XP
then it goes
Generic 16.0.0
Generic 16.0.0 (recovery)
Generic 15.0.0
Generic 15.0.0 (recovery mode)
memtest 83

---

### Post by apswartz on 2007-08-02
It sounds like you are using grub. I get a brief display to go into the menu (see image 1) and then I can see the menu (see image 2). Perhaps it would be helpful to see your grub configuration file.

See if you can give us the output of this command...
```
cat /boot/grub/menu.lst |grep -v \# 
```

BTW, I am really reaching for explanations :-(

---

### Post by Redd Ryder on 2007-08-03
gregg@Gregg-Home:~$ cat /boot/grub/menu.lst |grep -v \#

default         0

timeout         10






















title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f407c5aa-353d-4ed3-a766-c27bece5c4dc ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f407c5aa-353d-4ed3-a766-c27bece5c4dc ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet


title           Other operating systems:
root


title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


title           Ubuntu, kernel 2.6.20-16-generic (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=e09c2390-89c6-485b-99ab-be87775bb595 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


title           Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=e09c2390-89c6-485b-99ab-be87775bb595 ro single 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


title           Ubuntu, kernel 2.6.20-15-generic (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e09c2390-89c6-485b-99ab-be87775bb595 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


title           Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e09c2390-89c6-485b-99ab-be87775bb595 ro single 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


title           Ubuntu, memtest86+ (on /dev/sda2)
root            (hd0,1)
kernel          /boot/memtest86+.bin  
savedefault
boot

gregg@Gregg-Home:~$

---

### Post by apswartz on 2007-08-03
The first three items boot from your second hard drive. Every entry from Windows on boots off of the first hard drive.

Are you selecting the options before Windows or after Windows? If you deleted the partition on your first hard drive then the options after Windows should no long work.

Does the Memtest option before Windows work?

---

### Post by apswartz on 2007-08-03
btw, when you deleted those partitions from the first hard drive, what did you do with the freed up space?

---

### Post by Redd Ryder on 2007-08-03
well that makes sense then.....cus I was trying to boot after Windows....I never have tried the mentest at all in either cases....the free space is now for windows as far as I know when I cleaned up the drive

---

