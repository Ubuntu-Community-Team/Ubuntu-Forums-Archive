---
title: "[SOLVED] Safely Removing Ubuntu"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-11-14
No, it's not what it seems. I do not want to get rid of Ubuntu, just safely remove it, without harming other partitions.

You see, my Sister runs Dapper on her system with a dual-boot of Windows Media Center Edition... She uses that to play Chessmaster 9000 and First to Fight. I myself am always up for new and exciting challenges, whereas she is not quite so.

So here is what I want to do.
Either Safely remove Ubuntu (I know there has to be some links out there on this), so that Windows will still be there and be able to boot.
Or, Overwrite the old Ubuntu Partitions and install either Feisty or Gutsy on her system.

Any advice would be appreciated as what to do :)
Thanks,
Dr Small

---

### Post by Znort_Ubern00b on 2007-11-14
[Try this link]("http://ubuntuforums.org/showthread.php?t=611450")

Someone already asked and solved that tpoday

---

### Post by Inxsible on 2007-11-14
> **Znort_Ubern00b said:**
> [Try this link]("http://ubuntuforums.org/showthread.php?t=611450")

Someone already asked and solved that tpodayThat link is for removing Windows, not Ubuntu which is what Dr. Small wants.

I would recommend simply installing the newer Ubuntu over the existing partitions, unless you also want to change the partition tables and the sizes of those partitions.

---

### Post by Znort_Ubern00b on 2007-11-14
ooops sorry  :(

---

### Post by Dr Small on 2007-11-14
> **Znort_Ubern00b said:**
> [Try this link]("http://ubuntuforums.org/showthread.php?t=611450")

Someone already asked and solved that tpoday
Thank-you for the suggested reading,
but it seems to be the other way around :p

I'll keep looking though ;)

---

### Post by Dr Small on 2007-11-14
> **Inxsible said:**
> That link is for removing Windows, not Ubuntu which is what Dr. Small wants.

I would recommend simply installing the newer Ubuntu over the existing partitions, unless you also want to change the partition tables and the sizes of those partitions.
Ok. That is what I thought about, but was wondering if it would be easier to delete the Ubuntu partitions and just install from scratch.

Thanks :D

---

### Post by Inxsible on 2007-11-14
> **Dr Small said:**
> Ok. That is what I thought about, but was wondering if it would be easier to delete the Ubuntu partitions and just install from scratch.

Thanks :DBut you don't have to delete the partitions. You can simply install over them, and BAM you will have your new OS. The installer will have to work less too (since it won't be necessary to format those partitions).

But again, if you plan to change the sizes of the partitions, then you are better off deleting them and re-creating them with different sizes.

---

### Post by LowSky on 2007-11-14
go into windows
right click on the icon for my computer
click on manage 
go to storage>disk management
find ubuntu partition and delete it reformate or resize the drive

then grab windows install disc
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

---

### Post by Dr Small on 2007-11-14
> **Inxsible said:**
> But you don't have to delete the partitions. You can simply install over them, and BAM you will have your new OS. The installer will have to work less too (since it won't be necessary to format those partitions).

But again, if you plan to change the sizes of the partitions, then you are better off deleting them and re-creating them with different sizes.
Ok, that is fine. She probably doesn't want the partitions resized, as it works out quite fine right now.

So, is there any tutorial on how to do this ?
I would not mind it so bad if it was my system and I was fooling around on it, and accidentially did something wrong, but when you have a heated sister, breathing down your neck the entire time, it would be a little simpler to follow a guide, since I have never done this before :D

@LowSky:
I can't go that route then, because there is no Windows Disc. This was a preinstalled system when we bought it, and it had no Windows Discs with it, so that won't work :p

Dr Small

---

### Post by Inxsible on 2007-11-14
first download and burn the disc (whichever Linux distro you want).

During the installation process, make sure you install the root and the /home drive in the same partitions that currently exist. Check mark the format partition option only for the root and the home(if you have a separate home ie) 

Simply mount the other partitions, if any. Also make sure that you do NOT format any other partitions.
Once you start up the installer, its pretty intuitive.

---

### Post by Dr Small on 2007-11-14
Ok. I am a little confused. I do not see a Root Mount Point.
Maybe you all could guide me through this, while I am here right now....

I'll get to the screenshot in a second.
I installed the Restricted Nvidia Drivers, got my resolution to work after I restarted Xorg, but now I can not see my cursor :p
So, it's a little difficult to move the mouse and see where it is at ;)

Screenshot of Partitions:

---

### Post by Inxsible on 2007-11-14
Since you have only 1 ext3 partition, I am assuming thats where the current Ubuntu install is. Also you do not have a separate home drive, which means after the install you will have to configure all the applications again.

