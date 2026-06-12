---
title: "I got question before installing Ubuntu."
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by CuriousTeen on 2007-03-25
Hi all,

This is my 1st post here.

I using Dell Inspiron 6000 Latop and my current OS is WinXP Pro.

I'm curious how Linux perform and decide to try Ubuntu on my Dell laptop.

I need help on installing Ubuntu OS into my 160GB 3.5" external USB hard-drive.

See... my current USB hard-drive have plenty of music, video, back-up and software exe file, and I'm still using to back up my dell laptop info.

I want to install Ubuntu into my external USB HD with a multi-boot selection when I start-up my laptop with USB external HDD plugged so I can select either to boot XP or Ubuntu.

Q1) How to I go about it?

Q2) Can such installation be done without clearing/erase my external HD existing datas and still can continue using to back-up my Dell XP file? How?

Unfortunately I will have to drop this idea of installing Ubuntu if Question.2 is impossible.

Looking forward your help on above question. :) 

Thank you

---

### Post by lyceum on 2007-03-25
Yes, it possible to install Ubuntu onto your external hard drive. Yes you can create a partition for Ubuntu. I would not recommend doing though. I tried that on a laptop myself, and I messed everything up pretty bad. I had to re-format the laptop's hard drive. I had to also fix my external hard drive. I will look for the link on how to do it, but I would not try it unless you are ready to break everything and fix it. 

The way it works (if you do it right), when you boot up, have your laptop (or any PC you want to plug it into) set to boot from an external source (USB). When it loads, grub should ask you how.which OS to load. This is where I went wrong. Ubuntu on my extermal drive thought it was the only OS. My laptop thought my external was my main hard drive. 

Make sure this is worth the risk. 

This is basically the same thing...

