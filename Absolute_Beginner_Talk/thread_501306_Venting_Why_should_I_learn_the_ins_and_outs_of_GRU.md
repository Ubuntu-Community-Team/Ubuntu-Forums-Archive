---
title: "Venting: Why should I learn the ins and outs of GRUB?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by MrMercutio on 2007-07-15
Apologies for this vent but I just *have to* let off steam after a new foray into the Linux world sends me packing back to the Windows world, bruised and disappointed...

Once every six months I get the notion that I want to fill my unused partition Linus with some bootable content &#8211; Linux. But to this day my attempts to join the Linux revolution has been thwarted.

My demands are simple: give me a good Linux that I can learn, but don&#8217;t expect me to abandon Windows until I have a healthy grasp of Linux. Don&#8217;t expect me to start compiling the core, and hooking up additions to the core before I can even make heads or tails of how the OS names its harddisks!

Point and click, that&#8217;s what I want at this stage. Later, I would be able to both compile the core, and then dabble with the code of it. Eventually I could maybe write a great add on or two &#8211; but I still need to learn Linux. So, point and click right now.

**Many Linux distros promise pointing and clicking**, as does both Ubuntu and Kubuntu. Insert disk, boot, point and click, and voila &#8211; Linux is on the box&#8230; Things never turn out that way, at least not for me. I do not know if there&#8217;s a great hand in the sky that wants to keep me on the MS side of the computing world for ever. Something *always* go wrong when I try to install Linux. Either it's a driver that's acting up that forces me to wipe Linux from the box, or it's like now -- the boot.

Linus is always wiped again, and soon I&#8217;ll make it into a NTFS-disk rather than an ext 3&#8230; And this time both Ubuntu and Kubuntu was wiped from the disk. I have no need for an OS that I can&#8217;t boot into. Don&#8217;t get me wrong, every file was copied from the ISO to Linus. Every I was dotted, and every T was crossed in the installation.

Cheerio, good job, a quick installation and all that. But still no use, since I wasn&#8217;t able to boot either Ubuntu or Kubuntu from anything else than the Live CD. To be specific, I have no intention of pouring hours of frustration into learning the ins and out of GRUB to get it to work.

That&#8217;s not my job to begin with. My job is to install Ubuntu or Kubuntu and then ogle at how nice it/they are. At this stage. My job is not to, at this point, to want Linux so bad that I'm willing to pour a huge amount of sweat into the problem. My job is to learn Linux, and the ubuntu/kubuntu development team's job is still to sell the system to me by the quality of its design and the ease of its use.

**Yes, it is a matter of GRUB** the pernicious boot loader that should allow me to boot into Linux. I&#8217;ve read the questions here on the forum about the problems with GRUB to try to find the answer to my problems. They all speak of HD0, HDD and so on. Since I can&#8217;t boot Linux with anything but the live CD, I can&#8217;t even get any answer from fdisk &#8211;lu. Fdisk doesn&#8217;t tell me anything about the file system.

I&#8217;m supposed to be able to use the TAB character in the KDESU/SUDO GRUB in the console for code completion, but when I press tab &#8211; all I get is a movement of the cursor x number of blank spaces to the right, and error messages like 'the device doesn't exist'.

Given that I&#8217;m running Ubuntu/Kubuntu from a LIVE-CD I don&#8217;t know whether an install of LILO will matter a whit, or if it would just be temporarily installed for the pseudo file system of the current CD-boot. I&#8217;m not even going to try that, actually.

**Don&#8217;t get this venting wrong**, I still want to learn Linux. As a computer git who likes the slackware live distros I use, I still want to learn Linux just for rounding out my computer knowledge that is very Windows-based right now.

However, I don&#8217;t *have to *learn Linux, and if the developers of the Linux platsforms aren&#8217;t going to make it easy for me to get a toe into the Linux world by supplying a good boot loader that I don&#8217;t have to tear my hair out over, I&#8217;m not likely to ever learn it. Since Microsoft with Vista launched that new Windows boot loader that doesn't show anything else than MS-OS:es, that task does fall to the Linux development community.

