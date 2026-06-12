---
title: "First Post__(Intel Imac) Matsushita drive issues!"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by rezist on 2006-11-05
First I'd like to say that this is my first time deviating from the MacOS and Its has been liberating. However after running Edgy for two months now, and installing everything that every single guide in the known universe has instructed, I am still unable to have my DVD/CD drive read data on any type of disk. the drive is mounted and identifies when a disk is inserted as well as ejects them. A "cd rom" icon appears on the desktop when I put one in the drive yet it lists no content. I'm at a complete loss and have been screwing around for weeks on this issue! I humbly ask for some assistance.](*,)

---

### Post by autocrosser on 2006-11-05
Glad to see another X-OSX'er!! I was one of the beta-testers for OSX & finally got tired of Steve's wandering ways.....

In any case--Let's take a look at a few things--do a quick copy of your /etc/fstab & post it--also--give me a idea what you have tried & the answers (if any) you got from them.....

---

### Post by rezist on 2006-11-05
Yeah wandering ways and wnadering eyes, what's the deal with dashboard advisory attempting to connect all over the place ten times a day in OS X? Iv'e been on board since system 7, it's great to wake up and find a suitable alternative. Although I'm a video editor so I still have to use OS X for work....

The command /etc/fstab output is permission denied, last night before shut down I entered that command and attempted to match it to some other posts here and it gave me a legnthy output but today I'm not sure why it says permission denied, even as a root user... I aplogise for being a nOOb

---

### Post by autocrosser on 2006-11-05
Yea--I started with System 6 & was "almost" one of the first when Steve wanted testers after the "Public Beta"--I got a shiny disc of 10.0.04 to run & break my G3/400:rolleyes:

In any case--you can nav to /etc/fstab & double-click it to look(use text-editor--you can't save it unless you are sudo)--or copy/paste it to your desktop (remember to rename it--add .txt to the end or the forum won't let you upload it:-k)

Glad to talk with another "old-timer" been computing from the mid-70's--UNIX mainframes & port-sharing (wow--I do sound old)

---

### Post by rezist on 2006-11-05
Okay, here is the info that you asked for... I have no idea what this folder is for, or what this information is. I assume it holds instructions for Ubuntu's access to my drive?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=7f4f8612-bb09-4066-a6b2-6cf5282389e9 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=fcccc55d-56d5-4b36-a604-1716c4a90de5 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by autocrosser on 2006-11-05
Well--Let's see if we can change things;)  Goto a terminal and type in: sudo gedit /etc/fstab --you will be asked for your user password-input then <return>  this will open gedit with root permissions so you can edit the file:)

Look at the line:
 /dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

We'll change this line to:
/dev/hdb        /media/cdrom0   auto   user,noauto     0       0

This "should" allow you to open "any" file you put into your CD burner (what this "really" does--is "force" the OS to see what filesystem is on the disc & display it)

Save the file--you will need to reboot (that is easiest) to set the change--take a look after you reboot & post you results;)


Note: you should also go into Synaptic & type "hfs" into the search field--download anything that looks like it has to do with Mac OS filesystem;)

---

### Post by rezist on 2006-11-05
Thanks... I edited that file, and also opened the package manager. I searched for files that seemed related to Mac filesystems however there wasn't anything that jumped out at me... lots of libparted, lufs, squash, shfs ... not entirely sure what those actually pretain to. As a beginner is there anywhere you would direct me in terms of learning how to make the changes you showed me today? I guess I lack a basic understanding of Unix-Linux, I shoud most likely start there...

---

### Post by rezist on 2006-11-05
after the edit my file looks like so...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=7f4f8612-bb09-4066-a6b2-6cf5282389e9 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=fcccc55d-56d5-4b36-a604-1716c4a90de5 none swap sw 0 0
/dev/hdb        /media/cdrom0   auto user,noauto     0       

