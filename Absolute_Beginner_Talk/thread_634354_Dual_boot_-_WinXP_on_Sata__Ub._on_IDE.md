---
title: "Dual boot - WinXP on Sata / Ub. on IDE"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by PZJM on 2007-12-07
Hey folks, after many years of XP I am ready to start learning Linux.  I have worked with Unix for the past 8 years but just as a user of some specific applications, mainly ArcInfo.  Anyway, I am having a bear of a time installing Ubuntu so that I can dual boot with Windows XP.  Actually, the install went fine but when my computer rebooted I was not given a choice to boot into Ubuntu.  I went ahead and researched this on numerous forums and this seems to be a common problem with individuals that have a SATA and IDE hard drive.  Windows XP is loaded on my SATA and my IDE contains Ubuntu, however, there seems to be an issue with GRUB.  I have seen some error (bug)  postings regarding this but very few people have found a solid work around.  I don't want to enter my BIOS during boot up to select my OS.  Has anyone heard of a solid fix for this?

Here is my setup:

160 Gig WD SATA (partitioned as: 40gig and 120gig) - This houses my Win XP OS and the second partition contains my video, music, pictures.
80 Gig Seagate IDE drive - I am ready to dedicate this to Linux.

I installed Ubuntu from live cd and followed instructions.  However, there was no location to specify where to boot from.  I am wondering if I should try a clean install again or try and change the boot loader using GRUB.  Do you guys have any suggestions or knowledge if this is a bug?

---

### Post by victorgreen on 2007-12-07
The default grub screen gives you 3 seconds to hit I think its the esc key and get into the grub menu, there it will list all of your possible boot options. If you installed an MS OS BEFORE you installed Ubuntu, it will be the last entry on that grub menu. If you installed Ubuntu and then XP find a dual boot guide and follow its instructions to the LETTER or you could end up with a brick.

---

### Post by PZJM on 2007-12-09
I had Windows OS (XP) installed previous to my install of Ubuntu.  Win XP was installed on my SATA dirve.  Then I added an IDE drive (80 gig) to my IDE1 channel.  When I installed Ubuntu, I partitioned my IDE drive and dedicated 30 gigs to Ubuntu.  After installation I rebooted and was taken immediately to Windows.  I found it interested that Ubuntu did not ask where to install the boot loader.  From my readings the default setting is to install it on the MBR (which would be my sata drive).  I noticed the boot loader was loaded on (hd0, 1).  To my understanding, that would be my IDE drive, partition 1.  Something sounds screwy with this.

I read several other posts with the same issue and then I stumbled onto a bug list.  There was a rather heated debate whether this was a bug or anomoly.  Anyway, I am thinking during the install the boot loader was placed in the wrong location.  I will attempt to load Ubuntu again and hopefully the advanced button will allow me to select the location for the boot loader.

I hope this all makes sense.  Please let me know if my theory is correct.  I am all for ditching Windows, however, there still seems to be issues (especially with sata drives).

---

### Post by CDL-WarChilde on 2007-12-09
I have XP on my SATA and Ubuntu 7.10 on my IDE.  I installed Ubuntu on my IDE drive as the sole hard drive in the system (with the SATA drive disconnected).   After installing Ubuntu I then edited the menu.lst, shutdown machine and then connected my SATA drive.

Edit your menu.lst (lowercase "L").  
```
sudo gedit /boot/grub/menu.lst
```

Here's what mine looks like:

Timeout section, gives me time to choose Ubuntu and is displayed:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		7

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