USB install:
	[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
	[http://doc.gwos.org/index.php/Ubuntuliveusb](http://doc.gwos.org/index.php/Ubuntuliveusb)

USB Live:
	[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by buuntuu! on 2007-03-25
welcome!
lyceum is right, it's a bit trickier installing on an external drive
but you shouldn't be afraid to touch your internal hd: just back up your system to the external and install ubuntu on your internal drive. if you want to get rid of it again you can easily erase ubuntu and repair window$' mbr, there are many threads around...
once you've tried it however,  you will not want to get rid of ubuntu anymore, i think ;)

---

### Post by CuriousTeen on 2007-03-25
:( > **lyceum said:**
> 
USB install:
	[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
	[http://doc.gwos.org/index.php/Ubuntuliveusb](http://doc.gwos.org/index.php/Ubuntuliveusb)

USB Live:
	[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

The guide is too complicated for me to understand... I'm allergy to command line things like that.... :( 


[QUOTE=buuntuu]you shouldn't be afraid to touch your internal hd: just back up your system to the external and install ubuntu on your internal drive. if you want to get rid of it again you can easily erase ubuntu and repair window$' mbr, there are many threads around...
once you've tried it however, you will not want to get rid of ubuntu anymore, i think [/QUOTE]

I not use to other OS operate in the same partition with my current OS.
Anything go wrong, at least Hard disk corrupt but not laptop if i install into external usb HD.

I think I just not install Ubuntu at this moment untill I understand how to install on my USB HD.

Thank you guys

---

### Post by MrKlean on 2007-03-25
First thing you need to do is defrag your xp though.. at least twice ; )

---

### Post by antoz on 2007-03-25
Why don't you try the Live CD for a while before you go inn- head first with an install.
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")
You can learn a lot from the links above, cheers A

---

### Post by macogw on 2007-03-25
I've done the install to external, and it made it so I couldn't boot without plugging in the external.  The trick to making that work is take out the internal drive during install.  Then install Ubuntu on the external one.  Put the internal drive back in.  Now, when you turn on the computer, you go to boot options (F12 maybe?) and pick either main or external and it'll boot Windows if you pick main and Ubuntu if you pick USB.  Make sure the USB drive isn't mounted during install. If you do it this way, it should go well.  This method has never given me a problem (I adopted this method after accidentally installing Feisty to my good hard drive instead of external when I didn't pay attention to drive letters).

---

### Post by lyceum on 2007-03-26
Another thing you may want to try would be getting a second internal hard drive. Installing to that would be easy and safer. I have 2 hard drives in my PC, on with Ubuntu and the other with OpenSuSE (right now, I like to use it to try other flavors from time to time). When you start you PC you would have the option for Ubuntu or XP.

---

### Post by CuriousTeen on 2007-03-26
Hi,

Thank you guys. :) 

I suddently got an idea.

See, My dell laptop have one hard-disk, partition with C: & D: drive and I got F: drive which is my external 160GB USB 3.5" HD.

As for time-consuming, It is impossible for me to transfer F: files to my Dell Hard Disk cos it contain about 40GB.

What I wanna know is there any possible way, using Windows tool or any window designed program can aid me to create anther partition into my external HD and name as G: drive? (without F file erase) 

I already download and use PowerISO to burn into my CD/R just now.

I'll install Ubuntu into G drive using the method call ***'Resize IDE? Master, partition #? (hda?) and use free space'*** or ***'Manually edit partiton table' ***If this possibly can be done, I can set boot-up option and arrange the sequence as follow; CD-ROM, USB, HARD Disk and Fopply Disk.

Or my idea still don't work?

Thanks

---

### Post by CuriousTeen on 2007-03-26
Hi all,

It's me again.

I installed a partition tool program, it allow me to create another partition within the external HD and it call Paragon Partition Manager Pro.

Once it create a partition, the partition was not farmated.
It come with choices of formatting for that particular space

Can you advise me which format to use, choice are as follow:-

   - FAT12 & FAT16
   - FAT32
   - NTFS
   - Ext2
   - Ext3
   - ReiserFS
   - Linux Swap v. 2
   - HPFS

Once It done, do I need to set any value like pri/sec using Windows Computer Management?

Tks

---

### Post by lyceum on 2007-03-26
Actually, once you clean up your hard drive with scan disk, you can do that when you install Ubuntu. It will take the unused portion and make a partition for you. It is very convenient. As long as you have everything backed up it is the way to go. That is how my laptop is set up, Vista on 50 gigs, the rest it Ubuntu.

---

### Post by CuriousTeen on 2007-03-26
> **CuriousTeen said:**
> Hi all,

It's me again.

I installed a partition tool program, it allow me to create another partition within the external HD and it call Paragon Partition Manager Pro.

Once it create a partition, the partition was not farmated.
It come with choices of formatting for that particular space

Can you advise me which format to use, choice are as follow:-

   - FAT12 & FAT16
   - FAT32
   - NTFS
   - Ext2
   - Ext3
   - ReiserFS
   - Linux Swap v. 2
   - HPFS

Once It done, do I need to set any value like pri/sec using Windows Computer Management?

Tks

Thanks.

But I need someone to tell me which format should I go for in order to create the new partition? and Which mode should I select during the installation?

tks

---

### Post by amazingtaters on 2007-03-26
Depends really. I formatted by ubuntu partition to ext3 using the same program, though you could use FAT32 as well. Window's won't be able to read files on the ext3 partition but it will be able to see the files on a FAT32 drive. I've got an external HDD, 80 gigs NTFS and 80 ext3, and then on my main drive I've got 120 gigs for Windows, NTFS, and 40 for Ubuntu on another ext3.

---

### Post by CuriousTeen on 2007-03-26
> **amazingtaters said:**
> Depends really. I formatted by ubuntu partition to ext3 using the same program, though you could use FAT32 as well. Window's won't be able to read files on the ext3 partition but it will be able to see the files on a FAT32 drive. I've got an external HDD, 80 gigs NTFS and 80 ext3, and then on my main drive I've got 120 gigs for Windows, NTFS, and 40 for Ubuntu on another ext3.

Thanks.

I formated my new partition (G:) as Fat32.

I'm stuck during the installation process when ***I choose Manually edit partition table***.

---

### Post by sirkism on 2007-03-26
Just because I read this earlier today.. Haven't had a chance to check it out but it might be worth a look.

[Ext2 Installable File System For Windows]("http://www.fs-driver.org/")

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by lyceum on 2007-03-26
I really recomend reading Psycocat's Ubuntu page before you really get into things. It has some really good walkthroughs and explanations. There is a link in my signature.

---

### Post by CuriousTeen on 2007-03-26
> **lyceum said:**
> I really recomend reading Psycocat's Ubuntu page before you really get into things. It has some really good walkthroughs and explanations. There is a link in my signature.

I read Psycocat's [installing guide]("http://www.psychocats.net/ubuntu/installing") but doesn't feed my method.

My senerio is this:

I already create a G: partition (fat 32) into my F drive.

I wish someone can guide me on ***choose Manually edit partition table***.

I  don't understand ***/, /home, /var, and /boot*** so I can't perform that installation. :( 

I whole day finding the such info but no avail.

---

### Post by amazingtaters on 2007-03-26
I usually juct take the "/" option and no problems have resulted for me.

---

### Post by amazingtaters on 2007-03-26
> **sirkism said:**
> Just because I read this earlier today.. Haven't had a chance to check it out but it might be worth a look.

[Ext2 Installable File System For Windows]("http://www.fs-driver.org/")

[http://www.fs-driver.org/](http://www.fs-driver.org/)



That's awesome. Is there something similar for ext3 partitions?

---

### Post by CuriousTeen on 2007-03-26
Hi,

I finally install into my partition.

I actually format my G: drive into free space.

After that I run live CD, I use Psycocat's installing guide and modify abit.

1GB for my Swap [pri, linux swap]
15GB for for my document [pri, ext 2]
10GB for my / [pri, ext 3]
-------- for my .windows [logic, ---]

I think still not perfect.

Now I got problem.

I set 
1) Floppy (dummy)
2)USB
3)harddisk
4)CD-rom 

error messege = NTLDR is missing, Press Ctr+Alt+del to restart.


If i change to 

1) Floppy (dummy)
2)harddisk
3)USB
4)CD-rom 

