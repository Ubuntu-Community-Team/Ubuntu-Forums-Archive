---
title: "Booting/Cloning/A Big Mess"
date: 2012-05-24
forum: Any Other OS
---

### Post by Shadius on 2012-05-24
Hey everybody,

I have Windows XP and Ubuntu both on separate hard drives. However, my Windows XP hard drive is failing (since I've had it forever) so I want to clone my Windows XP hard drive to another hard drive. The Windows XP never came with an installation disk, just a Recovery CD, so I just can't reinstall my Windows XP to another hard drive. :( The computer is a [Compaq Presario 5410US]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00009504&cc=us&lc=en&dlc=en&product=93299") (if that helps with specs) and both drives are hooked up with no room for a third drive. My thinking is that I have to unplug the Ubuntu hard drive, plug in the new hard drive that Windows XP will be cloned to, and then log into Windows and use whatever software (hopefully, you can suggest one) to do the cloning process. However, when I disconnect the Ubuntu hard drive and try to start up my computer with only the Windows hard drive connected, I get some kind of black screen, maybe GRUB. I think it's because GRUB was written to the MBR and the Windows bootloader is now gone. I know I can restore the MBR of my Windows hard drive using Boot-Repair and GRUB no longer shows up for me to be able to log into Ubuntu, but I am wondering if I can configure it so that when I disconnect my Ubuntu hard drive, it picks up my Windows XP hard drive and lets me be able to log into my Windows XP as if Ubuntu was never there, and when I plug back in my Ubuntu hard drive, it picks it up and gives me back GRUB. Is that possible?

---

### Post by kc1di on 2012-05-24
a couple of disks that may be of help are:
Clonezilla - [http://www.clonezilla.org/]("http://www.clonezilla.org/")
And partedmagic
[http://partedmagic.com/doku.php]("http://partedmagic.com/doku.php")

Believe they will both do the job. 

As far as your boot problem don't think it will be a problem as these are both live cd's and will boot to their programs.

---

### Post by wilee-nilee on 2012-05-24
Use the boot-repair and run the create boot info summary info only and post the HTTP address.

---

### Post by Shadius on 2012-05-24
> **wilee-nilee said:**
> Use the boot-repair and run the create boot info summary info only and post the HTTP address.

Here you go: [Boot Info Summary]("http://paste.ubuntu.com/1005630/")

---

### Post by Shadius on 2012-05-24
> **kc1di said:**
> a couple of disks that may be of help are:
Clonezilla - [http://www.clonezilla.org/]("http://www.clonezilla.org/")
And partedmagic
[http://partedmagic.com/doku.php]("http://partedmagic.com/doku.php")

Believe they will both do the job. 

As far as your boot problem don't think it will be a problem as these are both live cd's and will boot to their programs.

Right, I know that the Live CDs will boot up, but am I right in my thinking that I have to disconnect the Ubuntu drive, plug in the destination drive, run the Live CD, and then proceed to clone the Windows XP drive? Thank you for those links. Clonezilla looks scary since I have no clue about command line.

---

### Post by kc1di on 2012-05-24
> **Shadius said:**
> Right, I know that the Live CDs will boot up, but am I right in my thinking that I have to disconnect the Ubuntu drive, plug in the destination drive, run the Live CD, and then proceed to clone the Windows XP drive? Thank you for those links. Clonezilla looks scary since I have no clue about command line.

yes you right about that you will have to have the new drive installed. But you do not have to boot the machine from the installed grub so don't worry about fixing that until you get the new drive cloned.  I like partedmagic. it works well. 

you can boot into the live cd and it will do the work don't know how much data has to be transferred but should take an hour or two.

good luck

---

### Post by wilee-nilee on 2012-05-24
> **Shadius said:**
> Here you go: [Boot Info Summary]("http://paste.ubuntu.com/1005630/")

The recovery disc will allow you to load the XP bootloader to the mbr of the new HD. I assume this disc gets you to the recovery, it is for using a recovery partition, I would think the recovery terminal as well.

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Grub in ubuntu will find the XP installation and add it to its menu if you run in ubuntu .

```
sudo update-grub
```

This all works, my hope is, is the XP salvagable from that HD.

---

### Post by Shadius on 2012-05-24
> **kc1di said:**
> yes you right about that you will have to have the new drive installed. But you do not have to boot the machine from the installed grub so don't worry about fixing that until you get the new drive cloned.  I like partedmagic. it works well. 

you can boot into the live cd and it will do the work don't know how much data has to be transferred but should take an hour or two.

good luck

*Sigh of relief* I cannot thank you enough. :D I can finally save my Windows XP! So I'm going to make the Parted Magic LiveCD and give it a try. I will be posting back here on my laptop. Thank you!

---

### Post by wilee-nilee on 2012-05-24
I would just use gparted on the live cd to do a copy and paste of the XP from the old drive to the new one.

You do this like any copy and paste copy the original; with a right click go to the HD dropdown in the top right, bring up the new drive, and paste to the NFTS you have made in the new one.

This saves the original as is in case of problems.

The receiving partition on the new HD has to be of equal size or bigger.

Then if you want that new HD to boot XP individually follow the link on loading its mbr in my last post.

---

### Post by Shadius on 2012-05-24
> **wilee-nilee said:**
> The recovery disc will allow you to load the XP bootloader to the mbr of the new HD. I assume this disc gets you to the recovery, it is for using a recovery partition, I would think the recovery terminal as well.

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Grub in ubuntu will find the XP installation and add it to its menu if you run in ubuntu .

```
sudo update-grub
```

This all works, my hope is, is the XP salvagable from that HD.

It's Windows XP Home Edition so it doesn't have the Recovery Console partition. I've used the Recovery CD to do a Factory Restore before. Now my question is, before cloning the Windows XP Home Edition, should I restore the MBR of that drive so that the MBR is cloned onto the new drive?

---

### Post by Dave_in_MD on 2012-05-24
> **Shadius said:**
> Hey everybody,

I have Windows XP and Ubuntu both on separate hard drives. However, my Windows XP hard drive is failing (since I've had it forever) so I want to clone my Windows XP hard drive to another hard drive. The Windows XP never came with an installation disk, just a Recovery CD, so I just can't reinstall my Windows XP to another hard drive. :( The computer is a [Compaq Presario 5410US]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00009504&cc=us&lc=en&dlc=en&product=93299") (if that helps with specs) and both drives are hooked up with no room for a third drive. My thinking is that I have to unplug the Ubuntu hard drive, plug in the new hard drive that Windows XP will be cloned to, and then log into Windows and use whatever software (hopefully, you can suggest one) to do the cloning process. However, when I disconnect the Ubuntu hard drive and try to start up my computer with only the Windows hard drive connected, I get some kind of black screen, maybe GRUB. I think it's because GRUB was written to the MBR and the Windows bootloader is now gone. I know I can restore the MBR of my Windows hard drive using Boot-Repair and GRUB no longer shows up for me to be able to log into Ubuntu, but I am wondering if I can configure it so that when I disconnect my Ubuntu hard drive, it picks up my Windows XP hard drive and lets me be able to log into my Windows XP as if Ubuntu was never there, and when I plug back in my Ubuntu hard drive, it picks it up and gives me back GRUB. Is that possible?

Try redo it is a ubuntu derivative that makes an image, we use it at work, for XP it carries the license, at least it does for an Enterprise License, info to the new drive as well.  Drive will be the same size as the source, if you image a 160GB to a 250GB drive you will have a 160 GB drive.

---

### Post by wilee-nilee on 2012-05-24
> **Shadius said:**
> It's Windows XP Home Edition so it doesn't have the Recovery Console partition. I've used the Recovery CD to do a Factory Restore before. Now my question is, before cloning the Windows XP Home Edition, should I restore the MBR of that drive so that the MBR is cloned onto the new drive?

I would not if you are using the boot-repair to do it, your choice really, a linux type bootloader called lilo can be used in the new HD, or the boot-repair again to fix this.

I suspect that XP recovery disc will get you to a recovery terminal as well, you just have not had to use it so you are not sure.

I never worry about the mbr as I have a bit of experience here so 
I may do things differently then others.

---

### Post by Shadius on 2012-05-24
> **wilee-nilee said:**
> I would not if you are using the boot-repair to do it, your choice really, a linux type bootloader called lilo can be used in the new HD, or the boot-repair again to fix this.

I suspect that XP recovery disc will get you to a recovery terminal as well, you just have not had to use it so you are not sure.

I never worry about the mbr as I have a bit of experience here so 
I may do things differently then others.

So what you're saying is that I clone the Windows XP Home Edition with the GRUB that's installed in the MBR of the drive, and then I'll be able to use Boot-Repair to bring back the Windows bootloader and make it like I never had Ubuntu, or I can use my Recovery CD and do a Factory Restore on the new Windows XP Home Edition so that I can start fresh, which would be awesome!

---

### Post by wilee-nilee on 2012-05-24
> **Shadius said:**
> So what you're saying is that I clone the Windows XP Home Edition with the GRUB that's installed in the MBR of the drive, and then I'll be able to use Boot-Repair to bring back the Windows bootloader and make it like I never had Ubuntu, or I can use my Recovery CD and do a Factory Restore on the new Windows XP Home Edition so that I can start fresh, which would be awesome!

Yeah, you could do this before hand or after, your choice really, I would be more concerned if the XP is going to be recoverable really, not sure of the damage the HD has had. 

I use clonezilla as suggested but it is a bit more difficult but fairly easy to understand, any gui cloner should work. I suspect that there are cloners that are on bootable cd's like clonzilla I have just not used them.

I would look for a bootable cloner if gparted does not work here.

---

### Post by kc1di on 2012-05-24
you can if you desire if you do follow the instructions on this page to restore the grub mbr after you get windows working.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Shadius on 2012-05-24
Thank you all for you help. I will post back here if I run into any problems while attempting to clone my Windows XP.

---

### Post by Shadius on 2012-05-24
So I made the Parted Magic LiveCD and booted into it with my Windows XP hard drive connected, my Ubuntu hard drive disconnected and my destination hard drive connected. I have no idea what to do from here on though. A little guidance please?

---

### Post by kc1di on 2012-05-24
here's a page that will discribe the proceedure for you.
[http://www.securitybeacon.com/?p=1089]("http://www.securitybeacon.com/?p=1089")

---

### Post by lilmagnus on 2012-05-24
Can you tell us how your drives show in Gparted? Which disk is /dev/sda and which is /dev/sdb? Using that information will determine which drive is selected and when while walking through the linked procedure in the above post.

---

### Post by Shadius on 2012-05-25
It's only picking up one drive. The destination drive. It's not picking up the Windows XP Home Edition Drive. Help please. :confused:

---

### Post by kc1di on 2012-05-25
Check which on is set to master which one is slave or are the both set to cable select?

if both the drives are set as master it may only see one of them.

---

### Post by Shadius on 2012-05-25
> **kc1di said:**
> Check which on is set to master which one is slave or are the both set to cable select?

if both the drives are set as master it may only see one of them.

The Windows XP hard drive is set to Master and the clone hard drive is set to Cable Select, do I need to set the clone drive to Slave?

---

### Post by kc1di on 2012-05-25
The clone should work on cable select but try setting it to slave and see what happens.

did you got to bios when you put in the new drive some bios's require to run a discovery to find new harddrives.

---

### Post by Shadius on 2012-05-25
> **kc1di said:**
> The clone should work on cable select but try setting it to slave and see what happens.

did you got to bios when you put in the new drive some bios's require to run a discovery to find new harddrives.

The clone drive isn't the problem. It's not picking up the Windows XP drive. It only picks up the clone drive.

---

### Post by kc1di on 2012-05-25
set the win xp drive to cableselect also see what happens.

Hope the win xp drive hasn't already bit the dust.

---

### Post by Shadius on 2012-05-25
> **kc1di said:**
> set the win xp drive to cableselect also see what happens.

Hope the win xp drive hasn't already bit the dust.

I thought it died, but then I hooked back up the Ubuntu drive and was able to boot into Windows XP from the GRUB menu. So I don't think it's dead.....yet.

---

### Post by kc1di on 2012-05-25
which position on the cable is the windows xp drive?
if it isn't connected first place it there and then the clone drive. set them both to cable select and try that.

---

### Post by Shadius on 2012-05-25
> **kc1di said:**
> which position on the cable is the windows xp drive?
if it isn't connected first place it there and then the clone drive. set them both to cable select and try that.

The first connector, Drive 0 it says on the cable, and the clone drive is on Drive 1.

---

### Post by Shadius on 2012-05-25
Okay, so I can't get to the Windows XP drive to remove it because I have to unscrew too many things and I don't feel like being frustrated with all that. So I'm assuming that my Windows XP drive is set to Master because that's what the computer originally came with, just that one Windows XP drive. Now, what I did was use Boot-Repair to restore the MBR of the Windows XP drive and I was able to boot into Windows XP like normal and I went into Disk Management and saw that the clone drive is there. The clone drive is formatted to NTFS. So with the Windows XP drive and the clone drive both connected, I rebooted with the Parted Magic LiveCD, went into Partition Editor and it only shows my Windows XP drive, but it shows the drive as unallocated. So confused right now. :confused: What is going on here???

---

### Post by kc1di on 2012-05-25
I'm not quiet sure,  lets do this go to the net and download and burn a copy of gparted. see what it looks like on there.

you can get it here: 
[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php")

---

### Post by Shadius on 2012-05-25
> **kc1di said:**
> I'm not quiet sure,  lets do this go to the net and download and burn a copy of gparted. see what it looks like on there.

you can get it here: 
[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php")

Just to try, I started up G4L and began the cloning process since I know everything is there and working properly. It detected my Windows XP drive (sda) and the clone drive (sdb). Everything seemed to be in order so I have started the cloning process and it is currently at 6%. I will burn GParted as it seems I will need it for later verification. Thanks a lot for your patience with me and walking me through this. I hope the Windows XP gets cloned properly to the new drive. :) Thank you for that guide on how to use G4L also, I would've been lost without it!

---

### Post by Shadius on 2012-05-25
Isn't GParted on the Parted Magic LiveCD already? :confused: It says GParted when I open up Partition Editor. Is it the same thing?

---

### Post by Shadius on 2012-05-25
The Windows XP drive has been successfully cloned!! :) According to Disk Management in Windows XP, I am left with 37.26 GB unallocated space. I want Windows XP to be able to use that space. How do I do this?

---

### Post by kc1di on 2012-05-25
> **Shadius said:**
> Isn't GParted on the Parted Magic LiveCD already? :confused: It says GParted when I open up Partition Editor. Is it the same thing?

yes gparted is there but thought since in wasn't finding the disc. that maybe for some reason it was a bad burn. so thought I would have you try another copy. that's all. Glad it's cloned now. 

Think you can just use the extra space by making a new partition and formatting is as ntfs..or fat32 and windows will find it as another drive. 

Good luck.

---

### Post by Shadius on 2012-05-25
> **kc1di said:**
> yes gparted is there but thought since in wasn't finding the disc. that maybe for some reason it was a bad burn. so thought I would have you try another copy. that's all. Glad it's cloned now. 

Think you can just use the extra space by making a new partition and formatting is as ntfs..or fat32 and windows will find it as another drive. 

Good luck.

I tried using the Recovery CD to restore it to Factory Settings, but nothing happened. Any ideas?

---

### Post by wilee-nilee on 2012-05-25
> **Shadius said:**
> I tried using the Recovery CD to restore it to Factory Settings, but nothing happened. Any ideas?

You have XP on the new HD and need the bootloader in the mbr?

Boot to the recovery terminal and run /fixmbr

---

### Post by Shadius on 2012-05-25
> **wilee-nilee said:**
> You have XP on the new HD and need the bootloader in the mbr?

Boot to the recovery terminal and run /fixmbr

I can log into my Windows XP from the new HDD, let's call it Windows XP Clone, to avoid confusion. I want to make the Windows XP Clone to Factory Settings. I tried using the Recovery CD, but when I choose the Factory Restore option, it flashes the screen for a second and I can see the progress bar of the restore process for a quick second. Normally, it would've stayed on that screen and it would progress, but it's just skipping that screen and telling me to reboot leaving me with nothing changed. 

How do I boot to the recovery terminal to run /fixmbr?

---

### Post by wilee-nilee on 2012-05-25
> **Shadius said:**
> I can log into my Windows XP from the new HDD, let's call it Windows XP Clone, to avoid confusion. I want to make the Windows XP Clone to Factory Settings. I tried using the Recovery CD, but when I choose the Factory Restore option, it flashes the screen for a second and I can see the progress bar of the restore process for a quick second. Normally, it would've stayed on that screen and it would progress, but it's just skipping that screen and telling me to reboot leaving me with nothing changed. 

How do I boot to the recovery terminal to run /fixmbr?

Never used a recovery disc for XP but I would assume it will get you to a terminal if needed here are the instructions for a regular disc. 

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Worse case scenario you can put the lilo bootloader in that HD's mbr from a ubuntu live cd, it will boot straight into XP from that HD then, if all is good.

Make sure the universal repo is on, if not tick it on, and untick the the cd, and run a update before these commands. This is in software sources. 
[FONT=Verdana, sans-serif][SIZE=1]sudo apt-get install lilo [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo lilo -M /dev/sda mbr [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]May show error messages about the rest of lilo missing, ignore, we just want MBR [/SIZE][/FONT] 
  
The XP boot has another repair command /fixboot as well

---

### Post by Shadius on 2012-05-26
> **wilee-nilee said:**
> Never used a recovery disc for XP but I would assume it will get you to a terminal if needed here are the instructions for a regular disc. 

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Worse case scenario you can put the lilo bootloader in that HD's mbr from a ubuntu live cd, it will boot straight into XP from that HD then, if all is good.

Make sure the universal repo is on, if not tick it on, and untick the the cd, and run a update before these commands. This is in software sources. 
[FONT=Verdana, sans-serif][SIZE=1]sudo apt-get install lilo [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo lilo -M /dev/sda mbr [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]May show error messages about the rest of lilo missing, ignore, we just want MBR [/SIZE][/FONT] 
  
The XP boot has another repair command /fixboot as well

I don't think the problem is the MBR needing to be fixed, as I can boot into Windows XP from the new HDD. What I need to do is restore my Windows XP Clone to Factory Settings, starting with a fresh install of Windows XP.

---

### Post by wilee-nilee on 2012-05-26
> **Shadius said:**
> I don't think the problem is the MBR needing to be fixed, as I can boot into Windows XP from the new HDD. What I need to do is restore my Windows XP Clone to Factory Settings, starting with a fresh install of Windows XP.

I see that better now I was not sure on the first factory settings mention, I have used this link to do that, maybe the same method you have.

[http://www.informationweek.com/news/windows/operatingsystems/189400897?pgno=1&queryText=&isPrev=](http://www.informationweek.com/news/windows/operatingsystems/189400897?pgno=1&queryText=&isPrev=)

This always has removed the activation though the couple of times I have tried it, needing the original activation key put in. If it is a OEM you can get the key I think like any other release with the magic jelly bean key finder.

[http://www.magicaljellybean.com/keyfinder/](http://www.magicaljellybean.com/keyfinder/)

I have seen the no format rebuild not work as well, so this is okay since the one you're working on is a clone I assume you still have the original. The one that did not work was a bad virus situation, like really bad.

---

### Post by Shadius on 2012-05-26
> **wilee-nilee said:**
> I see that better now I was not sure on the first factory settings mention, I have used this link to do that, maybe the same method you have.

[http://www.informationweek.com/news/windows/operatingsystems/189400897?pgno=1&queryText=&isPrev=](http://www.informationweek.com/news/windows/operatingsystems/189400897?pgno=1&queryText=&isPrev=)

This always has removed the activation though the couple of times I have tried it, needing the original activation key put in. If it is a OEM you can get the key I think like any other release with the magic jelly bean key finder.

[http://www.magicaljellybean.com/keyfinder/](http://www.magicaljellybean.com/keyfinder/)

I have seen the no format rebuild not work as well, so this is okay since the one you're working on is a clone I assume you still have the original. The one that did not work was a bad virus situation, like really bad.

My Windows XP Home Edition never came with an installation CD. It just came with the Recovery CD from Compaq. I do have my original Windows XP on the original 40 GB HDD (the one that's failing), that's why I needed to do a clone. Not a bad virus situation, just a dying HDD.

---

### Post by kc1di on 2012-05-26
on most newer compaq's the install disc is on the origianl H.D. and you are offered and opportunity to burn it once to CD or DVD. 
At least that's the way it's been on the last three compaq i've had.  After the original boot don't think that offer that option again.  So you may have missed that.  

you may beable to get it from compaq at this link if you really feel you need it.  if windows is working fine I would not bother.
but just in case here is the link:
[http://www.compaq.com/country/cpq_support.html]("http://www.compaq.com/country/cpq_support.html")

Sorry I just gave away my last xp disc. so can't even send one to you.

---

### Post by Shadius on 2012-05-26
> **kc1di said:**
> on most newer compaq's the install disc is on the origianl H.D. and you are offered and opportunity to burn it once to CD or DVD. 
At least that's the way it's been on the last three compaq i've had.  After the original boot don't think that offer that option again.  So you may have missed that.  

you may beable to get it from compaq at this link if you really feel you need it.  if windows is working fine I would not bother.
but just in case here is the link:
[http://www.compaq.com/country/cpq_support.html]("http://www.compaq.com/country/cpq_support.html")

Sorry I just gave away my last xp disc. so can't even send one to you.

Well, the Windows XP Clone works. :) That's good news. However, now I have 37.26 GB unallocated space on the new HDD and I'd like the Windows XP Clone to be able to use that. It is an 80 GB HDD and the C:, partition takes up 32.78 GB NTFS, D:, takes up 3.90 GB FAT32. How do I get the unallocated space to be added onto the 32.78 GB for C:,?

---

### Post by kc1di on 2012-05-26
hi again Shadius, 
I'm sorry that I do not have any windows xp computers here. so can't try this and walk you through it. Been long time since i played much with windows.  but here's a page that may be of help to you.

[http://www.support.com/blog/post/resize-your-hard-drive-partition-without-losing-data]("http://www.support.com/blog/post/resize-your-hard-drive-partition-without-losing-data")

---

### Post by Shadius on 2012-05-26
> **kc1di said:**
> hi again Shadius, 
I'm sorry that I do not have any windows xp computers here. so can't try this and walk you through it. Been long time since i played much with windows.  but here's a page that may be of help to you.

[http://www.support.com/blog/post/resize-your-hard-drive-partition-without-losing-data]("http://www.support.com/blog/post/resize-your-hard-drive-partition-without-losing-data")

I really appreciate the help. So I tried this using your link, but when I right click on the C: partition, it doesn't show any option to Extend Volume.

---

### Post by kc1di on 2012-05-26
ok I know you can do it with gparted ,think it's on the parted magic disk you made here's the link.

[http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

**I would back up any important data first though!**

---

### Post by Shadius on 2012-05-26
> **kc1di said:**
> ok I know you can do it with gparted ,think it's on the parted magic disk you made here's the link.

[http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

**I would back up any important data first though!**

Thanks a bunch. It worked!

Another issue:

Out of curiousity, I used the LILO bootloader by using my Ubuntu LiveCD and running
```
sudo apt-get install lilo
sudo lilo -M /dev/sda
```

I think that was the code, don't remember exactly. How would I reverse the process I did? Basically, uninstalling LILO and returning the Windows bootloader.

---

### Post by wilee-nilee on 2012-05-26
> **Shadius said:**
> Thanks a bunch. It worked!

Another issue:

Out of curiousity, I used the LILO bootloader by using my Ubuntu LiveCD and running
```
sudo apt-get install lilo
sudo lilo -M /dev/sda
```I think that was the code, don't remember exactly. How would I reverse the process I did? Basically, uninstalling LILO and returning the Windows bootloader.

Here is the link earlier in the thread.

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

---

### Post by howefield on 2012-06-17
Thread moved to "*Other OS/Distro Talk*" forum.

---