And, I don&#8217;t really see why the new users should learn the ins and outs of setting up a booter, given that the linux distro developers doesn't seem to want to solve the booting problems with GRUB. I could, of course, learn all that given enough time and effort, but I don't see the point if the linux development community isn't going to make the transition from Windows the Linux as easy as possible for users that aren't computer gits like me.

[Edited for spelling and grammar]

---

### Post by UFF on 2007-07-15
Hmm you have had similar problems to what I have had in the past with Linux. My problems were mostly driver related but I am really happy with Ubuntu because my install was mostly point and click!

I had a small issue with my screen-res and a few other little hiccups, but with the vast amount of posts on here I was able to fix it all up within about 15 minutes.


But I can definetely relate to your situation. Unfortunetly I am just as new at this so I can't offer you much except the best of luck :)

---

### Post by MrMercutio on 2007-07-15
Thanks, yes it's frustrating. For the boot thingie problem, the best way would of course be to put a GUI on top of GRUB that presented the user with the information needed to use it. Or use another boot loader that was better. LILO is probably not better than GRUB, since it is older and less flexible as to the OS:es it can recognize. But LILO is definitely easier to use...

---

### Post by splintercellguy on 2007-07-15
Okay, so your problem is that you're trying to dual-boot? What difficulty are you encountering? Forgive me if I've misinterpreted.

---

### Post by sonofusion82 on 2007-07-15
hmm.. i know the fustration with it just doesn't work. 
but i am always more optimistic that since i am getting it for free, putting a little extra time and effort to learn and fix the problem doesm't hurt compared to paying a whole lot of money for a piece of software but still not perfect.
i agree that the initial learning curve for linux is a little steeper than Windows, and quite often you will need to understand how the software works to modify or fix a config files.
but so far, i have never had any serious problems with grub or lilo.

---

### Post by MrMercutio on 2007-07-15
Actually, I want to triple boot: Windows XP that I use for jobs I need a dependable OS for, and that I can play games on; Windows Vista; and finally Ubuntu or Kubuntu.

[IMG]http://bloggenbent.dagenspolitik.se/images/myharddisks.jpg[/IMG]

Windows Vista sees only the XP, of course, as you know. Now I want to install either ubuntu or kubuntu. I'm leaning toward kubuntu because I'm more used to KDE from the Backtrack Live CD distro I'm using. Now, as has happened according to many posts in this forum, the installation goes fine but when you reboot the Vista bootloader comes up.