It start Ubuntu straight away without giving me choice to select XP or Ubuntu.

Can fix? pls advise.

Tks

---

### Post by agiamba on 2007-03-26
I have exactly the same computer, and almost exactly the same situation. All of my media/programs is saved on my external hard drive. I would highly recommend just partitoning space off your internal HD (Ubuntu live CD can do this without wiping out your XP drive, your data is saved!) and just leaving your external HD fat32 or whatever format it was.

---

### Post by CuriousTeen on 2007-03-26
Opps Sorry ...sorry.

After 20 mins updates, I restart my PC as was told by system.

The selection pop-up, take a look at this... quite strange. 
I snap my screen using Sony ericsson. (wow.... fanastic. I don't need to install driver and it work with Ubuntu... how to unplug USB device?)

[[img]http://upload7.postimage.org/403969/DSC00062.jpg[/img]](http://upload7.postimage.org/403969/photo_hosting.html)

e.g the 1st 4 lines.... 
- ubuntu , kenel......................2.6.17.11 generic
- ubuntu , kenel......................2.6.17.11 generic (recovery.... )
- ubuntu , kenel......................2.6.17.10 generic
- ubuntu , kenel......................2.6.17.10 generic (recovery.... )

I chose - **ubuntu , kenel......................2.6.17.11 generic** once restart.

Is this normal? 
the last two lines seem old version to me.  will it happen to add another new lines whenever I update?

tks

---

### Post by lyceum on 2007-03-26
yes. That is letting you pick between OS's. Good job!

:guitar:

---

### Post by CuriousTeen on 2007-03-27
> **lyceum said:**
> yes. That is letting you pick between OS's. Good job!

:guitar:

Thanks :)

Then how you guys unplug a USB device? Cos Windows have such function so linux?

---

### Post by Tomosaur on 2007-03-27
A USB device generally needs to be ejected. If you are using a storage device (usb flash drive, external hard drive, etc etc), you SHOULD get an icon on your desktop. When you want to remove it, just right click it and select 'eject'.

---