and the end of the file:
```
## ## End Default Options ##

title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=18101534-6a6d-405b-a29b-e1e5959e0788 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=18101534-6a6d-405b-a29b-e1e5959e0788 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

So, when my PC starts and I don't choose Ubuntu it boots to XP (yeah I know it says Media Center Edition) so my wife can use the machine.

---

### Post by PZJM on 2007-12-10
Hey CDL-WarChilde, thanks for the reply.  That is exactly what I am trying to do.  We still like XP for some of our basic tasks (Video Editing, Pictures, Music).

So, it seems you disconnected your SATA prior to installation of Ubuntu?  Did you also set your boot drive to your IDE drive?  I'm assuming yes.

Let's see if I can follow those steps:

1) Disconnect sata drive
2) Change boot drive to IDE 
3) Load Ubuntu from CD
4) Change menu.lst (as specified)
5) Shut down computer and reconnect sata drive
6) Change boot drive back to sata
7) Start'er back up and all should be good?

I'll give it a try.  Thanks.

---

### Post by Razorback on 2007-12-10
Just curious - are you booting from your IDE first?  I have the same setup - a 160 GB SATA (XP) and a 20 GB IDE (Ubuntu).  I boot the 20 GB first which enables GRUB to start.  You need to follow previous posts to edit your menu.lst file to add XP as a booting option.  This works great for me.

---

### Post by PZJM on 2007-12-10
In my BIO settings I have my SATA drive booting first.  This is were XP sites.  I just recently added my 80 gig IDE drive so I was never using it.  Are you recommending that I switch the drives during start up?  Why?  Should'nt Ubuntu recognize my SATA drive?

Also, what other posts are you talking about?  I have read numerous posts on this subject matter but it seems everyone has a different method.

---

### Post by CDL-WarChilde on 2007-12-10
I'll have to check when I get home, but I *think* I have my IDE drive booting 1st.  After thinking about it, that's where the grub boot loader is sitting so it would have to be the first drive.   hmmm.

---

### Post by Razorback on 2007-12-12
> **PZJM said:**
> In my BIO settings I have my SATA drive booting first.  This is were XP sites.  I just recently added my 80 gig IDE drive so I was never using it.  Are you recommending that I switch the drives during start up?  Why?  Should'nt Ubuntu recognize my SATA drive?

Yes, that is what I am suggesting.  Grub was probably loaded on your IDE drive when you installed ubuntu.  If Grub was loaded on your XP drive, it would start before XP started loading.  This method would be your best bet if you wanted to stay with your current setup.  Plus, each of your OSs would still run independently without interfering with the other, i.e. you decided that XP or unbuntu was what you preferred long term.

---

### Post by PZJM on 2007-12-13
Thanks folks.  I will attempt to give it a try tonight.  I'm gonna place the steps bellow, so if you see something that I'm missing please let me know.  Also, I will attempt this without disabling my sata drive (any comments on this)?

Current set up:

160 gig Sata with XP - primary hd that boots first
- partitioned to a 40 gig and 120 gig

80 gig IDE drive - empty but set up as primary IDE 1 (boots second)

Process to install Ubuntu:

1) Install OS using Live CD
2) Install OS on IDE drive - partitioned to 30 gig
3) Reboot
4) During reboot switch my boot drive to use IDE
5) Enter Grub and use the directions posted above
6) Keep fingers crossed

I hope this sounds correct.  From my understanding, the boot loader will be placed on my partitioned IDE drive as (hd1, 0) since I did not change my start up drive until after I loaded Ubuntu.  I will then have to change this to (hd0, 0) .  Any suggestions on how this is done?

Then my Win XP would be (hd1,0) - sata drive.  This sounds complicated.  I'm wondering if I should just change the boot drive before I install Ubuntu?  Any last minute suggestions?

By the way, thanks for the help and patience.  I can't wait to migrated from Windows.

---

### Post by dstew on 2007-12-13
Usually, it is best to install Ubuntu with your drives in, just as you are going to use them. You can get into really difficult problems if you unplug a drive, install, then plug it back in.

If you want a regular dual-boot system, just leave your drives in and install Ubuntu into the IDE drive as you plan to do. If the SATA drive is the first drive, install grub into it as (hd0). Do not install grub into a partition, such as (hd0,0), or (hd0,1). When you install grub, if you install it to (hd0), it should put its stage 1 into the MBR of the first disk, as numbered by BIOS. It should know where its other stages are (in the /boot/grub directory on the Ubuntu disk). If it does not install correctly, you can manually install grub using the grub command line.

Installing grub depends on how your BIOS enumerates your drives. Sometimes, that is hard to figure out. But, if you only have 2 drives, it has to be one way or the other!

---

### Post by Razorback on 2007-12-13
> **PZJM said:**
> 
Process to install Ubuntu:

1) Install OS using Live CD
2) Install OS on IDE drive - partitioned to 30 gig
3) Reboot
4) During reboot switch my boot drive to use IDE
5) Enter Grub and use the directions posted above
6) Keep fingers crossed

I hope this sounds correct.  From my understanding, the boot loader will be placed on my partitioned IDE drive as (hd1, 0) since I did not change my start up drive until after I loaded Ubuntu.  I will then have to change this to (hd0, 0) .  Any suggestions on how this is done?

Then my Win XP would be (hd1,0) - sata drive.  This sounds complicated.  I'm wondering if I should just change the boot drive before I install Ubuntu?  Any last minute suggestions?

By the way, thanks for the help and patience.  I can't wait to migrated from Windows.

That sounds good.  I am not sure about the drive designations.  I will try to get my box out and check my menu.lst file.  You will need to use gedit to edit the file.  The nice thing about this is that you want to leave windows and this method will put grub on your ubuntu disk.  Good luck. :)

---

### Post by PZJM on 2007-12-14
Well, I wrestled with the install for about 1.5 hrs last night.  Here is what I did and what happened.

1) Restart machine with live CD
2) My SATA drive was the first boot drive.
3) Attempt to install Ubuntu - This is where things started to go screwy.
* During the install I was not allowed to partition my disc as before.  My only partition option was on the SATA.  If I wanted to install Ubuntu I had to use the whole disk (IDE drive) option.
4) Install Ubuntu on IDE hard drive and click advanced tab to make sure where boot loader will be installed.  It said (hd0).
5) After install restart only booted into Windows.
6) Switch boot drives (in bios) and was prompted with several options for booting.
7) Choose Ubuntu and nothing happens.  The only message was "Starting...."  I waited 10 minutes.
8) I then changed my boot drive back to SATA (in bios) and Windows XP launched.

From here I was at a total lose.  I looked for the menu.lst and could not find one.  I then proceeded to format (using data life tools - win xp) my IDE 80 gig disk in hopes of clearing everything out (even thought there was nothing on it).  And I partitioned the drives 20gig FAT 60gig NTFS.

Anyway, I am still without Ubuntu.  My problem is that I don't give up easy.  So I will be attempting this again during the weekend.  Does anyone have some other suggestions?

---

### Post by dstew on 2007-12-14
I think I understand what is happening. When you installed, (hd0) was your IDE drive, so grub went into it. So, when you boot the IDE drive, you get grub, and when you boot the SATA drive, it goes straight to Windows because there is only the Windows boot loader there. Grub was confused by the BIOS enumeration of the disks, so its menu.lst will have the designations reversed. This is a problem with some BIOSes and the grub installation program.

You can probably fix it by editing the grub menu.lst file. You did get the menu when you booted the IDE drive, correct? When the menu comes up, highlight the Ubuntu selection but do not press enter. Press 'e' instead. Then you can change the boot commands, and see if at least you can get Ubuntu started. You can change the root command first. I suspect it will be root (hd0,0). Highlight the line, press 'e' again, change it to root (hd1,0), press enter, then 'b' to boot. If this works, you can make the change permanent by editing the /bbt/grub/menu.lst file. I know you couldn't find it, but it is there somewhere if you get the menu appearing at bootup.

---

### Post by PZJM on 2007-12-14
Thanks for the advice.  I will give it a try tonight.  Hopefully all goes well.

---

### Post by PZJM on 2007-12-14
SO DSTEW, does this mean I will be using my IDE drive as my boot drive and will I have to change this in my bios?  Currently, my sata drive is my boot drive.

---

### Post by dstew on 2007-12-14
It seems that when you change the boot order, the enumeration is changing also. That means the behavior of grub will depend on the boot order. You want to get it working with a particular boot order, and leave it unchanged after that. If you are going to dual boot, you want the system to boot to grub, and choose your operating system from the grub menu. I am trying to help you get to that point.

Since grub is currently successfully installed in your IDE drive, I would suggest making that your boot drive. Then we can try to reconfigure the grub menu.lst so that you can boot either Ubuntu or Windows from the grub menu.

The alternative it to leave the SATA drive as your boot drive, and re-install grub, trying to get it to go in properly. Either way, you will have to do some experimenting to get it right.

---

### Post by Razorback on 2007-12-14
How are things going?

---

### Post by PZJM on 2007-12-14
Just about to start.  I'll check back after I install Ubuntu.

---

### Post by PZJM on 2007-12-15
Well, things did not go so good.  I installed Ubuntu from CD to my IDE drive and the boot loader was pointing at sda (my sata drive).  However, during the install the partitioner did not allow me to partition my IDE drive.  My only option for partitioning was my SATA.  So I used the whole disk - 80 gig IDE drive.

I restarted and changed my boot drive to my IDE drive.  By the way, in my bios I noticed that the boot drives are number differently as channels.  For example, CH 0 is my IDE drive and is set to boot second.  My sata drive is CH 2 and that is my fist boot drive.  Anyway, I made it to the menu and hit edit so i can change the boot commands.  Well, I tried changing it from (hd0,0) to (hd1,) and received and error message: "Can not mount selected partition".  So I change back to (hd0,0) and booted.  All I recieved was a message saying "Starting.....".  Then all goes away.

So, I restarted once again with my boot drive as IDE and I selected Win XP from the menu and all is fine.  Now, my question is regarding the boot loader.  During the install, it mentioned the boot loader was going to be installed on my sda drive.  Wouldn't I change my boot command in grub to point at (sda0, 0)?

Any help at this point would be appreciated.  Also, I can I clean up my IDE drive.  It seems like something is not allowing Ubuntu to partition the drive even though it's clean.  Is there a way to format  the disk with the live CD?

---

### Post by Razorback on 2007-12-15
I take it you are still not able to boot into Ubuntu.

---

### Post by PZJM on 2007-12-15
Yup

---

### Post by Razorback on 2007-12-15
Have you tried any of the safe boot options from the grub menu?

---

### Post by Razorback on 2007-12-15
I need to hit the bed.  You seem like you just about have it working.  I will check tomorrow and try to compare your setup against mine.  It seems like they are almost identical.

---

### Post by PZJM on 2007-12-15
Not yet.  I am still puzzled how come I can not partition my IDE drive using the installer CD.  I may attempt to wipe the drive clean again and install on a formated hard drive.

So how can safe mode help me troubleshoot this?  Also, is it possible the boot loader is on my sata drive (sda)?  Does grub recognize stuff like this or does it mainly use (hd?)

---

### Post by Razorback on 2007-12-15
Since booting up is hanging, it will allow you to get to the command line to modify files, etc.

---

### Post by CDL-WarChilde on 2007-12-15
can you copy/paste your menu.lst for us to look at?

---

### Post by delphi15 on 2007-12-16
This is not help with the problem.  But a real world view of **[B]the problem**[/B].  For years Linux users have worked to make the OS somewhat a standard to complete with Windows etc.

I had Linux SUSE on a box years ago and it installed the dual boot without any intervention on my part.  The SUSE OS was lacking when compared to WIN or Apple so I let it go with the box into land fill.  

I have a V 7.1 of Ubuntu CD disk however after reading all the problems people are having trying to make a dual boot system work I do not think it will ever be installed.  I am a computer user, not a geek.  I read the threads but understand nothing and have no desire understand them.  

This is the "WHY" that Linux has not taken more of Window's market share.  It is still a geek play toy.  

Instead of adding a lot of new programs people should work on making the OS easy to install and programs easy to install.

Just my input.

Thanks,

Harvey Knauss

---

### Post by KimoSaber on 2007-12-16
I'm interested in your problem. I waiting for parts to upgrade my motherboard and cpu. I  plan to install XP or Vista in a SATA drive and Ubuntu on a second IDE drive. I was hoping that by just installing XP or Vista on SATA drive, Ubuntu would recognize the SATA drive.

Presently, I have 2 IDE's drive setup. I have Ubuntu installed as master (jumpers set) and XP as slave (jumpers set).  I used the following guide ([http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)). I believe the Grub loader is installed on the Ubuntu drive. I have to chose Microsoft XP when I bootup or else Ubuntu will load up as default operating system. I chose that setup because it was easier to  reinstall XP or Ubuntu if had to do it later. I didn't want to mess with partitions. I realize your setup is a 1 SATA and 1 IDE drive. I don't understand why it would be a problem, but you could be right PZJM there could be a problem with the Grub loader.

---

### Post by dstew on 2007-12-16
> I made it to the menu and hit edit so i can change the boot commands. Well, I tried changing it from (hd0,0) to (hd1,) and received and error message: "Can not mount selected partition".Which menu command were you editing, the Ubuntu command or the Windows command? Did you really enter (hd1,) or is that a typo?> So, I restarted once again with my boot drive as IDE and I selected Win XP from the menu and all is fine.Did you do this using the grub menu? That is, if you boot the IDE drive, you get a grub menu and the Windows choice works? But not the Ubuntu choice?> During the install, it mentioned the boot loader was going to be installed on my sda drive. Wouldn't I change my boot command in grub to point at (sda0, 0)?I am a bit confused by this. Usually, the installer uses the grub disk names, such as (hd0). It might have shown that (hd0) was the same as your SATA drive, which might have a Linux name like /dev/sda1. In any case, the menu command root statement uses grub names, not Linux names. So, root (hd0,0) would be the first partition of whatever disk grub has decided to name (hd0). In your system, I think there are only two possible grub root statments for booting the operating system: root (hd0,0), or root (hd1,0). I could be wrong, however. It would help if again, with the system you now have in place, that you boot a LiveCD and post the output of the **sudo fdisk -l **command. Once we know the Linux name of the partition in which Ubuntu is installed, we need to mount it and look at /boot/grub/menu.lst also.

---

### Post by PZJM on 2007-12-17
Sorry for the late reply.  My weekend was busy.  Regardless, I sat down last night and tried once again.  However, this time I was able to partition my IDE drive.  The method I used for this was to download the Seagate Utility Wizard for formating their hard drives.  I formated the hard drive as NTFS.  I then booted the computer using the live cd.  From there I was able to partition the drive and install Ubuntu.  The boot loader installed on hd0.  This is were I am getting confused.  I know Grub and Linux has slightly different means of delineating drives.  My IDE drive is connected to IDE 1 - Master.  My DVD/CD drive is connected to IDE 2 - Master.  My Sata drive is connected to my motherboard.  The Sata drive is the first to boot.

So, after installation (once again) Win XP booted without any other options.  I then changed the boot drive in my bios to IDE drive.  I was able to get into the Ubuntu start up screen but that's it.  I tried launching Ubuntu and the message just said "Starting.....".  Then the screen went blank.  I then tried changing the boot from (hd0,0) to (hd0,1).  This did not work.  I am at a complete loss.

Is it time to dig deeper into my bios?

--------------------------------------------------

I'll post my specs tonight......

Thanks for all the suggestions and help.

---

### Post by dstew on 2007-12-17
It seems from the behavior of your system that when you installed, (hd0) was your IDE drive. So, the grub boot loader went into the MBR on that drive, and was configured is such a way as to load its menu from the Ubuntu install on that same drive. But when you booted after that, it went right to WIndows, correct? That means the SATA drive was first in the boot order. The boot order and the BIOS drive enumeration are not the same thing! That is, during the installation, the SATA drive was (hd1) to grub, but was first in the boot order.

When you changed the boot order, the drive enumeration may have changed. The IDE booted grub because the BIOS made it boot. Grub got its menu from the right place, because that step involves a relative disk seek that does not depend on the drive enumeration. But now, the IDE drive is might be (hd1) and the SATA drive might be (hd0). My guess is that the root statements in the menu.lst file are therefore not correct. If the root statement for the Ubuntu system is root (hd0,0) it will try to mount the SATA drive and boot it. But, the SATA drive has a Windows system on it, not an Ubuntu system, so the boot fails.

> I then tried changing the boot from (hd0,0) to (hd0,1)Do you mean you tried to change the **root** command in a boot sequence on the menu.lst? If so, you did it backward. Anyway, when you get to the grub menu, with your IDE drive as the boot drive, look at the WIndows boot commands. I suspect you will see that the root command targets (hd1,0). Change it to root (hd0,0) and see if Windows boots.

These things are really experiments to try to understand what is happening. This is the kind of thing that I would do if I was sitting at your computer. I wish I could just say "This will fix it", but I don't completely understand what is happening. So, we do the experiments. What settings does your BIOS have for disk detection? If it has an auto-detect mode, maybe if you disable it, the enumeration will remain constant even if you change the boot order. Again, I am not sure this is the problem.

---

### Post by Razorback on 2007-12-17
What concerns me is that Ubuntu just goes to Starting when it is selected and does not go any further.  I have the same setup and I can launch Windows if I choose my SATA or I can launch Windows from the Grub menu.  Ubuntu works just fine also.  Are you sure that some else may be going on since Ubuntu will not boot at all.  Maybe there is  a hardware problem or a driver problem.  Just a thought.

---

### Post by PZJM on 2007-12-17
I am going to review some of my settings.  Hold tight and I'll get back with some more details.

By the way, pardon my terminology.  I did use the root command.

---

### Post by PZJM on 2007-12-17
Ok, here is some of my BIOS specs and a very odd situation.  

Specs:
IDE HDD Auto Detect - IDE
IDE CHANNEL 0 Master   [Auto]
Access Mode                   [Auto]

IDE Channel 1 Master - DVD/CD Burner

IDE Channel 2 Master
EXT IDE drive               [Auto]
Access mode               [Auto]

I changed my boot drive to IDE in BIOS and booted into Grub.  I tried reading the screen and it said "Starting Grub 1.5".  Then I was at the selection screen for which OS to boot.  I then hit "e" while highlighting Windows XP.  Then, I changed the root from (hd1,0) to (hd0,0) and Win XP started.  This is real weird because I would expect it not to boot.  Am I correct?

Anyway, I am still trying to figure out how to access the menu.lst file. Can I do this through Grub or will I have to load the Live CD?

---

### Post by Razorback on 2007-12-17
It appears that hd0 is your SATA drive and yes it is OK that it booted to XP.  That is how mine works.  Now, you need to find out what hd? is your Ubuntu drive.  I have always edited my menu.lst in Ubuntu but I would think you could change it with the live CD.  I have not had my linux box out for a while.  I will try to get it started up tomorrow night and post my menu.lst file.

---

### Post by PZJM on 2007-12-18
Here is what I got from doing an fdisk -l while the live cd was installed.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31a0588d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3305    26547381    7  HPFS/NTFS
/dev/hda2            3306        9461    49448070   83  Linux
/dev/hda3            9462        9729     2152710    5  Extended
/dev/hda5            9462        9729     2152678+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1dae1dad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4905    39399381    7  HPFS/NTFS
/dev/sda2            4906       19457   116888940    f  W95 Ext'd (LBA)
/dev/sda5            4906       19457   116888908+   7  HPFS/NTFS

---

### Post by dstew on 2007-12-18
> I changed the root from (hd1,0) to (hd0,0) and Win XP startedNot so weird, really. The problem you are having is due to the auto-detect routines in your BIOS. Sometimes, depending on the current drive configuration, that is, which drives are plugged in where, if the external drive is there or not, or the boot order, the drive enumeration changes from boot-to-boot. Grub, bless its heart, uses the BIOS to name the disks. So, at least to grub, sda can be (hd0) on one boot, and (hd1) on another. The Linux system, however, enumerates the drives itself, so hda will always be hda, never hdb. On the boot that worked for XP, the SATA drive happened to be (hd0), so it booted when you changed the root to (hd0,0).

---

### Post by PZJM on 2007-12-18
Aloha once again.  So it seems that we may be getting to the root of the problem.  I would like to work on this again tonight.  I'm wondering if I should turn off the auto detect?

Would it be easier to just put Ubuntu on a partition of the SATA drive and have both OS's sit on the same drive?  I don't mind dedicating my 80 gig hd to video editing.

---

### Post by dstew on 2007-12-18
It seems that at present you almost have everything working. Grub is working, and you get the menu to appear. You can boot Windows. You already have Ubuntu installed, and all you need to do is get your /boot/grub/menu.lst file straightened out. You don't need to turn auto-detect off as long as you don't change your disks around.

I think it is true that it is simplest to have auto-detect off, then install Ubuntu on the SATA drive, but lets just try to finish the configuration.

When you changed the root command that got Windows to boot, did you make that change permanent by editing the /boot/grub/menu.lst file? Or was it just an edit at the menu screen?

---

### Post by PZJM on 2007-12-18
It was just an edit at the menu screen.  I have yet to figure out how to access the menu.lst file?

---

### Post by dstew on 2007-12-19
To access the menu.lst file, which is on the external drive, you need to mount the partition that contains the file onto your LiveCD file system. Then, you will be able to read and edit the file using the a text editing program that is part of your LiveCD system. To mount a partition, you first need to create a **mount point** in the file system where the partition (really a file system) to be mounted will be attached. A mount point is simply a directory. To mount the Linux partition on your IDE drive onto the Ubuntu LiveCD file system, boot the CD, open a terminal, and issue this command:```
sudo mkdir /media/hda2
```Next issue the command to mount the partition, which from your fdisk output seems to be /dev/hda2```
sudo mount -t ext3 /dev/hda2 /media/hda2
```If successful, you might see the disk icon appear on your desktop, and you can explore it like any other file.

To edit the menu.lst file that is on the Linux hard drive system you can use the text editor nano in the terminal.```
sudo nano /media/hda2/boot/grub/menu.lst
```After you edit the file, you quit by entering control-X (listed in the menu at the bottom of the page as ^X), enter Y to save changes, then return to quit.

Since you are using the LiveCD system, when you quit, the mount point will disappear, and you will need to mount the hda2 partition again if you want to edit the menu.lst file again.

---

### Post by PZJM on 2007-12-19
Thanks for the info.  Last night I spent a good deal of time reading the GRUB documentation.  I will give it a try tonight...

---

### Post by PZJM on 2007-12-20
I am super busy at the moment and will not have time to address this issue till after Christmas.  However, I am one not to give up.  I was also thinking of formating my hard drives and starting from scratch.  This way I can load both XP and Ubuntu on my SATA drive and then use my IDE for video editing.

If I do the installation properly (most likely w/out ide drive installed) things will work just fine.  I will keep posting my results.  Once again, thanks for all the help.

"I'LL BE BACK"......

---