There was no change in Ubuntu reading my data disks. I guess the fact that I didn't download anything from the package manager is the reason Ubuntu still can't display the disks data. I will do some research on OS X filesystems and see if I can pick out what you told me too... Thanks for your help!

---

### Post by rezist on 2006-11-05
okay, I do have several files already installed from the package manager, they include... "hfsplus, hfsutils, libhfspO, libparted1.7-1, libparted1.6-13, mkisofs, parted."

Not sure if I mentioned this or if it matters but I'm running Ubuntu with Parallels. I was thinking to possibly install all of them, not sure if this would be a bad thing though.

---

### Post by autocrosser on 2006-11-05
Well--go ahead & install hfsplus & hfsutils--these will allow you better access to Mac-formatted information. I don't know about Parallels--I always have done a "real" install on a harddrive--maybe Parallels is not allowing use of removable media--do you have any problems with USB devices?

Interesting that "auto" didn't do anything--it's also possible that the drive is not seen correctly by linux--What type of Intel Mac are you using?  Also--take a look at Device Manager--It will have some very good info on the system.

---

### Post by rezist on 2006-11-05
I'm using the first Imac with a core duo. Funny thing when I put a DVD, CD in my drive when Parllels/Ubuntu is running, it doesn't show up on my OS X desktop, only in Ubuntu. (I have Ubuntu fullscreen on a second monitor) But when I place a USB flash drive in my Mac it only appears on the OS X desktop and not Ubuntu. Odd. Device manager does have info about my drive, yet to me it might as well be in Korean, I can't make heads or tails.

I have installed everything that appears after a HFS search with the package manager, restarted and still have no data showing up! Hmmm. I don't want to give up an Ubuntu... and it is amazing to be able to run both OS's at the same time, but maybe not running Ubuntu natively, but through Parallels is the problem? This seems weird because my wireless network was up and running with absolutly NO tweaking at all but something as simple as a DVD/CD drive is giving me all this trouble.

---

### Post by autocrosser on 2006-11-05
Well-I'm fresh out of ideas--you might look at Parallels website to see if this is a known problem--you might also see if you can use/borrow/buy a external USB CD-RW/DVD drive that is a different make to see it the problem is with the Matsu drive--And of course you could install Ubuntu on your drive--but I think there is still problems with the boot-loader--You could check the PPC/Mac Intel part of the forum for that info---

In any case--Glad to see another Apple person moving to Linux---We need all the people we can get--8)

---

### Post by Malac on 2006-11-09
Can I just, firstly, say I'm not a Mac user and have never used Parallels so this may not be relevant at all but have you tried inserting the CD/DVD into the drive then starting Parallels/Ubuntu and seeing if you can access the disc.
I know with early VM betas there was a bug where if there was no disc in the drive at startup of the VM it would basically screw the CD drive access up for that session.
Not sure this will help but it may be worth a try.

---

### Post by DonnieP on 2006-11-10
I also run Ubuntu in a Parallels VM on Intel iMac.  I don't know about data CDs, but audio CDs have been addressed in the Parallels forums.  Parallels does not support audio CDs in VM (they didn't explain why).  (Of course, you can play audio CDs on the Mac side at the same time you're running Ubuntu, so it's not really that big a deal.)  For data CDs maybe the better approach is to examine why you need the CD in Ubuntu and then come up with a workaround.  For instance, you can always copy data between the Mac host and Ubuntu guest VM and access the CD on the Mac side.  If direct Ubuntu access to the CD is an absolute requirement, you may have to explore the dual boot route.

---

### Post by autocrosser on 2006-11-10
Well--that seems to settle that--I've always moved towards a "real' install--you can format a external USB drive for HFS+ & have it show up in both OS--And there is a way to do Mac-on-Linux;) (hint-hint) Linux plays nicer than OSX when it comes to "sharing"

---

### Post by rezist on 2006-11-30
Thanks for the help, it has been revealed that Parallels doesn't support DVD/CD's as you have stated. I appreciate the help!

---

