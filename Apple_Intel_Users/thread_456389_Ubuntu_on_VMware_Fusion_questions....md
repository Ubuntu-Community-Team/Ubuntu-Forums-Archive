---
title: "Ubuntu on VMware Fusion questions..."
date: 2007-05-27
forum: Apple Intel Users
---

### Post by thully on 2007-05-27
Hi,

I've been playing with Ubuntu on my MacBook both in a dual-boot and in VMware and Parallels on OS X.
Anyway, I figure that I'm either going to install Ubuntu in VMware Fusion or do a full install and use it in place of OS X - I don't see myself dual-booting long-term (if I want OS X enough to keep it as a partition, I figure that the annoyance of dual-booting and sharing data between two OSes is probably too much...).  

However, I do have some questions regarding installing Ubuntu in VMware Fusion - while I have done it, I haven't used it heavily there...

First of all, can you disable the annoying VMware menu bar that pops up when your mouse cursor is at the top of the screen in fullscreen mode?  Also, can you get VMware Fusion to run fullscreen all the time?  I don't want to run in a window on my 13-inch MacBook...

Secondly, how do you get file/folder sharing to work properly between Ubuntu/OS X?  I tried this, and while you can share folders, many of the files/folders contained within give permission errors when accessed within Ubuntu.  Ideally I'd like to share my whole home directory between both OSes - including music, documents, and so on...

---

### Post by ronocdh on 2007-05-28
> **thully said:**
> I don't see myself dual-booting long-term (if I want OS X enough to keep it as a partition, I figure that the annoyance of dual-booting and sharing data between two OSes is probably too much...).Dude, it's no hassle at all! And you must understand that your boot times, even into Ubuntu, will be much faster *if OS X is installed on a separate partition*. This is because with OS X installed, you can use rEFIt as an EFI bootloader; without that, your Mac will be scanning the hardware looking for the GPT makeup when really Ubuntu's handled the drive with an MBR. It'll work, sure, but it adds tons of time (like 15 seconds after power on until it can boot from the drive). Benanzo has posted fairly extensively on this topic here.

> First of all, can you disable the annoying VMware menu bar that pops up when your mouse cursor is at the top of the screen in fullscreen mode?Not sure... and wait, VMWare Fusion has fullscreen? I thought the common complaint was that it didn't:>  Also, can you get VMware Fusion to run fullscreen all the time?  I don't want to run in a window on my 13-inch MacBook...I honestly haven't used it enough to know whether there's a "run in fullscreen only" option, but i did find it remarkable that it ran in a window by default, rather than maximized as another "place" as Parallels seems to do. Someone please post if they can add to this.

> Secondly, how do you get file/folder sharing to work properly between Ubuntu/OS X?  I tried this, and while you can share folders, many of the files/folders contained within give permission errors when accessed within Ubuntu.  Ideally I'd like to share my whole home directory between both OSes - including music, documents, and so on...No problem! First step is to disable journaling on your OS X party. Do this via Disk Utility or the terminal. Then in Ubuntu I did **sudo nautilus** (be very careful with this!) then navigated to the folders I wanted to have access to, e.g. /dev/sda2/Users/ronocdh/Documents or something and change the folder permissions. Make sure to have the permissions carry over to all folders and files contained therein recursively.

Last you'll want to add the OS X party to your fstab so it's always there when you start Ubuntu and you don't have to manually mount it via the terminal or something. Good luck!

---

### Post by thully on 2007-05-28
Thanks - I may try that out for sharing data.  Then again, I'm leaning towards only one primary OS as I only have a 60GB drive and having two sets of bookmarks/settings/etc is kind of annoying.  I'm thinking of maybe trying Ubuntu alone  (or with a very small OS X partition) for now and then going back to OS X if I decide I want to - I'm probably due a reinstall by now.

---

### Post by arijarot on 2007-05-29
I'm not sure what it is in mac or if it exists, but in windows, the vmware server's option to get into the full screen is ctl+alt+enter. maybe on mac it's something similar like, command.... just a thought.

---

### Post by arijarot on 2007-06-01
> **thully said:**
> 

First of all, can you disable the annoying VMware menu bar that pops up when your mouse cursor is at the top of the screen in fullscreen mode?  Also, can you get VMware Fusion to run fullscreen all the time?  I don't want to run in a window on my 13-inch MacBook...


to get rid of the menu bar that pops up at the top of the screen while in fullscreen mode (ctl+command+enter), you have to uninstall the vmware tools.

---

### Post by galvatron1983 on 2007-06-02
Fullscreen is Option+Enter. If you install the VMWare tools for Ubuntu, it will dynamically resize the Ubuntu resolution to match the MacBooks screen rez. 
 
To access your OS X files in Ubuntu just read my thread....

[http://ubuntuforums.org/showthread.php?t=443204]("http://ubuntuforums.org/showthread.php?t=443204")

---

### Post by davidj411 on 2008-05-19
when i run ubuntu in full screen mode on Fusion on my mac OS X 10.5 leopard, it does not show up in full screen. FULL SCREEN is supposedly open, but the size of the ubuntu screen is as if it were inside a small window. this results in my being unable to view applications in ubuntu, making it a rather un-usable operating system for this reason. i am not sure why it looks this way. i am attaching what the screen looks like. please advise me!! Thanks!

---

### Post by arijarot on 2008-05-19
Change the resolution in ubuntu.

---

### Post by cyberdork33 on 2008-05-19
This forum is just an archive. New posts should be made here:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

