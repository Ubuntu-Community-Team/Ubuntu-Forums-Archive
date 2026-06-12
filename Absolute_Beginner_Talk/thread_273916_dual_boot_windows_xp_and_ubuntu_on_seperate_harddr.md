---
title: "dual boot windows xp and ubuntu on seperate harddrives"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by conlin on 2006-10-09
Hi guys 
I just got ubuntu and excitied to start messing around with it.
how I did the install is, I installed the ubuntu to a seperat 14 g hard drive and i have 180 g hard drive that has all my xp stuff on it. I mainly  installed the ubuntu on the 14g becuase I just wanted to play around with it and get familar with another os. now that I have installed both OS, I wanted to try to but the xp 180g as the master and the ubuntu 14g as the slave, and at the boot up sequence I was hoping to have the oportunity to choose between xp and ubuntu. What happen is, I cant get both them to get recognized at boot up, no matter what I do, in order to use xp or ubuntu I have to physically remove one and then ad the other. and I'm sick of having my computers apart and changing harddrives manually,
so my question are these

1)can you have both ubuntu and xp os installed on different hard drives and have one as the master and one as the slave.

2) can someone run through the jumpers for me, I'm pretty sure I have it right, i followed the instruction on the harddrives but i cant get the computer to see both. How i had it set up was on master i have a jumper on the 50 and no jumper on the slave

3) also is it possible to have the option to load both os that are on seperate hard drives at start up.

I would love the help, I'm sick of having to change both hard drives manually in order to use one or the other OS,

---

### Post by koshari on 2006-10-09
> 1)can you have both ubuntu and xp os installed on different hard drives and have one as the master and one as the slave.

i cant see why not, i are guessing you may have a conflict on your setup with possably one hdd connected as CS and another as Master, ect, try setting both to cable select and put the drive you want to be master at the end of the cable, or better yet put the 2 hdds on a seperate channel.

> 2) can someone run through the jumpers for me, I'm pretty sure I have it right, i followed the instruction on the harddrives but i cant get the computer to see both. How i had it set up was on master i have a jumper on the 50 and no jumper on the slave

often you will need a master and a slave specificly selected if you want to override the CS preference, this also gets a little hairy with two different brand hdd,s 

> 3) also is it possible to have the option to load both os that are on seperate hard drives at start up.

you can load a linux system on any partitions you like, the key is to load windows first because windows doesnt play well with others.

---

### Post by goodfella on 2006-10-09
As far as having ubuntu and xp on different hard drives with one of them being the master and the other being the slave, it is possible.  It is my exact configuration.  I have xp on a 20 gb drive which is the master and ubuntu on an 80 gb drive which is partitioned 40 gb ntfs for xp and 40 gb seperated into a root, home and swap partition for linux.  At boot up grub gives me the option of ubuntu or xp.

As far as the jumper settings I cannot remember what they physically are on my drives; all I know is that the drive xp boots from is the master and and drive linux boots from is the slave.

I applogize for the lack of help I could give.  I just hope this shows that what you want is possible.

---

