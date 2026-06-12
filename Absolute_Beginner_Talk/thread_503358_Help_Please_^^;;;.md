---
title: "Help Please ^^;;;"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by ThatOneDude on 2007-07-17
Hi, let me brief you on what just happend.

I installed Partition Magic 8 so I could make a new partition just for Ubuntu. Well I made one and every went fine until I tried using the Tool called "Install New Operating System" and from then I choose what part. I wanted to use and I choose the new part. And after that it asked how much I wanted space I wanted to use off of it ( and I didn't want to mess with my C: so I choose all the the new part. ). And after that I made that part. run before the other one but AFTER the C: ( hope that makes sense ). And so it rebooted my comp and applied the changes when Windows loaded up and then rebooted after changes were made. Well from then I can boot through Windows anymore it tries to load a new operating system and the Ubuntu that I have on a CD doesn't want to load. And so I tried to repair Windows XP and I tried everything. And so I finally got rid of EVERY part. so only the C: was available. And then I tried to enable stuff, lke boot from system. Turns out it's not in the registry. So I can't run Ubuntu, can't load Windows XP, and I can't re-install Windows XP because the lincense key has been used to many times and so it won't work any more....And to make matters worse I have VERY important stuff on that HD and stuff I CAN'T get rid of ( formatting )....so any options besides using a new HDD to boot from and use this old one for storage? Is there ANYTHING I can do?

Thanks for at least reading o.o;;;;;

---

### Post by scrooge_74 on 2007-07-17
It was rather long I kind of got lost somewhere (plus I have a headache)

Next time use the tool inside the Live CD to repartition a drive before installing.

From what I can make of it you changed the order of booting, hum.  Try this maybe it will get you back

Boot from the Live CD tell it to reset the new partition.  At install time tell it to recognize the XP partition and the Ubuntu one, and install GRUB on the first partition (in the master boot sector)

Also you may want to check this[ website]("http://www.psychocats.net/") , it has very usefull info

---

### Post by ThatOneDude on 2007-07-17
Sorry for the long post lol

Well I can't boot from the CD because it doesn't recognize it. NVIDIA goes through the boot up manager thing and sits there for like 6min and then says BOOT UP FAILED, PLEASE ENTER SETUP DISC AND HIT ENTER even though the disc IS in there x.x;;;

---

### Post by scrooge_74 on 2007-07-17
Weird, is the BIOS set to but from CD?  Do a cold boot= take all power from the system, even unplug it (Dont ask me why, it works sometimes)

---

### Post by ThatOneDude on 2007-07-17
I unplugged the power cord and turned the power off on the back of the computer waited 15seconds put the power cord back in and then turned the power on and pressed the power button to start it up and it still does brings up the NVIDIA Boot Agent.

And the BIOS is setup to read from Removeable -> CD -> HDD o.o;; any other ideas T.T XD....

---

### Post by Zzl1xndd on 2007-07-17
Silly question but I have seen it happen before. How many drives are in the machine sometimes (once or twice i have seen it) people have too many drives and the CD/DVD drives are not spinning up at boot.

---

### Post by ThatOneDude on 2007-07-17
15 CD drives to be exact......j/j lol sorry just 1 o.o;;. And its spinning if that helps and it will run the XP setup but not the Ubuntu CD T.T

---

### Post by skymera on 2007-07-17
i had partition magic.

domnt lwt it fool you with 'new os' crud.

use the live CD ONLY!! to partition riht

---

### Post by ThatOneDude on 2007-07-18
Well I got Ubuntu to work ( the CD ). I burned it again but to another CD and it worked this time. But now I'm kinda having a problem. I want to install and see if I can at least copy all those files and stuff over onto another partition or burn themt o CDs or something. But when installing Ubuntu I don't understand whats going on really

I made a partition and that was 70GB big and I was going to install Ubuntu to it but it won't let me >.<. It asks if I want to resize it and something else. And the the only way I can install it is if I install it to the #1 partition which is my hard drive....and I don't know if thats going to get rid of XP and all of my stuff. Sooo ummm help >.<?

---

### Post by scrooge_74 on 2007-07-18
Read the instructions and follow them it is pretty straight up [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

That partition you made is in what file format? NTFS? Linux needs to reformat it into ext3.  That is one reason it could be asking you to resize it.  When you do it make yourself a separate /home partition so you can store your data there and if you reinstall in the future your data will be safe

---

### Post by ThatOneDude on 2007-07-18
The CD I got from the main site wasn't the Live CD since I had to install it first. So I ended up installing it and I made a 3rd partition and that is only the 70GB big but the problem now is I can only see THAT specific partition and hard drive. Other then that it see's only the CD and Floppy Drives. Soooo....anyway that I can get to the main partition?

---

### Post by scrooge_74 on 2007-07-18
you need to mount the ntfs partition.

Since you used the alternate cd that means you are using Xubuntu, if your system can handle you can then later install regular ubuntu from the internet by sudo apt-get install gnome-desktop

Any way.

Check this instructions  [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+driver+install](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+driver+install)

They explain how to mount your ntfs partition (were XP and your data is)

Good luck post if you dont understand something

---

### Post by ThatOneDude on 2007-07-18
First let me just say that it says Ubuntu not Kubuntu during start up and other than that I'll go start that guide on my computer ( I've been posting on this board on a different computer ) i'll either edit or reply if I have any problems or quests XD, thanks for your help =D

---

### Post by scrooge_74 on 2007-07-18
Oh then you got the other CD, because the alternate CD I use is for Xubuntu (Xfce as my windows manager)

Good luck, the instructions should work ok, since you are editing fstab, by the way I did the manual config and went ok. A few guys around had problems doing the automatic way.  So you should read carefull what you do because a mistake will make your system not to boot

---

### Post by ThatOneDude on 2007-07-18
Ok actually I do need help.......I dont know how to get to the terminal and also I cant type quotes or the apostropheT.T......so thats why dont is just....dont. Other then that Ive been having no problems lol. So I cant exactly start the guide if I dont know how to get to the terminal T.T....so please help lol

---

### Post by scrooge_74 on 2007-07-18
go to applications>accesories>terminal

there is also a shortcut in the keyboard but I just dont remember which one is since I always have a terminal on

humm, I dont get the meaning of typing quotes or apostrophes

---

### Post by ThatOneDude on 2007-07-18
Ummm well I followed that guide and nothing changed the hard drive doesnt show up still.  And I just now tried to install it over again and noticed what the terminal said

>  wget [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc) -O- | sudo apt-key add -
--22:41:00--  [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc)
           => `-'
Resolving flomertens.keo.in... 87.106.24.197
Connecting to flomertens.keo.in|87.106.24.197|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,690 (1.7K) [text/plain]

100%[====================================>] 1,690         --.--K/s             

22:41:01 (831.87 KB/s) - `-' saved [1690/1690]

OK
xxbunnyboyxx@Linux:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ntfs-config: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages
Ummmm....Not sure what to do >.<

---

### Post by scrooge_74 on 2007-07-18
skip to manual config I also got that error message when trying to do it automatically

In the end everything was ok by doing manually.

Do you already know under what name Linux recognize your windows partition?

---

### Post by ThatOneDude on 2007-07-19
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=144db2e4-fd83-4306-95f1-e73fb161ce42 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=9796d92a-829c-400e-aba5-c225bcabd715 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
Ummmm I dont get what its saying lol other than I see that the ext3 is there and than whats the /sda6? Im so lost T.T......

---

### Post by scrooge_74 on 2007-07-19
Good mess it seems you have

i can see the sytem is on sda3 and the swap is on sda6, but it seems it does not show any other 

type sudo fdisk /dev/sda

then when asked type p

to get a list of your partitions

then type q to exit

Good luck I am going to bed so you are on your own

---

### Post by macogw on 2007-07-19
> **scrooge_74 said:**
> 
Since you used the alternate cd that means you are using Xubuntu, if your system can handle you can then later install regular ubuntu from the internet by sudo apt-get install gnome-desktop


WTF?   Xubuntu, Ubuntu, and Kubuntu ALL have alternate CDs.  They all have Live CDs.  I have no idea where you got THAT idea.

---

### Post by macogw on 2007-07-19
/dev means devices
/dev/sda is the first SATA or SCSI device (could be hard drive or optical drive)
/dev/sdb is the second SATA or SCSI
/dev/hda is the first IDE device
/dev/sda1 is the first partition on the first SATA or SCSI device
/dev/sda6 is the 6th partition on the first SATA or SCSI device

if you deleted partitions a bunch of times, you can end up with some numbers missing, like having sda1 sda2 then sda5 with no 3 or 4 because those are partitions you ditched.

---

### Post by ThatOneDude on 2007-07-19
Well Im not exactly sure what to do >.<

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8511    68364576   83  Linux
/dev/sda2           28888       30401    12161205    5  Extended
/dev/sda3   *        8512       28887   163670220   83  Linux
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris
/dev/sda6           28888       29644     6080539+  82  Linux swap / Solaris

Partition table entries are not in disk order

How am I suppose to get files off from other parts of the hard drive? Hopefully you&#314;l answer when you get back XD..........

---

### Post by ThatOneDude on 2007-07-19
Ok well that whole thing didn't help at all and so I reinstalled XP but on a different partition ( the F partition ). And well I went to disc management and so I have my Ubuntu partition and my old XP partition. But they both are just....blank look

[[IMG]http://img216.imageshack.us/img216/9066/untitledpx5.th.jpg[/IMG]](http://img216.imageshack.us/my.php?image=untitledpx5.jpg)

The 65GB is Ubuntu and the 156GB is my old C drive which has XP installed. And so I'm wondering if I can do like a recall or something on the C: drive because that has all my stuff that I need >.<;; and also that was the last name I could use my product key on XP -.-;;;..........................so right now I can't activate XP >.<;;;.............

---

### Post by scrooge_74 on 2007-07-19
From what you posted earlier it looks like at some point you made two swap partitions /sda5 and sda6.

sda3 was the linux partition you had working, but sda1 and sda3 were just only there.

Sorry it seems you did wiped out the drive in the process, probably you inadverntely told the system to format the drive.

At this point there are a couple of tools you can use, but you are going to need a lot more help than what I can give to you on using those.

This are your best bets at getting your data back

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

I have never needed to use them, but  if you make a search here at the forums you will find a couple of threads on how to use them (I have read them so I know they help)

Sorry you got into a crash course of linux.

If you post they will help...

---

