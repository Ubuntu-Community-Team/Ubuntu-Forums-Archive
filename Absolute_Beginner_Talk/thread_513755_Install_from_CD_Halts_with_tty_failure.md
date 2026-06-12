---
title: "Install from CD Halts with tty failure?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by ronc55 on 2007-07-30
The initial installation halts with the following message:  /bin/sh:  can't access tty: job control turned off
Then returns the prompt to (initramfs)  I ran the winMd5Sum.exe program and says I have a valid file. 

The pc is an IBM R30 Laptop with a 2wire wireless pcmcia card which appears turned off at this point.  I get the initial startup screen just fine, am able to select the "Start or Install" line and after a few moments, this appears.  Do I need to enter something here to move it on?

---

### Post by Spr0k3t on 2007-07-31
I found this when doing a search, it seems it's related.

[http://ubuntuforums.org/showthread.php?t=279884](http://ubuntuforums.org/showthread.php?t=279884)

---

### Post by ronc55 on 2007-08-02
:)After working on this for 2 days I must confess disappointment.  I am still at square one.  I have read and read, download numerous programs, ran Gparted LiveCD - changed the partitions, deleted partitions, hammered the mbr, replaced it with whatever it is that Acronis provides.  I downloaded the alternative Install - it fails.  This is an IBM Laptop R30 with a 30 gig harddrive.  I had previously installed Red Hat Linux in 2001 and partitioned it so that it was dual boot.  I did it with Acronis and found after that that there were no drivers available for my wireless card so abandoned the effort although I did have a running Red Hat.  I'm a big fan of the idea behind Linux, I would love to rejoin the fun.

After the failure to install or run the Live install CD for Ubuntu, I deleted the dual boot thinking it would somehow make a different.  I no longer can find my Acronis disk so can't go back on that decision.  It does boot to Windows from power on.  Using Gparted LiveCD I have deleted all the Linux partitions and my Fdisk -l looks like this

/dev/hda1  HPFS/NTFS
/dev/hda2  Extended - Note I tried to resize this as I suspect it to be RH, it won't.  Seems protected as I can only increase the size.
/dev/hda5  HPFS/NTFS
/dev/hda6  Hidden Fat 16 <32M

Now the questions:

Other than reformatting the entire drive to NTFS any suggestions.  If I reformat which I'm willing to do as this is a secondary machine and I have the Windows XP Pro CD and License I could re-install at least Windows and sell the darn thing.  All the important docs and pics are backed up long ago.  If I reformat the entire drive will the Ubuntu LiveCD run, reformat and configure the partitions or do I need to do that prior to running it?

---

### Post by ronc55 on 2007-08-02
While I was waiting I thought I would try one more time with the alternative cd ubuntu-7.04-alternate-i386.iso.  I have run the winMd5Sum against it.  This is the 3rd download of this file and each fails the test.  Is there a problem with this file?  I have tried this process both against the file as downloaded and again after it was burned to a cd using InfaRecorder.  In both situations the files fail the check.  I'm feeling snake bit on this guys.  Again - please help!

---

### Post by davidjmayo on 2007-08-03
Regarding the iso download. 3 fails is very unusual. I would try from a torrent as this will check each piece for integrity after it's downloaded. A server download is a big file and it only takes one little bad piece to corrupt the file hence MD5 fails
You can get the torrent from the bottom of this page
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

