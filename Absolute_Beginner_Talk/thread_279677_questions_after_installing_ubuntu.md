---
title: "questions after installing ubuntu"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by ExtraEye on 2006-10-18
i moved two days ago to working with linux software for the first time. i use ubuntu.
i have an amd athlon 64 processor with 1024 DDRam and Geforce 6600GT and 
two hard drives:

Drive1: 147 giga
windows is installed
uses NTFS

Drive2: 74 giga
contains the linux installation
apparantly uses ext3

i need some help with the following questions:

1)how can i split my linux drive two drives that one of the will contain the linux installation and the other will have the rest of the space and work for both windows and linux.

2)I have a HD TV that is connected through DVI type connection. How can I reach something similiar to windows' dual screen mode so i can watch movies through the TV while I'm working on the computer?

3)I tried to install wine in many different ways but nothing worked (installation itself fails). Even used Automatrix2 and didn't have the option to install it :(

plz help me smile.gif

---

### Post by PriceChild on 2006-10-18
For the linux drive.

You'll want to use gparted or something similar to create a fat32 partition which you can mount using: [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

Or you could install an ext3 driver onto windows to read/write the linux partition, linux being able to read ntfs, and ([http://fs-driver.org/](http://fs-driver.org/)) read/write fat32 using [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by ReaderRat on 2006-10-18
1) You could resize and add a partition - formatted as fat32 - which both Linux and Windoze can read/write.

---

### Post by ExtraEye on 2006-10-18
thank for the replies.
ReaderRat - that's what I plan to do.
synaptic package shows gparted is installed but it doesn't show up in any of the menus.
also installed QTparted but when i start it, it says it can't find devices and it suggestes that maybe im not a root user (although i tried logging as one and it still said that...)

---

### Post by localuser on 2006-10-18
gparted doesn't automatically get entered into the menu system.  If its installed properly you will need to open a terminal session (Applications | Accessories | Terminal) and enter the following:

~$ sudo /usr/bin/gparted

You will then have to enter your login password.  "sudo" means that you want to run the command with root privileges.  Since the root account is disabled by default in Ubuntu, you will need to do this when you get a privilege error.

Here's a link to the gparted doc pages...
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)


~lu

---

### Post by ExtraEye on 2006-10-19
o.k i did reach gparted but for the drive i want to work on all options are grayed out. so it doesn't really let me do anything except "unmount" which obviously doesnn't work either since "drive is in use".
o.k according to the guide i understand it probably isn't possible to do this through linux since it says i have to unmount a partition in order to resize it but when i try to unmount it says this partition is busy. obviously i can't do this while linux is runing (although scechualing should be made possible :/).
so does anybody know of a partition software on windows that can work on ext3 or maybe a partitioner that can scechual(can't remember how to spell that :P).

*sigh* I hate it when the smallest things comlicate...

---

### Post by localuser on 2006-10-19
No worries, there are always options.

Here's a link to a GParted LiveCD.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

~lu

---

### Post by CatKiller on 2006-10-19
> **ExtraEye said:**
> i need some help with the following questions:

1)how can i split my linux drive two drives that one of the will contain the linux installation and the other will have the rest of the space and work for both windows and linux.

Either use the live cd that you installed from, or download the [GParted live cd]("http://gparted.sourceforge.net/livecd.php") if you want to use the latest version, which has support for more operations. As you've found, you can't change the partition that you're using to change the partition :) Using a live environment, the drives aren't mounted, so you avoid that problem. If you use the Ubuntu live cd, you might get some complaints unless you use the command ```
sudo swapoff -a
``` The swap partition that you made during the install gets used by the live cd to improve performance, but you might want to not use it for the reasons above.

> 2)I have a HD TV that is connected through DVI type connection. How can I reach something similiar to windows' dual screen mode so i can watch movies through the TV while I'm working on the computer?

