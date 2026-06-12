---
title: "G75VW: Compiz/unity crashes, small resolution"
date: 2013-02-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Jonathan Rung on 2013-02-18
Hello everyone,

I'm going crazy trying to get ubuntu working on my windows 7 laptop, which I freshly installed about five times.  My computer is a G75VW with nVidia 660m.  It came with Windows 7 and a 1GB HDD.  I added a solid state drive, installed windows onto the SSD, and I'm using the HDD for data (the HDD still has some of the old windows recovery/boot partitions, which take up comparatively little space, and I figure could be useful if I ever botch the boot programs).  

I then began installing ubuntu onto the SSD, which I knew would be a little trickier than usual because wubi and live ubuntu pendrives didn't work (I think because my windows setup is using UEFI) and because I read on these forums about some problems people experienced with nVidia drivers.  Anyway, eventually I stumbled across [this]("http://www.rodsbooks.com/refind/installing.html#windows"), installed it, and I was able to select the pen drive from the boot menu and it started up without a hitch.  Everything looked great in ubuntu (I never saw ubuntu running on a 1080 screen before!), so I made a new 40gb partition for ubuntu, an 8gb partition for swap, and I think I installed the boot to the first partition of the SSD, the 200 mb partition.  Here's a picture:

[http://i.imgur.com/W6aUhQg.jpg]("http://i.imgur.com/W6aUhQg.jpg")

The installation runs smoothly (either from "try ubuntu without installing, and then installing from within ubuntu, or going straight to the installation from the pendrive), and then it asks me to reboot.  When I reboot, I'm greeted with the GRUB 2 menu, and Ubuntu booted up without any problems...  However, about 5-10 minutes after ubuntu boots, I get a warning that compiz crashed, I hit relaunch, but it doesn't relaunch.  Around this time, most of the desktop environment crashes and disappears (window borders, sidebar, topbar, etc).

If I log out and log back in, the desktop is still bare.  If I make a new admin user and log into that, same issue.  If I rebooted, the GRUB2 menu would appear, but ubuntu would either a) boot with a really low resolution and still no unity desktop, or b) not boot at all, just boot a black screen.  Side note: from GRUB 2, if I choose Win7, it will not boot, so I need to hit escape on boot and get into the boot menu to boot windows 7.  This doesn't bother me; I'm mentioning it in case it's indicative of the larger problem.

I booted using the pen drive again, re-installed ubuntu, and changed the graphics driver from software sources to something proprietary from nvidia (I read on here that some people's resolution dropped to like 600x800, and that nvidia drivers fixed the problem).  However, the same exact thing happens: compiz crashes, I hit relaunch, it actually does relaunch once or twice, but it never stayed open for more than a minute and then it was gone forever.

I read [this]("http://ubuntuforums.org/showthread.php?t=2058444") guide, which I tried to follow step-by step, but many steps didn't work - perhaps most notably the Ubuntu recovery area, which seems to simply crash my PC after making a selection.  However, I can use a terminal from within Ubuntu (on two occassions, I did these commands immediately after the fresh install, when the desktop was still running and I had native resolution, but after I restarted the computer the desktop was broken again), so I typed *sudo apt-get install nvidia-current*, and it installed the driver, and nvidia-xconfig also seemed to work (it needed root access, and I don't know what was supposed to happen, but it saved something to a file), but the inevitable compiz crash/desktop crash/screen resolution shrink still came around.  One last note, it seems like with every boot after an install, ubuntu becomes less and less stable, doing things like booting (I hear the ubuntu startup sound) but the screen is black, or the screen just freezes on the ubuntu logo and then glitches out with random pixels if I press enter).

I know that's a lot of information, but I'd appreciate any suggestions.

---

