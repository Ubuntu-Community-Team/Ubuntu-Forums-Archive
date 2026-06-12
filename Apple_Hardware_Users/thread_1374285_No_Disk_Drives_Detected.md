---
title: "No Disk Drives Detected"
date: 2010-01-06
forum: Apple Hardware Users
---

### Post by iamdigitalman on 2010-01-06
So, I am using the community build of Ubuntu 9.10, I have an old as dirt Power Macintosh G3 Blue And White, and I can't get it to install. I tried the live CD first of course, and now the alternate. Both tell me that no disk drives detected, even though Mac OS 9, X, and Fedora all detect both my 40gb seagate, my 120gb seagate, and my 120gb maxtor.

I am trying to get this running with some sort of linux for a school project.

What is happening is it asks me what driver to use, and if I select the bottom option that it is none of the above, it asks me to load a driver from a USB flash drive, which I don't know what driver to use. They are all standard IDE devices hooked into the built in bus. I obviously can't move past this point.

Specs:

PowerPC G3 450mhz
1gb of RAM
120gb hard drive
DVD-ROM drive
ZIP 250 drive (currently not hooked up)
PCI ATI Rage 128 16mb video card (stock)
Apple Fast ethernet 10/100 PCI card (machine has built in ethernet, but I am turning this machine into a hardware firewall, so a second NIC is required).

Oh, I have used this machine perfectly with ubuntu before. When I first got it, I started out running Ubuntu 5.10 way back in 2005. I was thinking of downloading and burning 6.06, and upgrading from there. That version seemed to work perfectly on this hardware.

---

### Post by llamabr on 2010-01-06
Unless you're wedded to ubuntu for some reason, I find that debian has better support for the ppc architecture.  I'm running debian lenny on my ibook.  I just did a reinstall yesterday in 15 minutes, with no problems.

---

### Post by iamdigitalman on 2010-01-06
You know, I never thought of debian. I like the debian distros more than red hat based ones anyway. I actually have 4.0 for ppc burned to a CD already. Can you update from 4.0 to 5.0 easily? That was one of the biggest disappointments about Fedora. You need to burn a new disc, or do a whole bunch of stuff to get it to update. What makes that worse is that we are using Fedora 8.0 in my class, which is over 2 years outdated. A lot can change in 2 years.

Still, if possible, I would like to get Ubuntu running. I burned 2 CDs already for this project alone. Ubuntu is my favorite disto by far, so I really hope(d) to get it running.

---

### Post by iamdigitalman on 2010-01-08
I tried the Debian 4.0 CD. It's the net install disc, and I ended up getting an error about an invalid key on the first package for the base system. I guess that is too out of date too.

This is getting frustrating. The 9.10 live cd did not work because it did not automatically log in for some reason, and refused every login info I gave it.

---

### Post by linuxopjemac on 2010-01-08
> This is getting frustrating. The 9.10 live cd did not work because it did not automatically log in for some reason, and refused every login info I gave it.

Maybe your PRAM battery is dead. YOu might want to consider this thread:

[http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram](http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram)

---

### Post by grof on 2010-01-08
Hello guys...

