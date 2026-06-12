---
title: "Mysterious hard drive problem #2"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by kcbear on 2007-01-05
(i decided to repost this, with additions, ](*,) as its been days since ive been able to reply)

Hi, im very new to linux 

i have a 30gb maxtor hard drive partitioned 5gb for ubuntu and 25 for the rest.  for some reason i have to set the jumpers to 'slave' for linux 6.0.6  to boot up. if i set it to master it stops part way through loading when its trying to access root files. 

this wouldnt be too much of a problem except that now im tying to set up a dual os, dual hard drive system, im running into problems getting the computer to recognise both hard drives and getting them both to work. (i'm using IDE connections)

would like to solve the problem of why i need to set jumpers to slave before moving onto trying to solve dual hard drive problem.

ive tried several arrangements with various success

1) set linux hd to master and put in end connector and windows hd to slave and put on middle connector- fails to load linux at 'Mounting root file system'
2) setting both hard drives to cs- fails to detect either hard drive
3) set linux hd to master and in middle or end connector on IDE 1 - hangs at 'waiting for root file system
4) set linux to slave and put in master or slave postion, no windows hd- works fine but hooks up to ISP through dialup even before i log in!
5)linux as slave in end connector with windows as slave in middle connector- hangs after trying to boot from cdrom

any help would be appreciated

---

### Post by teaker1s on 2007-01-05
if I understand correctly
guessing it's a grub problem as altering hard drive position would then alter where grub looks to boot

---

### Post by Sasa_Ivanovic on 2007-01-05
You shouldn't be messing up with hardware if you don't know what are you doing. Find a friend that does, read a book, or call a service.

---

### Post by louieb on 2007-01-05
Don't know why cable select did not work but sometimes it just doesn't.
If it were mine I would go with your option 1.

> 1) set linux hd to master and put in end connector and windows hd to slave and put on middle connector- fails to load linux at 'Mounting root file system'Then follow the link in my signature and reinstall Grub. 
That should get booting into Ubuntu .
This is assuming that when you installed Ubuntu you had a single hard drive and it was set as master and plugged in to the end connector of IDE 0. If you had a different setup when you Installed Ubuntu get back and I bet we can figure it out.

---

### Post by Ocxic on 2007-01-05
Sasa don't be like that, if he does something that breaks his computer he should learn how to fix it himself, it up to him if he want to get some one who knows better. it the best way to learn anyway.

re-installing grub should do the trick.

---

### Post by moshuptrail on 2007-01-05
kcbear -
There are two drive connectors on a typical IDE cable.  If the HD is your only drive it should be plugged into the last (furthest one out) connector and set to either cable select or master.  Do you have more than one cennection slot on the motherboard?  The IDE cable should be plugged into the one marked 0, not 1.

If that is not working, there may be a problem in the motherboard.  But check your bios setting and see if there is any flexibility there.  I've never seen a bios that had it, but just in case. 

If you set the drive as a slave, plug it to the middle connector on the cable.  I'm not sure if that will work, (for an only drive) but at least the cable and the drive selection will be consistent.

Cable select is usually better.  It tells the drive to detect which connector on the cable it's connected to and then decide from that which drive it should be; master or slave.  If you use cable select, and plug the drive to the middle connector, you might get wierd results.  In that case there would be no master drive.  I had my XP system set that way for a long time by accident and it worked.  But that could be a motherboard or bios peculiarity.

P.S. You can edit the grub menu file easily.  sudo gedit /boot/grub/menu.lst
The lines designating boot, should be hd0,0 for the master drive, first partition, hd0,1 for the next partition
hd1,0 is the slave, first partition, hd1,1 is the slave, second partition, etc.  just make sure everything is consistent.

---

### Post by kcbear on 2007-01-06
Hhhhmmm, 

am feeling slightly peeved. My first question on these forums was not replied to. this one, my third, i have recieved a put-down from 'Sasa', who doesnt know enough about me to make those sort of comments and maybe shouldnt be answering the questions of new people if he's going to be so dismisive. just because im new to linux doesn't necessarily mean i'm a newbie to computer hardware. some others dont seem to have read my problem and are giving advice that is already stated as not working(ie, setting hd's to cs does not work). while i appreciate the advice of some who obviously are being helpful i am dissapointed with my experiences with these forums so far. makes me wonder if i made the right decision to try this course. 

i will try and re-install grub and see what happens. thanks again to those who gave me helpful suggestions.

---

### Post by louieb on 2007-01-06
Sorry you feel put down. Especially after spending several days trying to get it going. But you have to admit that your hard drive problem is an oddball situation. You set the jumper to master, plug a drive into the end connector of the first IDE channel   (yea moshuptrail is right i should have called it ide 0 but i think you figured that out) not a good reason that it shouldn't have worked. But there is a bad reason it called  hardware going or gone bad.

---

### Post by oldcotton1 on 2007-01-06
I'm also new here, to Linux / Ubuntu but years of experience as system builder. I have often found that the CS position doesn't do as anticipated and always set systems up with jumpers set for master / slave.  One thing to watch for is the actual jumper positions on the drives themselves.  The old jumper on for master  off for slave doesn't always hold true anymore.  I know setting up my test 6.10 system I had two identical 40GB drives and found out by double checking everything these Samsungs have a position for Master (alone) and Master with slave and obviously another spot for slave.

Just some food for thought.  Other thing to do iif you have your data backed up is to just blow away the install and start from fresh.  I know in my case I was getting some weird things appearing on the drives despite them be fdisked with both Ubuntu and old MSDOS Fdisk.  Low level formatted the drives with a good diagnostic package and the next install went very smooth.


Good luck in your pursuit,

---