### Post by binary00mind on 2013-02-27
You gave us a lot of info....
So I gather that you have Win 7 and Win 8 plus Linux.
Pressing escape is not needed. just make Win 7 partition active instead of Win 8..edit the boot menu (under 7) and the problem will go away...but then again where is your grub installed?.
I use escape sometimes as well but only to choose other Hard Disk (portable or stick) that wasn't configured

I can boot into any OS from any Hard Drive, (including portables) so no escape is needed for me. And I have in totall 4 OS's installed on my 2 internal HD's alone.

Anyhow my Notebook is 3 years older and my compiz-config crashes as well. As a matter of fact i just submitted as a bug.

Ubuntu cannot find the right nvidia driver for you. and your Asus is newer than mine.
So just forget all about it and wait until the Ubuntu Developer team will catch up and/or Nvidia will by itself provide a driver for Linux.  Meantime no "Special Effects" for you..
 
Asus is tricky, :popcorn:

---

### Post by Jonathan Rung on 2013-03-02
> **binary00mind said:**
> You gave us a lot of info....
So I gather that you have Win 7 and Win 8 plus Linux.
Pressing escape is not needed. just make Win 7 partition active instead of Win 8..edit the boot menu (under 7) and the problem will go away...but then again where is your grub installed?.
I use escape sometimes as well but only to choose other Hard Disk (portable or stick) that wasn't configured

I can boot into any OS from any Hard Drive, (including portables) so no escape is needed for me. And I have in totall 4 OS's installed on my 2 internal HD's alone.

Anyhow my Notebook is 3 years older and my compiz-config crashes as well. As a matter of fact i just submitted as a bug.

Ubuntu cannot find the right nvidia driver for you. and your Asus is newer than mine.
So just forget all about it and wait until the Ubuntu Developer team will catch up and/or Nvidia will by itself provide a driver for Linux.  Meantime no "Special Effects" for you..
 
Asus is tricky, :popcorn:

Thanks for the response.  I only have Win7 and Ubuntu (well, an ubuntu partition anyway!).  I *do* need to hit escape if I want to boot to windows - it will not boot from the GRUB 2 menu, but like I said, that's not really a problem/hassle, just wanted to mention in case it was helpful for diagnosis :)  My windows 7 copy shipped with a UEFI bootloader, which I think is in the first 200 mb partition of the SSD, and that is where I (think) I installed GRUB 2.  I followed the directions for a dual boot installation for UEFI systems from the ubuntu website, and troubleshooted through these forums and elsewhere.  I may be using some of these technical terms incorrectly - these are things I read from various guides, I don't quite understand a lot of this.

My issue isn't that I don't have special effects - ubuntu doesn't really work at all.  I'm pretty sure the kernel boots, but the diagnostic menu crashes, the screen is like 800x600 (if I'm lucky) and has no GUI except for the wallpaper and I can launch a GUI terminal that crashes if I try to move it.  If I'm not lucky, the system crashes immediately after booting.

I found the following suggestion (I tried the nvidia-current command before but I didn't uninstall it first - I don't know if the nvida drivers are to blame for the drivers, but if they are, then perhaps it will help) on these forums, and I'm going to give it yet another go this weekend, but I've tried so many fixes/workarounds, and wasted so much time, that I'm running out of patience :( The frustrating thing is that I know my exact system model runs ubuntu for other people, but I can't figure out what I'm doing differently.

[B]Notes about nvidia cards and SLI 
The "nomodeset" kernel bootline switch usually works for most nVidia cards, but now all.

Especially for nvidia cards, I usually just into a text mode by going to a text console via grub edit ('e") append " text " to the end of the kernel boot line and boot{"ctrl-x') and after a login type 
Code:

sudo apt-get updatesudo nvidia-installer --uninstallsudo apt-get remove nvidia-*sudo apt-get install linux-headers-'uname -r'sudo apt-get install nvidia-current  sudo nvidia-xconfigsudo apt-get update
(Note- This example assumes that you have a GeoForce 6xxx or better card) then try to start the GUI viaCode:

sudo service gdm  start
[/B]

---

