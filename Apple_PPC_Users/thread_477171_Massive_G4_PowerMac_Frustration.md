---
title: "Massive G4 PowerMac Frustration"
date: 2007-06-18
forum: Apple PPC Users
---

### Post by Slushdoot on 2007-06-18
Hello, gents.  I work in a small tech support department where we deal with a few hundred machines.  My workstation is currently like so:
P4 Wilamette, 1.7 Ghz
512 MiB Rambus memory (maxed out)
20 GiB PATA hard disk
nVidia TNT2 Riva GPU
Running Ubuntu 7.04

I have to assemble our own machines by piecing them together from surplus recieved back from end users who have upgraded as there is little money in the budget for our own purposes.  This machine was a massive improvement from my previous rig, a 700 MHz P3 with 256 MiB Rambus memory.

We've recently retired our Mac image server formerly used for net booting and installations.  It's a:
G4 Server DP (Quicksilver)
dual 1.0 Ghz G4s
1.5 GiB PC133 memory (maxed out)
73 GiB SCSI hard disk
40 GiB PATA hard disk
ATi 7300 GPU

It was my goal to ditch the Mac OS on it so that I could use Ubuntu so I could continue to use the Linux programs and related files to which I am accustomed.  I like not having to worry about licensing or similar concerns and Ubuntu has done a yeoman's job over the last year or so.  I wanted to put / on the SCSI disk and /home on the PATA disk.   However, installing a working system has been a source of much frustration.

I initially decided to match the 7.04 installation on the IBM-compatible machine by using the unofficial powerpc version of 7.04.  This did not work very well.  I was getting X server errors when using the live CD that were not fixed by reconfiguring the xserver.  Running with video=ofonly let Gnome begin to load without error but it always hung before loading anything other than the beige background and the cursor.  I downloaded and installed the alternate version.  This seemed to work fine until it came time to boot the new system.  It was always unable to find a bootable partition, even though the automatic installer had obviously installed one.  I goofed around with this for quite some timje, trying 6.10 and 6.06 as well.  All efforts to use the SCSI disk resulted in failure.  More than that it took ages to even meet with boot failure which was mysterious.  I'd start the machine and 20 minutes later the yaboot screen would appear.

I decided to try installing on the PATA disk with /home on the SCSI disk, in case the proper SCSI module had not loaded into the system at the proper time.  This too met with failure.  I was able to boot occasionally but it would hang before bringing up the GDM login screen.  I decided that the SCSI device must be the problem.  I unplugged it from the system and tried again with 7.04.

This time it would successfully load into the desktop after I'd used vim to change the video driver from "ati" to "radeon" which gave me a glimmer of hope.  glxgears worked just fine with that driver so it makes me think that it was working all right.  Now that the SCSI drive was gone it no longer took 30+ minutes to boot.  I installed the empty-package SMP kernel so that I was guaranteed to have the latest version.  I rebooted and found that it was still booting off of the old uniprocessor kernel.  I futzed around with this for a while before reinstalling.  When I did that I repeated the exact same procedure and lo and behold it worked perfectly.  Mysterious.

I then tried creating the necessary users which went just fine until I tried to log in as one of the new users.  Gnome would hang before bringing up the desktop, stranding me at the beige screen again.  I restarted X and tried logging back in as myself to discover that mine was broken as well.  I reinstalled and did the same except this time I did not create the new users.  I discovered that after a few logins Gnome would start freezing for me.  I have no idea what's wrong.  It does the same with 6.10 and 6.06.

I'm at my wit's end with this machine.  It would be a nice boon to my productivity but the system needs to be stable.  If I can't get this to work I'm going to have to install Leopard Server, the OS that the machine left the factory with, which is something I don't want to do.  Every time I try to boot a live CD it gives me a Buffer I/O error on device hdc.  I have no idea which disk this is as the only drives in the system are hda, the optical drive, and hdb, the PATA hard disk.  Sometimes the live CD will work just fine and I have installed from it a few times.  Some times it hangs when loading.  Sometimes it hangs when I'm using it.  Sometimes it hangs when loading Gnome.  

Can you please provide some insight on this problem.  I'm more than willing to answer any whention about the rig you might ask.  I'm, perhaps, an intermediate Linux user.  I know my way around pretty well but could stand to have more knowledge.  I've installed no fewer than 30 times in the past week and nothing seems to be working.  Sorry for rewriting War and Peace here but I don't know what else to do.  Help! :)

---

### Post by ssam on 2007-06-18
Some times resetting the PRAM can cure mac problems.

see [http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

also check that the system date is correct, and being retained between boots. see [https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

there are some sound related problems in 7.04 (at least on G4 powerbooks, maybe on G4 desktops). this can cause gnome not to log in. see [http://ubuntuforums.org/showthread.php?t=475675](http://ubuntuforums.org/showthread.php?t=475675)

---

### Post by Slushdoot on 2007-06-18
Nah, I've zapped the PRAM too many times to count.  The system time is fine and is retained when I switch the machine off.  Sound works just fine as well, if that can be taken as evidence.  Thanks for the reply though. :)

The really frustrating part is that sometimes it works and sometimes it doesn't and there's no way to predict when I will observe each behavior.

---

### Post by ssam on 2007-06-18
i suspect there is some sort of hardware problem.

there is a program in the repos called memtest. you could try that.

[http://www.thexlab.com/faqs/aht.html](http://www.thexlab.com/faqs/aht.html) has some information about apple hardware testing.

could you borrow a mac os x install cd, and see if that worked.

---

### Post by Slushdoot on 2007-06-18
I'll try installing OS X again this afternoon.  I began to install it back when I was having trouble booting off of the SCSI drive.  I used its formatter to partition the disk at one point to see if an Apple-created partition would be more effective.  It was not. :p

I have a copy of the G4 Apple Hardware test backed up in a .dmg.  When I have installed OS X I will be able to extract and burn it.  I'll let you know how it goes.

---

### Post by Slushdoot on 2007-06-18
Ok, I installed Panther on the SCSI drive and it went swimmingly.  The machine hasn't missed a beat and passed the Apple Hardware Test so I'm fairly certain it's not a hardware problem.  I'll try Feisty again tomorrow.  Wish me luck. :p

---