There are lots of posts about dual screen and dual head setups. Some of the solutions are more fiddly than others, depending on how it's all connected to which devices. The file /etc/X11/xorg.conf is the key.

> 3)I tried to install wine in many different ways but nothing worked (installation itself fails). Even used Automatrix2 and didn't have the option to install it :(

The way that I found easiest, and this gets you the latest version, is to run Synaptic, click on Settings -> Repositories -> Add -> Custom and type > deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main Hit the Reload button, find wine in the list and select "Mark for Installation".

---

### Post by ExtraEye on 2006-10-20
> The way that I found easiest, and this gets you the latest version, is to run Synaptic, click on Settings -> Repositories -> Add -> Custom and type  Hit the Reload button, find wine in the list and select "Mark for Installation".
Actually that's the first way i tried installing it and it didn't work. but i redid it now just to see if I'm wrong and this is what I got when i hit reload:
```
[http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:) 404 Not Found
```

Edit: I also went through this guide:[http://www.ricetek.net/howtos/nvidia-dual-monitors-on-ubuntu-dapper/](http://www.ricetek.net/howtos/nvidia-dual-monitors-on-ubuntu-dapper/) 
and now i have the dual screen feature working but windows x woun't load... so no interface :( How do I fix this?

---

### Post by CatKiller on 2006-10-20
I hadn't realised you were using the 64-bit version. That makes things more complicated, since apparently it's less user-friendly, and there's less software that works - including drivers.

That howto is right - nVidia's config tool is absolute crap. I'd edit my xorg.conf by hand if I were you. There's a TwinView howto in the Multimedia & Video forum that might get you started. For now you can restore your backup to get X going again - possibly you already have. You'll probably also want to check if there are 64-bit drivers and a 64-bit version of Wine in existence.

---

### Post by Old Pink on 2006-10-20
> **ExtraEye said:**
> 3)I tried to install wine in many different ways but nothing worked (installation itself fails). Even used Automatrix2 and didn't have the option to install it :(

Do you have an internet connection? Have you tried typing the following in terminal?```
sudo aptitude install wine
```or```
sudo apt-get install wine
```

---

### Post by ExtraEye on 2006-10-21
> **CatKiller said:**
> There'sFor now you can restore your backup to get X going again

No I just went back to my windows installation for now. Finally successfully added a big fat32 partition so now i have breathing space in win.
I was waiting for an explanation on how to restore the backup. When I load linux it woun't take me to the desktop and leave me in some black screen which I can type into and I don't really know how to work with this...

old pink - yes i tried that

---

### Post by CatKiller on 2006-10-21
> **ExtraEye said:**
> I was waiting for an explanation on how to restore the backup.

Sorry. Ctrl-Alt-F2 will get you to a virtual terminal where you can log in. Then ```
sudo cp /etc/X11/xorg.conf.whatever-you-called-your-backup /etc/X11/xorg.conf
``` Then Ctrl-Alt-F7 to go back to the graphical screen and Ctrl-Alt-Backspace to restart your X server.

---

### Post by ExtraEye on 2006-10-21
wierd stuff... i restored my backup and now instead of loading the usuall way the TV is the display and the pc monitor shows a wierd screen (something with many lines and color) - in short it's trying to dual display but can't. I'm typing from linux now but my display is only the TV (not to comfortable btw).
how do i fix this now? :(

thanks for all the help till now

---

### Post by CatKiller on 2006-10-21
You could either post the contents of your xorg.conf here and hope that someone here can spot what's wrong with the configuration, or browse around for more guides on a TV-out setup (although that bit seems to be the bit you've got working), or both. Post as much detail as you can about your setup - graphics card, monitor and the like. Or you could save a copy of your xorg.conf somewhere, run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` to get your monitor working again, and use your saved xorg.conf to then add in the TV bits.

---

### Post by ExtraEye on 2006-10-23
when i login to ubuntu without my tv on the monitor display work so thatll do.
so i guess all that's keft is to get wine working. do i need a 64 bit specific version?

---

