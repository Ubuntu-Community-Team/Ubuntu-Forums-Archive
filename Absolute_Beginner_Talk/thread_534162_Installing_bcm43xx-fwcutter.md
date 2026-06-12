---
title: "Installing bcm43xx-fwcutter"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Diamyst on 2007-08-24
I downloaded bcm43xx-fwcutter.   I have downloaded the appropriate file for my Broadcom wireless card.  I have no idea how or where to install fwcutter so I can install the other file.  I'm lost, lost, lost...     Help please..  simple directions in very plain layman's language would be every so greatly appreciated.  I'm not as young as I used to be and brain fog is sometimes and issue.

Thanks.

---

### Post by SpiritIsReality on 2007-08-24
howdy

I heard it's best to go with ndiswrapper, worked for me
either way, this is where I started

[http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com+wireless+feisty&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com+wireless+feisty&btnG=Search&meta=)

trails

---

### Post by loevans on 2007-08-24
Dia,

First start by downloading the driver.  I had to go to dell and extract the driver from their self-extracting file.  When I extracted it, there is a directory called "DRIVER" that has the .inf and .sys files.  Just copy that whole thing to your home directory...call it 43xxWRLS or something else really neat.  I was _somewhat_ lucky - I have xp installed on the same box, so I could just copy from the ntfs partition to the ext3 partition where my home dir is.  moving on...

I am new to ubuntu (first time on debian variant),  so, don't kill me if there's an easier way.  I found this to be an easy way to do it.  Run apt (i.e. click applications...add/remove).

Search for the package ndiswrapper.  In order to do this you type in wireless in the search box top left of the add/remove applications dialog.  make sure when you do this that the "All" category is selected.  

once you have found ndiswrapper, go ahead and click the check box.  The description will be "Windows Wireless Drivers / Ndiswrapper driver installation tool".  Once you are there, it can't hurt to install the wireless assistant.  Go ahead and check that one as well.  Now click OK (bottom left).

I think it would be best now to restart ubuntu, but I'm sure it's not completely necessary.  Sometimes getting rid of Windows habits are hard.

When this comes back up, drop to a terminal session and cd to your home directory and then cd to the directory where the windows driver files are.  now type in the command "ndiswrapper -i bcmwl5.inf" (at least that's what i typed - i guess it will depend on the windows driver files you download).  

Now I had to go to /etc/modprobe.d and edit the blacklist file.  add the line "blacklist bcm43xx" to the end of the file.  If you have problems with sudo-ing to get the file read/write, then drop to a terminal session, cd to /etc/modprobe.d and type "sudo gedit blacklist".  this will make it a little easier for you if you have any issues with vi.

Now, again, I rebooted just to make sure everything got a fresh start.

Now drop to a terminal and type gksudo -S wlassistant (you may have to provide a path for this, but probably not).  Now you should see some wireless networks if you are broadcasting from your AP.

HTH
le

---

### Post by kevdog on 2007-08-25
If you want to use the bcm43xx-fwcutter method do not install ndiswrapper.  

Here is what I did originally I had a broadcom 4306 rev03 card WPC54g v3 windows driver:

You can do the following to obtain a wirless connection on an unencrypted network (encryption will be dealt with later).

1. On the computer with the internet connection and with USB drive installed
	Download the following 2 files to the USB stick:
	Debian Prepackaged Source for bcm43xx-firmware package:
		[http://packages.debian.org/cgi-bin/search_contents.pl?searchmode=filelist&word=bcm43xx-fwcutter&version=testing&arch=i386](http://packages.debian.org/cgi-bin/search_contents.pl?searchmode=filelist&word=bcm43xx-fwcutter&version=testing&arch=i386)

	WPC54g v3 windows driver:
		[http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)

2. Insert the USB stick into the wireless computer in which you are installing Ubuntu
3. The USB stick should be recognized automatically, and a window should come up asking you what to do.  Select open folder
4. Navigate to where you placed the 2 files above.
5. Right Click on the Debian File and select Install with Debian Package Manager
	During the installation a dialoge box will appear, click on Terminal.  After sometime a Blue screen will appear in the 
	terminal asking whether you want to download updates.  Select NO (since there is no internet connection). And the installation
	will continue and complete
6. Drag the wl_apsta.o to the Desktop
7. Type the following lines within a terminal window:
	sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
	sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o 

Then use network manager to make the physical connection.

---

### Post by mc4man on 2007-08-25
By far the easiest way I've found enable this wireless is to                1. download bcm4318.all.tar.tz  to desktop
then simply run 
```
cd ~/Desktop 
tar -xf bcm4318*.tar.gz
sudo ./ndiswrapper_setup
```

done
dl.location (attachment half way down page)
[http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper]("http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper")

---