I have one of this old machines at my workbench :)
B&W G3 PPC Mac and I have same problems (login [solved via link in previous post] and no IDE recognizing.

But, I do some analyses and concluded that the main reason for no detecting HDDs is missing of pata_cmd64x or cmd64x modules in kernel build.

Ubuntu 9.04 uses cmd64x (kernel 2.6.28 )
Fedora 12 PPC uses pata_cmd64x  (kernel 2.6.31 as in Koala)

Today I will manually add this module and will see what happened.
But, the main issue will persist, how include this missing driver after installation to hard drive?

I will try with rebuilding initrd image with mkinitramfs command, and exchange it with original one in /boot.

I thinking about building "third party driver update CD" with pata_cmd64x module, but I must investigate how to create valid driver CD. Because, no documentations about this on inet...
Only something here:
[https://wiki.ubuntu.com/Ubiquity/DriverUpdates](https://wiki.ubuntu.com/Ubiquity/DriverUpdates)
(Vendor process)

---

### Post by linuxopjemac on 2010-01-08
Grof: good idea. Let us know how it will work out...maybe you can post what you did to help others!

---

### Post by grof on 2010-01-09
I am successfully activate hard drives in Koala with external pata_cmd64x driver under LiveCD.
I'm still in processing of simplify installer for this  kernel module.

Currently I have problems with bootstraping because something wrong with yaboot under Koala. (If I reconfigure yaboot.conf with old yaboot under Ubuntu 9.04, than all works fine.)

I will publish all of my work here very soon.

So, stay tuned :)

---

### Post by linuxopjemac on 2010-01-09
You will have a nice installer soon, which should work for the older G3 machines....keep us informed...

---

### Post by iamdigitalman on 2010-01-09
yes, please keep us informed on this. I would like to try this out on my box as soon as possible, so maybe you could PM me with the file and instructions so I can get it running.

I don't even have a PRAM battery in the machine (whoops). Never really needed it with OS X. I can try resetting the PRAM before I attempt installing, but I also have a few of the buggers floating around here, and I believe they are good. Maybe that is why fedora was not installing, or it could be a bad DVD-ROM drive, because I tried booting my Ubuntu CD in it, and it did not boot after a few attempts, but it worked perfectly under the 32x black CD-ROM drive I have.

---

### Post by grof on 2010-01-10
Aha, the installer is mostly finished :)
All works fine except one thing!

pata_cmd64x driver do not survive kernel updating via ubuntu update process, yet. Update procedure do not include them to new initrd.img file, so I must fix that.

Now, I'm finding solution with DKMS system, and when I finished that, I'll published all here.

---

### Post by linuxopjemac on 2010-01-10
> I don't even have a PRAM battery in the machine (whoops). Never really needed it with OS X. I can try resetting the PRAM before I attempt installing, but I also have a few of the buggers floating around here, and I believe they are good. Maybe that is why fedora was not installing, or it could be a bad DVD-ROM drive, because I tried booting my Ubuntu CD in it, and it did not boot after a few attempts, but it worked perfectly under the 32x black CD-ROM drive I have.

The solution to this is to set the date and time in open firmware:
[http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram](http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram)

---

### Post by iamdigitalman on 2010-01-10
I did set the time and date via open firmware. It did work, as it showed up correctly under the Ubuntu disk at the login screen. It turns out that was a bad image file, so I downloaded a new one during the night, and burned it this morning. Despite telling imgburn to do it at 1x, it did it at 12x, but it works. I am typing this under the live CD on the B&W right now.

However, the issue with the disk drive is also in this disc as well. No disk drives detected by the installer, or by gparted.

I am thinking of going with Debian at this point. the 5.0.3 net installer I have works great, but it froze at the install software at 1% saying please wait. I will try it again.

Hopefully this gets fixed in a later build. Maybe grof can submit his work for the 10.04 community build. I will probably start using Ubuntu on this machine again if that is the case. Tiger is starting to look really long in the tooth, and with my mobileme expired, there is no use running it.

---

### Post by linuxopjemac on 2010-01-11
Maybe you have to try again with the Debian installer. I had the same issues with older hardware. Sometimes, the CD drives don't really read those burnt CD's very well. The only solution to that is burning at (very) low speed. Just try again. I am sure it will work out for you.

---

### Post by grof on 2010-01-11
I'm finish with workaround for HDD recognizing.

I'm tested this on my Vbox machine (not on PPC). So feel free to try.

Here are the instructions (included into package, too):

Installation procedure must be done in two stages.

Stage 1 – prior Installation (on LiveCD)
-----------------------------------------
Steps:

1. Startup LiveCD and wait to be booted up.
2. When system is up, install attached pata_cmd64x.deb package
3. Open terminal and type:
[FONT="Courier New"]cd /usr/src/pata_cmd64x-0.1
sudo sh install-livecd.sh[/FONT]
4. After that (for a few seconds) hard drives will up! 
5. Now, you can start Installation procedure, and install Ubuntu onto wanted hard drive.
6. When installation procedure finished **DO NOT RESTART PPC YET!** You must copy updated initrd.img to /boot dir on hard drive where Ubuntu installed. So, type:
[FONT="Courier New"]ls /media[/FONT]
Look what is the name of HDD where you installed Ubuntu
[FONT="Courier New"]cp /usr/src/pata_cmd64x-0.1/initrd.img-`uname -r` /media/<enter name of HDD here>/boot[/FONT]
7. Now, you can restart PPC!
8. When boot menu appeared on screen, just press enter, and if you did procedure well, Ubuntu should be booted properly.
9. But this is not finish. We have to do some job, yet. :)