### Post by gonesolo on 2006-10-09
> **conlin said:**
> Hi guys 
1)can you have both ubuntu and xp os installed on different hard drives and have one as the master and one as the slave.`


Yes you can quite easily. Once the disks are configured and seen correctly by the bios the trick is to install Windows first and then install Ubuntu and let it install GRUB to the Windows MBR so you get a menu to choose from at boot time.

> 
2) can someone run through the jumpers for me, I'm pretty sure I have it right, i followed the instruction on the harddrives but i cant get the computer to see both. How i had it set up was on master i have a jumper on the 50 and no jumper on the slave


jumper settings change from hard disk to hard disk so any advice given may not apply to your disks. Unfortunatly if you're mixing hard disk manufacturers you could be in for a world of pain. 

Anyway I'll advise what I can. Firstly ignore the CS (Cable select) option on the disks in 11 years I've found it rarely works. 

You are right usually one disk needs to be jumpered master (or Slave present on some disks) and the other as slave. Cable position also plays a factor however. Your master disk should be the last drive on the IDE cable (ie the one furthest from the motherboard) and the slave is the connector midway down the cable.

> 
3) also is it possible to have the option to load both os that are on seperate hard drives at start up.

I would love the help, I'm sick of having to change both hard drives manually in order to use one or the other OS,


As I said above if you get the disks setup correctly and seen in the bios then install Windows and then install Ubuntu you should get the GRUB menu (read as boot menu) which will allow you to select which OS to load.

This works well as it is the configuration I have at home, but I'm using two SATA drives so no master/slave headaches for me, and it works well for me. Any problems either PM me here or e-mail me (gonesolo@imagine.ie) and I'll help anyway I can.

---

### Post by conlin on 2006-10-10
> **gonesolo said:**
> Yes you can quite easily. Once the disks are configured and seen correctly by the bios the trick is to install Windows first and then install Ubuntu and let it install GRUB to the Windows MBR so you get a menu to choose from at boot time.



jumper settings change from hard disk to hard disk so any advice given may not apply to your disks. Unfortunatly if you're mixing hard disk manufacturers you could be in for a world of pain. 

Anyway I'll advise what I can. Firstly ignore the CS (Cable select) option on the disks in 11 years I've found it rarely works. 

You are right usually one disk needs to be jumpered master (or Slave present on some disks) and the other as slave. Cable position also plays a factor however. Your master disk should be the last drive on the IDE cable (ie the one furthest from the motherboard) and the slave is the connector midway down the cable.



As I said above if you get the disks setup correctly and seen in the bios then install Windows and then install Ubuntu you should get the GRUB menu (read as boot menu) which will allow you to select which OS to load.

This works well as it is the configuration I have at home, but I'm using two SATA drives so no master/slave headaches for me, and it works well for me. Any problems either PM me here or e-mail me (gonesolo@imagine.ie) and I'll help anyway I can.

Hey thanks for the help, So i was able to set up both disk drives and i can see the other harddrive in ubuntu but of course i cant read it cuz its in windows, but this brings up different problems,
They are:

Do i have to reinstall ubuntu then reinstall windows in order to get the grub to recognized that I have two os's?

Also is there a way to loging into the grub and get it to recognize both os for example of how you can hit delete before xp loads and it brings you to that basic setup window? because if i can loginto the grub should i not have the option of picking one or the other?

last night I had just windows xp just working and everthing was ok I shut it down and today I cant boot it up, what happens when i get to the windows xp loading page it pauses and then it just reboots and does the same thing just loops. did I ruin my hard drive messing around with it?
also when i load ubunt it recognizes that it is there so is it just a matter of windows having a clitch ? or did i do something really bad to it?

---

### Post by bobpur on 2006-10-10
First of all,(this is for PATA drives) there is a diagram on your hard drive that shows what position your jumpers should be in for master, slave, or cable select. Master and slave are pretty self explanitory and should be placed on the cable accordingly. Master goes on the end and slave goes to the connecter in the middle. The end that goes on the motherboard is furtherest from the one in the middle than the one on the other end (whew!). Which brings us to cable select. With the jumpers set to cable select, the position of the drive on the cable determines its function as master or slave.Some cables take the worry out of being right by labeling the cable connectors. Make sure you have the drive properly jumpered for the connector it's on.
Also, install XP first then ubuntu. If you install in the wrong order, XP overwrites grub and no ubuntu.
To each his own, but, I prefer having my OS's on two different harddrives and a third (an old 10 gb or less) dedicated for swap.

---

### Post by confused57 on 2006-10-11
conlin,
   In Ubuntu, you might want to open a terminal(Applications---Accessories---Terminal), and post the output of:
```
sudo fdisk -l
```
The -l is a small "L".

and

```
cat /boot/grub/menu.lst
```

I have 2 computers set up like this:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

