---
title: "Questions."
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by Rojay on 2006-05-16
okay most of these questions were probably answered before but ....

iv been usuing windows since 1993
and i thought id give linux a try and after taking a quiz [http://www.zegeniestudios.net/ldc/index.php?firsttime=true](http://www.zegeniestudios.net/ldc/index.php?firsttime=true) i decided to go with ubuntu
so i downloaded the live cd (havent tried it yet)

my questions are:

1-if i installed the full version of ubuntu will i be able to access my other NTFS partitions ?? because all of my files are on it
2-can i download software of the internet and install it ?? like [http://mercury.to](http://mercury.to) ??
3-can i run exe's on ubuntu?? because i read somewhere that xandros does

thanks :)

---

### Post by Rinzwind on 2006-05-16
1. yes, but only READ them. It's better to have a FAT32 partition for sharing between Ubuntu and Windows. 

2. yes, [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)
Automatix installs Mercury Messenger (Java based MSN client with webcam support)

3. NO. Not in Ubuntu. You can install windows inside Ubuntu (Ubuntu->VMWare->Windows->Exe's).

---

### Post by aysiu on 2006-05-16
[QUOTE=Rojay]so i downloaded the live cd (havent tried it yet)[/quote] Can I just say that I'm glad you start asking questions *before* you install Ubuntu? I think that's a very good idea.

> 
1-if i installed the full version of ubuntu will i be able to access my other NTFS partitions ?? because all of my files are on it No, you will be able to access NTFS read-only. On the other hand, from Windows, you will be able to access Ubuntu's Ext3 partition with this driver: [http://www.fs-driver.org](http://www.fs-driver.org)
> 
2-can i download software of the internet and install it ?? like [http://mercury.to](http://mercury.to) ?? Yes, but it's much easier to use a package manager for your software needs.
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

For Mercury, you'd download [this file](http://umn.dl.sourceforge.net/sourceforge/projeto-messias/mercury-messenger_1710_S7_i386.deb) to your desktop and paste these two commands into the terminal: ```
cd ~/Desktop
sudo dpkg -i mercury-messenger_1710_S7_i386.deb
```
> 
3-can i run exe's on ubuntu?? because i read somewhere that xandros does It depends on the .exe.

In general, it's always best to try to find a native Linux application.

Then, if you have a program that works in Windows '98, it'll probably work in *wine*.

If it needs Windows 2000 or XP, it'll probably need Crossover Office to work.

If it's a game, it'll probably need Cedega to play.

And some... just won't work at all.

---

### Post by Sef on 2006-05-16
> 1-if i installed the full version of ubuntu will i be able to access my other NTFS partitions ?? because all of my files are on it

GNU/Linux can read, but not write to NTFS.  If you make a FAT32 partition, GNU/Linux and Windows can both read and write to it.

> 2-can i download software of the internet and install it ?? like [http://mercury.to](http://mercury.to) ??

Read these two web pages to learn how to install.

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

[http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal]("http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal")

> 3-can i run exe's on ubuntu?? because i read somewhere that xandros does

I just read a post the other day that talked how to do it.  I am not sure off-hand how to do it.

---

### Post by nalmeth on 2006-05-16
.exe's is tricky business.

You can easily acquire the freely available wine (Windows Compatibility Layer), which has limited success running certain windows applications

If you want MS Office, Photoshop, apps like that, you'll have to *pay* for Crossover Office. It's kinda pricy, and you should instead use the linux native equivalent applications: OpenOffice GIMP

If you want to play games, you need Cedega, which cost's minimum $15.00 (3 month subscription).

---

### Post by Rojay on 2006-05-16
thanks alot you guys :)
but

if i can read files from NTFS partition, can i copy the files to linux and then edit them or whatever i want to do with these files ?(i guess i can, but i want to makes sure)

how big is the ubuntu full package ? is it a DVD and is there CDs for it ? because i dont have a DVD burner 

and can i free some space from my D: partition -NTFS- and use partition magic to convert this empty space to EXT3 ?? or it must be on the C: ?

ill guess ill look around for the installation guide, but i dont think they answer these question there :)

---

### Post by nalmeth on 2006-05-16
[quote=Rojay]thanks alot you guys :)
but

if i can read files from NTFS partition, can i copy the files to linux and then edit them or whatever i want to do with these files ?(i guess i can, but i want to makes sure)

how big is the ubuntu full package ? is it a DVD and is there CDs for it ? because i dont have a DVD burner 

and can i free some space from my D: partition -NTFS- and use partition magic to convert this empty space to EXT3 ?? or it must be on the C: ?

ill guess ill look around for the installation guide, but i dont think they answer these question there :)[/quote] 
1. hmm, I believe you can do this, but I don't have NTFS to check and make sure.

2. You can install ubuntu with one [install CD]("http://www.ubuntu.com/download"). Then the installer uses the internet to install a lot of the packages.

3. You *can* free space from your NTFS, but before you shrink it, DEFRAG the heck out of it. Windows can become damaged if you shrink it when it's fragmented :rolleyes:

4. If you have the space, you may prefer creating an EXT 3 partition after your NTFS, and creating a FAT32 partition for shared data.

This is a good setup for dual boot. Unless of course you can reinstall windows with fat32, but this usually isn't practical for most

---

### Post by mostwanted on 2006-05-16
[QUOTE=Sef]GNU/Linux can read, but not write to NTFS.  If you make a FAT32 partition, GNU/Linux and Windows can both read and write to it.



Read these two web pages to learn how to install.

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

[http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal]("http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal")



I just read a post the other day that talked how to do it.  I am not sure off-hand how to do it.[/QUOTE]


Sef, the correct link is [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html) ; currently you're linking to a sub section in the appendix about navigating inside a terminal. It's a little confusing ;)

---

### Post by aysiu on 2006-05-16
[QUOTE=Rojay]
if i can read files from NTFS partition, can i copy the files to linux and then edit them or whatever i want to do with these files ?(i guess i can, but i want to makes sure)[/quote] Yes, you can, but you may have to change ownership of those files first. It's a long story, but basically the way NTFS gets mounted read-only, it's owned by *root* but readable by anyone (including rojay). When you copy it over to Ubuntu, it'll still be owned by root, but I'm not sure it'll be readable by user any more.

> 
how big is the ubuntu full package ? is it a DVD and is there CDs for it ? because i dont have a DVD burner  It's a CD. There are DVD versions available as well. I don't have a DVD burner either. I always get the CD image.

> 
and can i free some space from my D: partition -NTFS- and use partition magic to convert this empty space to EXT3 ?? or it must be on the C: ? Don't use Partition Magic. I've read it does weird things with Ext3. Use this dual-boot guide: [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

> ill guess ill look around for the installation guide, but i dont think they answer these question there :) Read this: [http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf)

---

### Post by Rojay on 2006-05-17
well is there a multiple CDs package instead of the DVD ?? because i tried downloading fromt he installers but it was soo slow
plus i wouldnt want to go thru the downloading everytime i install it
i would like to have it on CDs -like 5~6 CDs-

---

### Post by aysiu on 2006-05-17
Ubuntu doesn't do multiple CDs.
Mandriva, Debian, and Fedora, however, do.

---

