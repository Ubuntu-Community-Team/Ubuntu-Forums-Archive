---
title: "Switching to Ubuntu to Kubuntu"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by zanomix on 2007-02-05
Hello,

I would like to switch from Windows XP to Linux. I've obtained an ubuntu 6.06 cd by a friend and now I would like to set up a Dual Boot system.

Last time I tried to set one up I messed up and I had to format my harddisk without backing up. But I won't give up that easely :lolflag: 

But this time I would like to have a proper preparation.

What do I have to do to instal ubuntu with a dual boot windows, how can I turn my ubuntu into kubuntu and wich programs can I use as an alternative for:

iTunes (with mp3's and stuff), Dreamweaver, BSPlayer and MSN. I didn't liked gaim becuase they don't have those messages msn has like 'Bart has signed in'. It could also be that i didn't had the right thing turned on :P

I'm sure I'm not the first one asking these things but its really complicated if I have to search al those things.

---

### Post by aktiwers on 2007-02-05
Yeah Gaim can do that too.

Instead of Itunes... There are lots of Music players, I use Rhythumbox, songbird and Xmms.

Instead of Bsplayer, I use VLC, Mplayer and Totem

Instead of Gaim I sometimes use aMSN, which is more like MSN than gaim.

Instead of Dreamweaver..  I think you have a problem there..

To install Kubuntu Look here:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by galvatron1983 on 2007-02-05
I prefer Kubuntu to Ubuntu because of the KDE desktop environment gives me a little more control over my interface and allows me access to more settings and features by default. I also prefer the layout of Konquerer to Nautilus and the overall set up of the desktop in general. 

For iTunes you have Rhythmbox
For Dreamweaver you have Nvu
MSN is covered with aMSN and Kopete

---

### Post by zanomix on 2007-02-05
Thanks for the help! Any idea how it went wrong at my previeus installation? When I chose Windows in my dual boot screen I went to HP System Backup. I was forced to reformat. I partitioned my disk with the normal ubuntu partitioning tool.

---

### Post by livingtarget on 2007-02-05
With Gaim you can indeed get msn-style popups with the libNotify plugin.

I think it comes with gaim by default, here's how to enable it:
Tools -> Plug-ins

There should be a list of plugins, enable "LibNotify popups" and you should receive popups when people sign in etc. You can also configure the plugin. See the attached screenshot for the plug-ins window in Gaim

About dual booting; does windows launch at all? I assume when you boot you see the (linux) grub boot loader and then you select to boot Windows. There can be problems if Grub resides in the MBR (Master Boot Record) and windows sometimes does not like that. There's a few ways around it, but I can't give you any real pointers atm.

Maybe also tell us what your hard disk(s) setup is like. That would help us understand. Are you installing linux on a seperate physical hard drive or on the same hard drive?

---

### Post by true_friend on 2007-02-05
I love KDE.
Suggest u to use KDE also. ;)

---

### Post by zanomix on 2007-02-05
Again thanks.

Its to late to safe anything but then I know what I did wrong the previeous time. I used NTFS as filesystem. I think that was my problem.

---

### Post by TAfricanski on 2007-02-05
That can't have been your problem because Ubuntu does not install on NTFS and it resides peacefully with two NTFS partitions on my harddrive. These can be mounted and read by Linux, I've heard they could be even written on, but the function is still in BETA and disabled by default...
I had a similar problem last time I tried to install Mandrake. I think just GRUB did not have the right settings and if I knew how to configure it I could have saved my data... That's why my GRUB is now on a diskette. I think this is the best solution for a dual boot system provided that you have a floppy drive, though. ;)

---

### Post by zanomix on 2007-02-08
Thanks for the advice :)

---

### Post by mikemn84 on 2007-02-08
I'd suggest Quanta Plus as another option to replace Dreamweaver.  It handles CSS better than Nvu among other things, and suited my needs better than Nvu did.

---

