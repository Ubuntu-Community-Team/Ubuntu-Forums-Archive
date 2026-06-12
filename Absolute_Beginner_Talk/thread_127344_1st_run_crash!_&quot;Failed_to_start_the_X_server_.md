---
title: "1st run crash! &quot;Failed to start the X server ...&quot;"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by Jaan1970 on 2006-02-08
Hi everyone ... I am a complete newbie when it comes to Linux.  I've never used it and I don't really know how it's all put together.

I partitioned a virgin hard drive with the specific intention of dual booting Windows and Ubuntu.  I made one partition, installed XP Pro, and made sure I had all the upgrades, patches, and drivers.  I then made another partition with FAT32 (someone told me it's good for sharing files between Windows and Ubuntu), and then I ran the Ubuntu install disk I downloaded this morning.  I made a 512MB swap file partition, and then installed Ubuntu on a 20 gig partition.

Everything seemed to go smoothly until I actually tried to run Ubuntu.  I got a crash and an error message which began with: Failed to start the X server ...".  I get this every time, and then I can at least get to a "command prompt".

I've looked around and viewed some threads that probably hold the answer, but since I don't have a clue where to start it's all Greek to me right now.  What do I do at this point?  What information do I need to tell you guys (and how do I find it)?  

My computer specs are listed on the web page below, except I added 512MB RAM and the hard drive is now a 120 gig Western Digital:

[http://tinyurl.com/bouoe](http://tinyurl.com/bouoe)

Any help is greatly appreciated!

---

### Post by AndyCooll on 2006-02-08
Sounds like your x-server settings haven't installed properly. Try reconfiguring them again.
First backup your settings, so that you can return to them again if necessary:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then reconfigure:

```
sudo dpkg-reconfigure xserver-xorg
```

This will start a wizard. You can accept most of the defaults. For the graphics card it might be worth trying "vesa". Also I got errors when selecting the wrong mouse type. When its finished type:

```
startx
```

If it doesn't work you can always run through the wizard again.

:cool:

---

### Post by Nrvnqsr on 2006-02-08
EDIT: =o lol AndyCool beat me to it so anyway here's how I did it

the reason you have a X server crash is because you got ATI video card which the build-in Ubuntu drivers doesn't recognize so what you need to do is when you get on command line after X server crash type in 

> 
sudo nano /etc/X11/xorg.conf


find this area of the file
> 
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		**"ati"**
	BusID		"PCI:1:5:0"
EndSection


and change from *ati* to *vesa*

> 
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		**"vesa"**
	BusID		"PCI:1:5:0"
EndSection


save and reboot and it will be able to run on basic video

then follow the direction in this thread to install the video drivers for ATI X200M
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

second EDIT: checking on your specs, I would say that the multi-card reader may or may not work on Ubuntu so just a lil caution

---

### Post by Jaan1970 on 2006-02-09
Thanks a lot guys ... changing my graphics card from ATI to Vesa did the trick!

I haven't installed the new drivers yet but at least I got on ... the point of setting this up as dual boot is so I can slowly migrate over and learn while I'm doing it ... it sure helps having two computers hooked up to the internet right next to each other too (c:

EDIT: Ubuntu is reading my multi memory card reader no problem.  I just looked at some photos.  Ironically, the fresh install of Windows XP Pro gave me some problems in that area.

---

### Post by hotpurple on 2006-02-09
An even easier method is to type

```

sudo fglrxconfig

```

and fill in all the questions it asks you. This worked a treat on my PC. I had the same issue by the way.

Chris

---

