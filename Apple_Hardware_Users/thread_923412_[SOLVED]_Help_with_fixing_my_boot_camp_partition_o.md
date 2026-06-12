---
title: "[SOLVED] Help with fixing my boot camp partition on a triple boot rig."
date: 2008-09-18
forum: Apple Hardware Users
---

### Post by dsmoot on 2008-09-18
I'm going to blast everything out and start over unless somebody has an easy fix.  I'm one of the millions in the Houston area affected by Ike.  I've got power but no broadband (just phone tethering) and lots of time on my hand until the re-open my job.  So I decided to finally get around to setting up triple boot.

I've got a Macbook pro 2,1.  Until yesterday, it was config'ed as a bootcamp setup with OS X and Windows.  I've also got vmware installed to run the windows partition.

Yesterday I backed up the Mac partition and the windows partition and started working on making it triple boot Kubuntu 8.04.  I split off a 20 gig partition using the OS X disk util.  I installed refit.  I booted from the Kubuntu CD.  I formatted the new partition ext3 and I noticed I had 500MB free space so I made it swap.  

Kubuntu boots and works fine.  I have not gotten the wireless working yet but that should not be hard once broadband returns.

My problem is I appear to have broken my Windows install but in a wierd way.  I thought I might have busted the MBR / boot stuff but the boot process starts normally and it starts loading dll's then it just reboots.  When I tried to start my windows partition it complains about a corrupt hal.dll in system32.  I'm going to boot into kubuntu and try to overwrite hal.dll with a clean copy off another windows box but I am not expecting success.

So my question:
I have a XP license and a full XP backup done using the built in XP backup feature (.bkf file).  Is there anyway I can get into a windows recovery mode and re-install my backup to that partition only?  Boot camp assistant complains about my partitioning scheme and won't let me do anything.  I know I could boot off of the XP CD but I know that would totally hose my rEfit setup.  

I may just backup the Kubuntu partition and blow everything out and start from scratch.  Any suggestions? 

David

---

### Post by cyberdork33 on 2008-09-18
> **dsmoot said:**
> My problem is I appear to have broken my Windows install but in a wierd way.  I thought I might have busted the MBR / boot stuff but the boot process starts normally and it starts loading dll's then it just reboots.  When I tried to start my windows partition it complains about a corrupt hal.dll in system32.  I'm going to boot into kubuntu and try to overwrite hal.dll with a clean copy off another windows box but I am not expecting success.That probably won't work. Windows has a fit if you change the partitioning scheme after you have already installed. You probabaly need to reinstall.

> **dsmoot said:**
> Boot camp assistant complains about my partitioning scheme and won't let me do anything.  I know I could boot off of the XP CD but I know that would totally hose my rEfit setup.  Just use gparted on the Ubuntu CD. Booting the XP CD will not mess up rEFIt either.

> **dsmoot said:**
> I may just backup the Kubuntu partition and blow everything out and start from scratch.  Any suggestions? Just reinstall windows to the partition you have. It will detect the new partition scheme and set everything up from there. Since you are starting over, you might as well fix the swap to the proper size as well. You should have a partition layout something like this in the end:

1. EFI partition
2. OS X
3. Kubuntu Root
4. Windows
5. Swap

---

### Post by prshah on 2008-09-18
> **dsmoot said:**
> 
I thought I might have busted the MBR / boot stuff but the boot process starts normally and it starts loading dll's then it just reboots.  When I tried to start my windows partition it complains about a corrupt hal.dll in system32.  I'm going to boot into kubuntu and try to overwrite hal.dll with a clean copy off another windows box but I am not expecting success.

Surprisingly, replacing the hal.dll file from another (working) machine _will_ work.