If you need a lightweight win torrent client I would recommend utorrent
[http://utorrent.com/](http://utorrent.com/)

As to partitioning it is hard to advise as you don't give the partition sizes. This guide may help
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

If I were deleting your partitions and knew what they were I would use GParted Live CD as you did. I'd start by deleting hda6 then hda5 then the extended (and the win partition if you want to). Also I'd do this one operation at a time so:
delete partition hda6==>apply (this is only an example as I don't know what that hidden partition is)
then do the next operation delete hda5==> apply
etc.

The free space I would leave unformatted and let ubuntu do it during the install
During the install I would choose "Guided Partition" and the option to use the "Free Space"

---

### Post by ronc55 on 2007-08-03
Thanks for the pointers.  One more observation that seems to be consistent each time I attempt an install.  There is a log file named Casper.log.  I read the file and it is complaining as follows:

"mount: Mounting /dev/hda1 on /cdrom failed:  No such device: error 0."

This continues 16 times and then finally writes: "unable to find a medium containing a live file system" and then ends.  

That seems to me that I still have a problem on my MBR as a possiblility?  I think I need to fix that first before moving on?  And if so do you have a recommendation of a tool that could do that and be recognized by the installation process?  Windows continues at this time to still boot just fine.

---

### Post by ronc55 on 2007-08-03
Well I have deleted all partitions - I now have 27+ gigs of unallocated space and the installation still fails with the same message.  The Casper.log file continues to report the same message as above. This computer is empty of all operating systems.  The snake has bit me.  Not sure where to go from here.  The alternative cd continues (another 3 trys) to fail the md5 test. I tried uTorrent and it does not list my router for port forwarding.   Any useful thoughts or do I put the machine up for sale as you guys are probably tired of hearing from me!

---

### Post by davidjmayo on 2007-08-03
> "mount: Mounting /dev/hda1 on /cdrom failed: No such device: error 0."

I don't understand why a HDD is trying to mount as a CD-ROM. Never saw this before
Anything in BIOS to try to do this? (unlikely)
I'm out of ideas on all fronts (I don't even have a router so can't advise what to do next)

This will bump your post FWIW and wait a while to see if someone else can help

My last idea is to click on "report" for your post and request it to be moved to the "hardware and laptops" forum

> 
Any useful thoughts or do I put the machine up for sale as you guys are probably tired of hearing from me!

In this forum nobody will get tired of you. They will help to get a solution if they can

---

### Post by ronc55 on 2007-08-03
There does appear in the bad Alternative install a reference at the very beginning to a conflict with irq 15. It seems to be the cdrom but calls a process to resolve it and moves on untill the process completely fails.  Does seem odd that error message is in the Casper.log as it obviously is reading the cdrom.  I appreciate you comments.  

The complete deletion of all the partitions has apparently taken out the MBR so I will try to reinstall Windows XP and see if that puts that back again.  Certainly an exercise of patience -OK, I am editing this to indicate I have a clean Windows XP Pro install and fixed MBR & Boot table.  I tried the original Ubuntu install again and get the same tty failure.  I'm going to check and will advise on the IRQ 15 issue in windows.  There are no conflicts showing in the Device Manager so I think that is a none issue at this point.

---

### Post by ronc55 on 2007-08-04
New Day - I seached this forum and found a reference to something that seemed to help others.  At the boot splash, select F6 backspace over the "quiet splash --" and see quote below:


Originally Posted by Aldebran View Post
"I think I have some solutions :"

The first solution is (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'all_generic_ide'

The second solution is more complex but i think it's better (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'break=top'
A shell will appear, so :
- Write 'modprobe piix' (after you will see some text)
- Finally, write 'exit'

Ok I tried a bit of a modification of the above and using the 1st solution got well into the install code.  Then it failed with the standard tty error message

I entered 'modprobe piix' and exited - got the following:

cp:  unable to open '/root/var/log/':  No such file or directory 
Done.
Begin: Running /scripts/init-bottom ...
mount: Mounting /root/dev on /dev/.static/dev failed:  No such file or directory
Done.
Mount: Mounting /sys on /root/sys failed:  No such file or directory
mount: Mounting /proc on /root/proc failed:  No such file or directory
Target filesystem doesn't have /sbin/init

Then the standard /bin/sh: can't access tty; job control turned off
 I'm sitting at the (initramfs) prompt.

So close but yet I'm still missing something - help please - thanks 
Does this help anyone to understand what is happening?  I feel like I'm almost there, just need one? more little thing!

---

### Post by ronc55 on 2007-08-05
Okay it is late on the same day and after reading another thread on this same subject I became very discouraged that I was ever going to solve this.  So I went out and downloaded a different distribution with a different kernel.  I loaded in my CD drawer and booted.  It too failed with the same message so I erased the splash comment after selecting 
F6.  This outputs the process of installation to the screen so that you can sorta follow along.  Just before it aborted with the tty failure it was complaining of an irq conflict and made the recommentdation to use irqpoll.  Being a newbie I didn't know exactly where to put this but I eleminated the quiet splash and put it there after pressing F6.  The distribution took me all the way to the screen where it was running off the cd.  I had a desktop and everything else was available.

Shutdown and put in the Ubunto install disk and tried the same thing eleminating the quiet splash and using irqpoll in its place.  Ubuntu ran all the way to the desktop.  Thought you would like to know.  A couple of thoughts, this miight be unique to my machine (irq conflicts) so it may not work on yours.

I installed Ubunto - and it failed with the tty error again.  I rebooted in the Rescue Mode and entered irqpoll and got to a terminal.  I exited and went to the desktop.  I then edited the /boot/grub/menu.lst file to add irqpoll on the quiet splash line - just typed it after that entry.  It has been working since then.  I hope this helps, Ubuntu is worth the effort, I like it.  Not bad for a 63 year old Grumpy Grampa!

Ron

---

### Post by todak on 2007-08-06
I have the same occurrence when I try to install anything with a kernel newer than 2.6.20.xx. It happens with debian, sidux and any other distro using a 2.6.21.xx kernel or newer. Even on my sidux install, when I just attempt to upgrade to a newer kernel, the upgrade and install of the kernel goes fine, but it will not boot. So I remove the offending kernel and use 2.6.20.xx and everything runs just great! It appears to be a hardware configuration related bug in the newer kernels.

---

### Post by ihristov on 2007-08-11
I get the same error on the IBM R30 laptop. The problems seems to be some bug in the BIOS which apparently makes IRQ 15 disappear and from there the CD-ROM stops working and it can't boot further.

I have seen the same problem with other versions of the kernel (older Ubuntu releases).

The workaround is to add the option "irqpoll" at boot time. In other words when the CD boots on the initial screen press F6. Press back space a couple of times to remove the "--" and type irqpoll then press Enter. You should then be able to boot in the live CD.

Not sure if this affects performance.

Not sure if after install will have to supply the "irqpoll" parameter again.

Update: I just finished the installation. It requires to have "irqpoll" in the startup parameters. Otherwise it takes forever to boot and sound does not work.
To add it permanently edit /boot/grub/menu.lst and add the option to the kernel entry there.

Update 2: After upgrading the kernel sound stopped working, so I removed the new kernel and "pinned" the linux-image and related packages. In Synaptic this is done by selecting the package(s) and then choosing "Lock version" from the "Package" menu.

I "pinned" the following packages. I think this is sufficient.
{{{
linux-generic
linux-headers-2.6.20-15
linux-headers-2.6.20-15-generic
linux-headers-generic
linux-image-2.6.20-15-generic
linux-image-generic
linux-restricted-modules-2.6.20-15-generic
linux-restricted-modules-common
linux-restricted-modules-generic
}}}

The kernel package that works fine with the sound is 2.6.20-15.27 - the one that came with the installation CD
The one that the sound did not work is the current one as of this writing - 2.6.20.5-16.29

---