Stage 2 – after Installation (on HDD itself)
---------------------------------------------
Steps: 

1. When you booted to hard drive, take once again attached .deb package and install them. 
**IMPORTANT!**
Do this PRIOR first update of the system.
2. Again, open terminal and type:
[FONT="Courier New"]cd /usr/src/pata_cmd64x-0.1
sudo sh install.sh[/FONT]
3. Wait for procedure will be done and then update your PPC.
4. Do reboot as is suggested and see is it all right.
5. Enjoy Koala at your PPC G3.

---

### Post by linuxopjemac on 2010-01-11
good work! I hope someone else can test if it works...

---

### Post by grof on 2010-01-12
> **linuxopjemac said:**
> good work! I hope someone else can test if it works...

I tested yesterday with LiveCD on Mac BW G3. It works, but prior start install-livecd.sh script do (I'll fix that in the near future ): 

sudo chmod +x *.sh 

And, yaboot definitely does not work with this machine. I will find the solution for this issue and implement that to this install scripts. (Ubuntu's 9.04 yaboot works well)

---

### Post by grof on 2010-01-13
I found issue with yaboot under Koala.

This issue is not in yaboot itself, but in drivers.

Explanation:

pata_cmd64x driver assign drives as SCSI devices (/dev/**sd**x), and not as IDE devices (/dev(**hd**x).
So, this confusing yaboot's ybin program when it writing device-boot parameter in NVRAM. 

Resolving this can be done in two ways.
_1st and worse:_ call ybin with -o hd:x parameter (x - number of bootstrap partition)(this is actually workaround of workaround :) )
_2nd and better:_ Using old cmd64x driver which assign drives as IDE devices.

I will package this cmd64x driver very soon, so be patient a little more :).

---

### Post by linuxopjemac on 2010-01-13
if all is finished, hand it over to the developers. Maybe they can offer the installer as an alternative for PPC machines.

---

### Post by grof on 2010-01-13
> **linuxopjemac said:**
> if all is finished, hand it over to the developers. Maybe they can offer the installer as an alternative for PPC machines.

OK, I will, good idea!

But first I want to test once again...

---

### Post by iamdigitalman on 2010-01-19
Ok well, I ended up using 9.04 for the project. Will be using it to run Firestarter. I burned 9.04 to a CD, and installed it, but I encountered a couple odd errors when I tired updating to 9.10 twice:

The first time it updated perfectly, but then a set of packages came in software update. I don't remember hitting install, but it must have. But when it rebooted, I was dropped into busybox with a message above saying it gave up waiting for root device, and that my /dev/hdc3 did not exist. Upon reinstall and attempt to upgrade again, it happened right after the 9.10 upgrade. The shell was named initramfs.

Oh, and I managed to set the time using open firmware. here's how:

1. boot into open firmware by pressing and holding command+option+o+f after pressing the power button.

2. at the prompt, type time&date and hit enter to display the time in the nvram.

3. type in the time using the time&date command in this format:
time&date hh:mm:ss mm/dd/yy press enter. It will say something like no value OK. Type time&date and press enter again to verify the time.

4. Type mac-boot to continue booting.

I found that with the time&date command, it does not work with the 4 yyyy format, as indicated here in the comments: [http://www.macosxhints.com/article.php?story=20060814075952448](http://www.macosxhints.com/article.php?story=20060814075952448)

the decimal dev rtc never worked for me.

Hope the fix is in 10.04 so I can use this old beast as a linux box again. Can't wait until April!!

---

### Post by crutchshop on 2010-01-22
I am in the same position and can say that I followed the same steps with the same g3 bw and had the same problem.  9.04 works fine but the upgrade to 9.10 knocked out my drive detection.  I'm gonna try with a SCSI drive I have and see if the same issues persist or go away.  I intend on using this machine as a NAS for video and music storage but I don't know what SATA PCI card to buy or if it will work.  Any thoughts?

---

### Post by grof on 2010-01-26
> **crutchshop said:**
> I am in the same position and can say that I followed the same steps with the same g3 bw and had the same problem.  9.04 works fine but the upgrade to 9.10 knocked out my drive detection.  I'm gonna try with a SCSI drive I have and see if the same issues persist or go away.  I intend on using this machine as a NAS for video and music storage but I don't know what SATA PCI card to buy or if it will work.  Any thoughts?

I prepared missing cmd64x driver needed for successfully run hard drives in BW G3 PPC. 

I'll publish link here, soon. :)

---

### Post by linuxopjemac on 2010-01-26
very well done Grof!!! You found a way to install Karmic on B&W G3's, a difficult one...I hope the Ubuntu team will take your installer as an option...

---

### Post by grof on 2010-01-26
> **linuxopjemac said:**
> very well done Grof!!! You found a way to install Karmic on B&W G3's, a difficult one...I hope the Ubuntu team will take your installer as an option...

It will be enough to include cmd64x module in kernel-tree.
This module exists in kernel's source package but not in binary.
For some reason it is not compiled...

---

### Post by linuxopjemac on 2010-01-26
it has been missing in the installers since 8.04  :(
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/296263](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/296263)

---

### Post by grof on 2010-01-27
This is final procedure for successfully install cmd64x driver:

Installation procedure must be done in two stages.

_**Stage 1 &#8211; prior Installation (on LiveCD)**_

Steps:

[LIST=1]
[*]Startup LiveCD and wait to be booted up.
[*]When system is up, unpack attached **cmd64x-0.1.tar.gz** archive and install **cmd64x-dkms_0.1_all.deb** package
[*]Open terminal and type:
```
cd /usr/src/cmd64x-0.1
sudo sh install-livecd.sh
```
[*]After that (for a few seconds) hard drives will wake-up! 
[*]Now, you can start Installation procedure, and install Ubuntu onto wanted hard drive.
[*]When installation procedure finished **DO NOT RESTART PPC YET! **You **must** copy updated initrd.img to /boot dir on hard drive where Ubuntu installed. So, type:
```
ls /media
```
Look what is the name of HDD where you installed Ubuntu
```
cp /usr/src/cmd64x-0.1/initrd.img-`uname -r` /media/<enter name of HDD here>/boot
```
[*]Now, you can restart PPC!
[*]When boot menu appeared on screen, just press enter, and if you did procedure well, Ubuntu should be booted properly.
[*]But this is not finish. We have to do some job, yet. :)
[/LIST]

_**Stage 2 &#8211; after Installation (on HDD itself)**_

Steps: 

[LIST=1]
[*]When you booted from hard drive, once again unpack attached **cmd64x-0.1.tar.gz** archive and install **cmd64x-dkms_0.1_all.deb** package and install them. 
**IMPORTANT!**
Do this PRIOR first update of the system.
[*]Again, open terminal and type:
```
cd /usr/src/cmd64x-0.1
sudo sh install.sh
```
[*]Wait for procedure will be done and then update your PPC.
[*]Do reboot as is suggested and see is it all right.
[*]Enjoy Koala at your PPC G3.
[/LIST]

I reported this issue as a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131)

---

### Post by pietroman on 2010-12-11
Hi, 

Is there anyone who can briefly explain how to install the cmd64x.ko driver for Ubuntu 10.04?
I want to install it on a G3 B&W, tried everything as explained in the final procedure, but it gives me every time an error "FATAL: Module cmd64x not found" after the sudo sh install-livecd.sh command.  Tried other thing such as copying the file in the requested directory (/lib/modules/2.6.32-21-powerpc/updates/dkms/), also using the modprobe command, ... but nothing helps.

I'm not very familiar with linux, so a step-by-step explanation is highly appreciated ;-)

Thx in advance!

---

### Post by B_Free on 2011-03-25
If this problem has been reported, has the installer been fixed?

---

### Post by linuxopjemac on 2011-03-26
B_free: nope.

---

### Post by B_Free on 2011-03-27
Within the iso image, what is the file that is defective?

---

### Post by B_Free on 2011-03-28
Would the installer from 8.04 or another Debian release work?

---