As for the reboot, it is being automatically triggered because of some misconfiguration. You can get more details by tapping F8 (after BIOS check, but _before_ windows splashscreen; if you see the splashscreen, you've missed the chance) which will load up the startup options menu. In that menu, choose "Disable Automatic Restart on Failure" option, and then proceed normally; this time, instead of a reboot, you'll get the (in)famous blue screen with details of the error. Posting back those details may help in clearing this up.

Unfortunately there's no advice I can offer about the rest of your post.

---

### Post by dsmoot on 2008-09-18
> **prshah said:**
> Surprisingly, replacing the hal.dll file from another (working) machine _will_ work.

As for the reboot, it is being automatically triggered because of some misconfiguration. You can get more details by tapping F8 (after BIOS check, but _before_ windows splashscreen; if you see the splashscreen, you've missed the chance) which will load up the startup options menu. In that menu, choose "Disable Automatic Restart on Failure" option, and then proceed normally; this time, instead of a reboot, you'll get the (in)famous blue screen with details of the error. Posting back those details may help in clearing this up.

Unfortunately there's no advice I can offer about the rest of your post.

The hal.dll replace did not work (probably because I bet that was not my root problem) I did as you suggested and the error code is "UNMOUNTABLE_BOOT_VOLUME".  I think splitting the OSX partition and using the free space as swap somehow screwed up the windows boot process.

So some questions for those reading the thread and willing to help:

If I insert the XP CD, install to the windows partition, then re-install my backup, will I damage the refit or the ability to boot OSX and Kubuntu?  I just want to be sure before I screw it up worse.

I'm struggling getting madwifi to work.  I downloaded the latest (which may be my mistake) version from svn and did the make, sudo make install, sudo modprobe ath_pci with no errors.  sudo iwlist ath0 scan works and shows me the name of a local access point that has no encryption.  But this is where I hang up.  The KDE network panels can't seem to see the network.  I went to iwconfig and tried every variation of the iwconfig command.  They never returned any errors but they never gave me a working connection either.  

By the way, you might want to update the FAQ, the path pointed to by benanzo for the madwifi drivers no longer exists.  He calls out [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) but that path is no longer valid, it is [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk).  

I'm doing a svn co to my USB stick while booted into OSX then doing a build under kubuntu.  I can't get svn working on my kubuntu install until I get networking going.  

Keyboard layout is a little annoying...  I've got hit double quotes twice to get the quotes and even then they are not the "right" double quotes.

If I can just get networking up, It will be a lot easier to bring everything else up to speed.  

Thanks for the help guys.  I'm sure I'll be back to get this thing set up right.

David

Edit:  Think I found my mistake with madwifi.... in [http://madwi&#64257;.org/wiki/UserDocs/FirstTimeHowTo](http://madwi&#64257;.org/wiki/UserDocs/FirstTimeHowTo) they show a critical step not in benanzo's post:
wlanconfig ath0 create wlandev wifi0 wlanmode sta

So time to reboot and try again.  Hopefully my next post is from konquerer.

David

---

### Post by prshah on 2008-09-18
> **dsmoot said:**
> 
and the error code is "UNMOUNTABLE_BOOT_VOLUME".  

Is the XP partition set to "active"? ```
sudo fdisk -l
``` from ubuntu, then check if there's a "*" next to the XP partition in the second column (Boot). If you want to check through XP, you can use the CD's recovery console and run "fdisk" off it.

If it's not active, set it as active (through either Ubuntu's fdisk / Windows fdisk).

Flagging a partition as active will not affect the data in that partition in any way.

However, I have _absolutely_ no knowledge of the mac side of things, and I don't know what "refit" does, etc; you have been suitably advised about my ignorance :)

---

### Post by dsmoot on 2008-09-18
Yep, its set to active.  I think I'll risk a boot from windows install CD and reinstall.  If it hoses up the other partitions, I'll just start from scratch and re-do everything.  

Thanks again for your help.  I got a little further with madwifi but not there yet.

David

---

### Post by cyberdork33 on 2008-09-18
> **dsmoot said:**
> If I insert the XP CD, install to the windows partition, then re-install my backup, will I damage the refit or the ability to boot OSX and Kubuntu?  I just want to be sure before I screw it up worse.no, no problem there.

> **dsmoot said:**
> I'm struggling getting madwifi to work.  I downloaded the latest (which may be my mistake) version from svn and did the make, sudo make install, sudo modprobe ath_pci with no errors.  sudo iwlist ath0 scan works and shows me the name of a local access point that has no encryption.  But this is where I hang up.  The KDE network panels can't seem to see the network.  I went to iwconfig and tried every variation of the iwconfig command.  They never returned any errors but they never gave me a working connection either.  

By the way, you might want to update the FAQ, the path pointed to by benanzo for the madwifi drivers no longer exists.  He calls out [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) but that path is no longer valid, it is [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk).  

I'm doing a svn co to my USB stick while booted into OSX then doing a build under kubuntu.  I can't get svn working on my kubuntu install until I get networking going.
You should follow the guide specifically for your particular hardware. See the "Before You Post..." link in my signature.

Why don't you just plug in to ethernet for a bit?

There is also the ath9k driver which might work better for you.

> **dsmoot said:**
> Keyboard layout is a little annoying...  I've got hit double quotes twice to get the quotes and even then they are not the "right" double quotes.I don't really know what you are talking about there...

> **dsmoot said:**
> Yep, its set to active.  I think I'll risk a boot from windows install CD and reinstall.  If it hoses up the other partitions, I'll just start from scratch and re-do everything.
and don't change it as that will just make things worse.

---

### Post by dsmoot on 2008-09-19
> **cyberdork33 said:**
> no, no problem there.


You should follow the guide specifically for your particular hardware. See the "Before You Post..." link in my signature.

Why don't you just plug in to ethernet for a bit?

There is also the ath9k driver which might work better for you.

I don't really know what you are talking about there...


and don't change it as that will just make things worse.

For the record, I did read the FAQ's and stuff before I posted.  My problem was I was starting from a wierd point... Already boot camped but not really partitioned with triple in mind.

I don't have a wired connection available :(.  Comcast still has not fixed my home broadband after Ike.  I'm riding to work with my wife and they offer guest wifi access, no wired connection.
 
I think my problem is a kubuntu issue.  See: [http://ubuntuforums.org/showthread.php?t=779235](http://ubuntuforums.org/showthread.php?t=779235)
I think the knemo package is required but it is not on the install CD.  I was able to get really close to success yesterday... I could join the network and get a DHCP address.  But this network has no wep but requires you to enter a password on a login page.  And KDE for some reason could not detect the network.  I could ping the login server just fine, just no browser access from Konquerer.  And no other browsers on the install CD.

Anyway, it has been a partial success.  I got the triple boot part working last night, now I just have to try to download knemo and its dependencies to a USB stick from OSX and give it a whirl.

Thanks for your help.

David

---

### Post by dsmoot on 2008-09-19
Finally solved the problems I was having but boy was it a PITA.  The wireless access point that I have has no password bu t it requires you to authenticate to a web page.  

Problem 1 was 8.04 kubuntu CD lacks knemo, the network monitor that is critical to use the network.

Problem 2 was Konquerer simply did not work for me to get to the login page.

Solution:  Cheat.  Found a wired connection that I am not authorized to use and download knemo and firefox.  Reboot and follow the directions in the FAQ and I am online.  

Thanks guys.  I´ve got to figure out xorg.conf stuff that works for me.  The trackpad sensitivity is driving me nuts...  Every time I brush the trackpad while typing the cursor jumps.  But all that data is in the FAQ so I am over the hump.

David

---

### Post by cyberdork33 on 2008-09-19
great, can you mark this thread solved (from the thread tools menu)?

---

### Post by dsmoot on 2008-09-19
This is not important enough to warrant a separate thread but I've got to vent...  Who's the genius that put keyboard layouts under "region & language" instead of "keyboard & mouse" on the kubuntu system settings?

I've been googling for 20 minutes trying to figure out how to correct my screwup configuring the keyboard during setup.

slowly coming together... This web connection is so slow it is taking forever to download the packages I want.  Thanks Cyberdork33.  If my job ever sends me back to our Huntsville office again I'll buy you a beer.

David

---

### Post by cyberdork33 on 2008-09-19
> **dsmoot said:**
>  Thanks Cyberdork33.  If my job ever sends me back to our Huntsville office again I'll buy you a beer.
Sounds Good!

---

### Post by keisunesu on 2008-11-02
I'm having a similar problem to the opening post in that when Windows starts to boot the computer suddenly restarts.  I tried pressing F8 after selecting the "Start Windows with last known good settings" option, but all I got was a blank screen.  After pressing ctrl-alt-del, the Windows splash screen appeared, and then the computer restarted again.

---

### Post by cyberdork33 on 2008-11-02
> **keisunesu said:**
> I'm having a similar problem to the opening post in that when Windows starts to boot the computer suddenly restarts.  I tried pressing F8 after selecting the "Start Windows with last known good settings" option, but all I got was a blank screen.  After pressing ctrl-alt-del, the Windows splash screen appeared, and then the computer restarted again.
try booting into safe mode. Isn't that option on the screen that has "start windows with last known good settings"?

---

### Post by keisunesu on 2008-11-02
It restarts when I pick Safe Mode too.

---

### Post by dsmoot on 2008-11-02
I'm still not sure why but Windows freaks out after you install Linux.  

You pretty much have to re-install windows.  You can select some option to turn off automatically restarting after an error.  Then you will see it crash and complain about hal.dll.  I fought with Windows for a while trying to "fix" it but eventually gave up.  The 2 times I set this rig up, both times I had to install windows twice.

You might also take a look at this link that I recently saw on slashdot:
[http://www.anomalousanomaly.com/2008/10/31/triple-booting-your-mac/](http://www.anomalousanomaly.com/2008/10/31/triple-booting-your-mac/)

If I did not already have a stable rig I would try out his ideas.

David

---

### Post by cyberdork33 on 2008-11-02
> **dsmoot said:**
> You might also take a look at this link that I recently saw on slashdot:
[http://www.anomalousanomaly.com/2008/10/31/triple-booting-your-mac/](http://www.anomalousanomaly.com/2008/10/31/triple-booting-your-mac/)

Good find. I will read this tomorrow.

---