You want to install in the ext3 partition. Click on Edit partition and then change the mount point to / -- which is of course the root. If you want to create a separate home partition, then you can do that to. Use the following link to get a better understanding of installation. Since you have about 64GB, you can create a 10 GB root, 20 GB home partition and a shared partition (about 34 GB) which you can access from Windows too. Or on the other hand you can simply make a 10 GB root and the rest as home. you can even access home drives from Windows (after installing fs-driver) but I am paranoid about it, since someone can mess up your /home from Windows and render you incapable of logging into Ubuntu.

[www.psychocats.net/ubuntu/installing]("http://www.psychocats.com/ubuntu/installing")

---

### Post by mike555 on 2007-11-14
you can put a check in the format box for the ext3 partition and set it as " / "
 leave the rest alone ..... then install .... that will wipe your older  Linux and install newer version (be sure you have backed up any documents etc first)...... then restart and if you need drivers for your video card install them ..

---

### Post by Inxsible on 2007-11-14
Oh btw, It's always a good idea to have a separate home partition. That way you dont have to keep re-configuring your applications even when you install a newer version of the OS.

---

### Post by Dr Small on 2007-11-14
Ok, I understand about the /home partition and stuff, but we really don't want, nor a shared partition for Windows, as she just rarely uses it.

Sorry for being so paranoid, but I don't want to make a wrong mistake, and want to be exact.
So, lemme get this straight, as from viewing that screenshot; I am supposed to check the "Format" box on /dev/sda2 (ext3) and then on the next screen or so, set it to "/" for root ?
/me now goes and read psychocats :D

---

### Post by Inxsible on 2007-11-14
> **Dr Small said:**
> Ok, I understand about the /home partition and stuff, but we really don't want, nor a shared partition for Windows, as she just rarely uses it.

Sorry for being so paranoid, but I don't want to make a wrong mistake, and want to be exact.
So, lemme get this straight, as from viewing that screenshot; I am supposed to check the "Format" box on /dev/sda2 (ext3) and then on the next screen or so, set it to "/" for root ?
/me now goes and read psychocats :DCORRECT :D. But actually if you click edit partition, it will give you the option of changing the mount point there itself.

---

### Post by Dr Small on 2007-11-14
Ok. The installation went well. Now I have a different problem.
The Nvidia Restricted Driver will not install now.

I go to System > Administration > Restricted Drivers Manager,
click the Checkbox on NVIDIA accelerated graphics driver, it tells me to click "Enable Driver", the box turns grey, then goes back, and never downloads or installs the driver.

How do I get that driver to install ?
Her screen is 800x600 and we really need this!

Thanks,
Dr Small

Edit, I clicked post, tried it again, and it started downloading.... It fears the wrath of the community :p

I'll see what happens :)

---

### Post by Inxsible on 2007-11-14
> **Dr Small said:**
> It fears the wrath of the community :p

LOL ;)

---

### Post by Dr Small on 2007-11-14
Ok. Nvidia drivers working flawlessly ;)
So, now. On the desktop, are SDA1 and SDA3, mounting automatically from fstab.
They are basically just accessing her Windows, but she doesn't want them to auto mount from fstab, so I must do something about it.

Here is my fstab:
```
firefoxwiz@firefoxwiz-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=92efca33-1025-486d-a81d-86f962955709 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=D614286C142851B3 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=4B6E-6BC0  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=a34aa8ea-4cf6-4c43-9752-a3b5f9993ec9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I just need to remove the /dev/sda1 and /dev/sda3 entries ?

---

### Post by Duck2006 on 2007-11-14
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

mite be a bit late but hear it is.

---

### Post by Inxsible on 2007-11-14
Simply comment them out using a # sign in the front of the line. that way, if you do need access to them in the future, you can simply uncomment them and you will be good to go.

---

### Post by Dr Small on 2007-11-14
> **Inxsible said:**
> Simply comment them out using a # sign in the front of the line. that way, if you do need access to them in the future, you can simply uncomment them and you will be good to go.
Done. Works perfect. I thank you, and everyone else who aided in my help to successfully install a newer version of Ubuntu on my sisters system. I could never have done it without the community :)

Now, she has everything the way she likes it, and is now copying her files back to her system, via FTP from my FTP server ;) The real reason she wanted a newer version, was to play PiXfrogger and other games that just wouldn't work on Dapper :p

Thanks again!

Dr Small

---

### Post by Inxsible on 2007-11-14
Sweet !!

Glad to see that its all working out for you and your sis :D

---