You then go into the Live CD Ubuntu/Kubuntu to try to fix this, and in at least my case I can't make heads or tails about what to do. GRUB just doesn't work for me. FDISK doesn't tell me what I need to know, ie what the hard disks are called. /dev/ just talks about the UUID of each hard disk, but my grub refuses to recognise any UUID. It also refuses to recognize HD0, HDD1, and so on. Since FDISK doesn't tell me what my hard disks are called I have to guess (or try to use GRUB:s code completion TAB which just gives me X amount of blankspaces to the right when I use it.

Therefore, my complaint. I'm sure there's a solution for this. But that wasn't the point of my vent. The point of my vent was to vent the fact that you need to go into this forensic operation in the first place with something that should be a breeze.

---

### Post by splintercellguy on 2007-07-15
Well, when you install Ubuntu, shouldn't the installed GRUB bootloader automatically detect the Windows?

---

### Post by MrMercutio on 2007-07-15
> **splintercellguy said:**
> Well, when you install Ubuntu, shouldn't the installed GRUB bootloader automatically detect the Windows?

It doesn't. I don't think GRUB is installed at all when I install Ubuntu.

I've loaded the Live CD now, and I'm writing this from it. Here's the information I do get:

**FDISK -lu**:

ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/**sda**: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   389479859   194739898+   7  HPFS/NTFS
/dev/sda2       389479860   625137344   117828742+   f  W95 Ext'd (LBA)
/dev/sda5       389592378   515429459    62918541    7  HPFS/NTFS
/dev/sda6       515429523   625137344    54853911    7  HPFS/NTFS

Disk /dev/**hdd:** 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders, total 40088160 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *          63    38331089    19165513+  83  Linux
/dev/hdd2        38331090    40082174      875542+   5  Extended
/dev/hdd5        38331153    40082174      875511   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

HDD is Linus then, the Linux-partition. But GRUB recognizes neither HDD nor SDA. It does not recognise HDD1-5, SDD1-6, etc. I don't know where to find out the HDX  - where X is the number that is supposed to be used. Trying to guess that SDA is HD0 and HDD is HD1 didn't work either.

**MOUNT** (as in: sudo mount)

ubuntu@ubuntu:~$ sudo mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdd1 on /media/disk type ext3 (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/disk-1 type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sda6 on /media/disk-2 type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sda5 on /media/disk-3 type ntfs (rw,nosuid,nodev,umask=222,utf8)
ubuntu@ubuntu:~$ 

**GRUB**: (as in the command line : sudo grub)

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions. [B] Anywhere else TAB lists the possible
         completions of a device/filename[/B]. ]
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd0,0)
setup (hd0,0)

Error 17: Cannot mount selected partition

grub> root (hd1,0)
root (hd1,0)
grub> setup (hd0,0)
setup (hd0,0)

Error 17: Cannot mount selected partition

And so on, and so on...

---

### Post by Vague on 2007-07-15
I'm going to put in a guess here that may or may not be right.  Your "Linus" partition is on a separate hard disk than your Windows partitions, right?  And your problem is that you don't see GRUB at all when you boot after installing Ubuntu?  (I might be misunderstanding you, but that's what I got out of what you said.)  Is your BIOS set to boot to the disk that has GRUB on it, or are you booting straight to your Windows disk?

> And, I don&#8217;t really see why the new users should learn the ins and outs of setting up a booter, given that the linux distro developers doesn't seem to want to solve the booting problems with GRUB.

I hate to get sidetracked by comments like this, but it isn't as if GRUB is *supposed* to have to be tweaked on a standard Ubuntu install.

---

### Post by MrMercutio on 2007-07-15
Yes, Linus is an older IDE harddisk that I installed in my new machine because back when it used to have lots of important data. After I moved the data to a more durable media, I never removed it again. And since I wanted to install Linux on it (20 GB should be ample space and then some for Linux). 

And yes, I'm presented with the Windows Vista boot loader when I reboot, giving me a choice between XP and Vista, and nothing more.

---

### Post by Vague on 2007-07-15
> **MrMercutio said:**
> (20 GB should be ample space and then some for Linux). 

It certainly is.

> And yes, I'm presented with the Windows Vista boot loader when I reboot, giving me a choice between XP and Vista, and nothing more.

This leads me to believe I might be on the right track.  If you're booting to your Windows disk before the disk GRUB is installed on, you're never going to see GRUB.  I'd definitely check in your BIOS to see if your SATA disk is booting before your IDE disk.

---

### Post by caravel on 2007-07-15
The problem is that GRUB is installed on the first HDD which looks like a Deskstar 34GXP 20.5GB PATA drive?

The second HDD with Vista and XP on it seems to be either:

1) A SCSI or SATA/SATA II drive connected to a SCSI or SATA/SATA II controller.

2) A PATA drive connected to a PCI RAID controller card.

Basically Ubuntu is not detecting the second drive connected to the controller at all, and this is why your windows OSes are invisible to Ubuntu.  I believe that in order for this to work you will need to compile the driver for the (assumed) RAID controller into the kernel.  This is the kind of thing that you were complaining about in your first post though - being asked to run before you can walk - but I'm not sure if there's any other way out of it.

---

### Post by MrMercutio on 2007-07-15
> **Vague said:**
> This leads me to believe I might be on the right track.  If you're booting to your Windows disk before the disk GRUB is installed on, you're never going to see GRUB.  I'd definitely check in your BIOS to see if your SATA disk is booting before your IDE disk.

I was under the impression that the point of GRUB was to overwrite the master boot record on the SATA disk?

---

### Post by Tomosaur on 2007-07-15
> **MrMercutio said:**
> I was under the impression that the point of GRUB was to overwrite the master boot record on the SATA disk?

The installer is ignorant about such things, I believe. It assumes that whatever hard disk you're installing Ubuntu on is the hard disk you'll be booting from, since that tends to be the most common configuration. I believe the problem is that Grub is installed on your /dev/hdd, while Windows is installed on /dev/sda. The solution to your problem may be as simple as swapping the boot order of your disks, so that the disk with Linux installed boots first, and thus Grub gets a chance to load.

However, I do a fair amount of messing about after I install a new version of Ubuntu, and I can't quite remember whether the default installation of Ubuntu has the support for such a configuration, although if it doesn't, you can certainly install such support manually.

My advice is to simply switch the boot order around and hope for the best. If that doesn't work, you **may** be able to get Ubuntu to show up in your Windows boot loader. I have Ubuntu showing in my WinXP bootloader, but I rarely see it since I have Grub installed aswell, and basically just use that. Unfortunately I can't remember exactly how I went about setting that up, so you'll just have to search the web I'm afraid.

Another possible solution, if the boot-order switching doesn't work, is to put another bootloader such as [GAG ](http://gag.sourceforge.net/) onto a floppy drive, and hopefully that will detect all your available operating systems and allow you to boot into Ubuntu.

It's a bit of a sticky situation, but I'm sure you'll be able to work it out. I hope you get it all working, and hope you have a great time using Ubuntu :)

---

### Post by MrMercutio on 2007-07-15
I'm reinstalling Ubuntu now as I write this. I've changed the BIOS boot order. We'll see in a while, I guess...

If it doesn't work, I guess I'll just wipe the HD and let it sit for another six months until I'm lured back by another distro that promises point and click Linux...

I've never had trouble with Backtrack linux, btw, but that distro is limited to just network work, and there's therefore no point in installing it on a hard disk.

---

### Post by MrMercutio on 2007-07-15
Thanks everyone for your kind help to this frustrated user. Finally, Linux is actually installed on my system. Okay, so it is Kubuntu, rather than Ubuntu -- but I'm just a lot more used to KDE than Gnome, and I have had enough of the learning curve for today.

As it was pointed out, it was the boot order that was the culprit, and perhaps not Ubuntu/Kubuntu itself. If anyone think I've been grossly unfair to their favorite OS by my initial gripe, I hereby apologize. Still, it is still my conviction that these distros should be able to scan for multiple physical hard disks, and act accordingly.

But thank you all! I'm now off to learn more about this new OS of mine. I'm not completely un-Linuxed, of course. I've done a bit of networking jobs with the Backtrack distro, which is based on slackware, so I'll try to repay the help I got if there's any question I can answer about that. 

:)

---

### Post by regomodo on 2007-07-15
> **MrMercutio said:**
> I'm reinstalling Ubuntu now as I write this. I've changed the BIOS boot order.

yeah. i was just  going to point that out.

when i couldn't get grub to work properly the bios setting was my form of os selector for a while

---

### Post by Vague on 2007-07-15
Glad to see you were able to get it up and running.

> **MrMercutio said:**
> As it was pointed out, it was the boot order that was the culprit, and perhaps not Ubuntu/Kubuntu itself. If anyone think I've been grossly unfair to their favorite OS by my initial gripe, I hereby apologize. Still, it is still my conviction that these distros should be able to scan for multiple physical hard disks, and act accordingly.

I don't think you've been unfair, just frustrated, really.  To answer your last sentence, I'm really not sure why the Live CD doesn't allow you to choose where GRUB is installed, like the alternate install CD does.

---

