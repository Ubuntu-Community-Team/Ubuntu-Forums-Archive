---
title: "Ubuntu Server 7.04 Installs well does not boot"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by jrtorrent on 2007-09-03
I'm really at the bottom of the heap as far as OS knowledge is concerned, so don't get too technical or I'll get LOST!

My hardware: ASUS A8N5X motherboard with an AMD dual core 4400  box, 2 gig memory, ASUS-nvidia video cardd.

I downloaded Ubuntu server 64bit, created a CD and booted to the server install. I chose to use the full 60GB drive for Ubuntu. The installation appeared to go smooth and everything seem Ok till the system asked me to remove the CD to reboot. Ubuntu attempts to boot, tells me the kernel is active but then a message says it cannot recognize hd0
I thought ... maybe the old Vista installation was responsible ... I reformated the hard drive using XP and did a full XP install. Windows XP booted perfectly. Reinstalled Ubuntu chose (again) full Ubuntu installation... got the same result. Doesn't boot.

Suggestions please ..

---

### Post by Yasumoto on 2007-09-03
Are you keeping the partitions for the two operating systems separated?

When Windows installs, it should format the whole hard drive, and then you'll have to first shrink the amount of space it takes up on the disk, and then install Ubuntu on the remaining free space.

If you boot up using a livecd, what does "sudo fdisk -l" give you?

---

### Post by jrtorrent on 2007-09-04
I chose to use the whole system for ubuntu server only. No windows left. So maybe my first question should be: Is it possible to run Ubuntu without any other OS?

---

### Post by hyper_ch on 2007-09-04
is there just 1 harddisk in the system?

---

### Post by BaffledMollusc on 2007-09-04
> **jrtorrent said:**
> I chose to use the whole system for ubuntu server only. No windows left. So maybe my first question should be: Is it possible to run Ubuntu without any other OS?

It's definitely possible to run Ubuntu without any other OS installed - after all, it *is* an OS.

Answering Yasumoto and hyper_ch's questions will help. Since you said you didn't have much technical knowledge let me explain Yasumoto's question more clearly.

The standard desktop CD functions as a Live CD (although, now that I think about it, maybe the server install CD doesn't... out of curiousity, why did you choose the 64-bit server CD instead of the 32 bit desktop CD?). A Live CD means you can boot from the CD and run Ubuntu off the CD without installing it to the hard drive.

If you do this, once Ubuntu is running off the CD, you can choose Applications->Accessories->Terminal to get a command prompt window. In this window type "sudo fdisk -l" without quotes and let us know the output.

Let me stress, though, that's what you do with the desktop version of Ubuntu. For all I know, the server version may not even function like a Live CD.

---

### Post by jrtorrent on 2007-09-04
> **hyper_ch said:**
> is there just 1 harddisk in the system?

Yes, a 60GB Maxtor

---

### Post by conjur3r on 2007-09-04
Is it a sata hard disk?

When do you get the error message?  Does the error have anything like "grub" in it?

---

### Post by jrtorrent on 2007-09-22
1st my deepest apologies. One of my customers opened a whole in their firewall and you can imagine what happened. It was apocalyptic. Slept 2-4 hours a day till we got the whole system back. Anyway that was the reason I did not answer or followed up.

2nd No, it is not SATA but old fashion IDE. The only relevant items in the hardware is that I'm running in an antec box with Asus motherboard and AMD dual core.

Here is a recap of the issue with a transcript of what happens

******
Installed Ubuntu Server 64 on a Fulldisk, that is, the whole disk is dedicated to Ubuntu  (only Ubuntu installed)
- Installation proceed without apparent problems -

Does Not Load - Disk Problem - I reloaded (XP) and worked fine with windows (XP)

Re-Installed Ubuntu Server 64 again using the whole disk. NO WINDOWS

[COLOR="Red"]Here is the sequence that scrolls on the screen:[/COLOR]

 
[68.628889]Buffer I/O Error on device hda, logical block 0
[66.002245]ldm_validate_partition_table(): disk read failure

[COLOR="Red"]while at the bottom of the screen there is this display
[/COLOR]
Kernel Alive
Kernel direct mapping tables up to 140000000 @ 8000-e000

[COLOR="Red"]After a few minutes the following shows up[/COLOR]

Check root = bootarg cat /proc/cmdline ls /dev
or missing modules, devices: cat /proc/modules ls /dev

!ALERT!  /dev/mapper/ubuntuserver-root does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian v1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh/ can't access tty; job control turned off.
(initramfs)

Typing tty<enter> the shell replies:  /dev/console ... so I'm lost!

Ladies and gents I'll appreciate your feedback and direction.

Thanks
(initramfs)

---

### Post by Kilz on 2007-09-22
> **jrtorrent said:**
> 1st my deepest apologies. One of my customers opened a whole in their firewall and you can imagine what happened. It was apocalyptic. Slept 2-4 hours a day till we got the whole system back. Anyway that was the reason I did not answer or followed up.

2nd No, it is not SATA but old fashion IDE. The only relevant items in the hardware is that I'm running in an antec box with Asus motherboard and AMD dual core.

Here is a recap of the issue with a transcript of what happens

******
Installed Ubuntu Server 64 on a Fulldisk, that is, the whole disk is dedicated to Ubuntu  (only Ubuntu installed)
- Installation proceed without apparent problems -

Does Not Load - Disk Problem - I reloaded (XP) and worked fine with windows (XP)

Re-Installed Ubuntu Server 64 again using the whole disk. NO WINDOWS

[COLOR="Red"]Here is the sequence that scrolls on the screen:[/COLOR]

 
[68.628889]Buffer I/O Error on device hda, logical block 0
[66.002245]ldm_validate_partition_table(): disk read failure

[COLOR="Red"]while at the bottom of the screen there is this display
[/COLOR]
Kernel Alive
Kernel direct mapping tables up to 140000000 @ 8000-e000

[COLOR="Red"]After a few minutes the following shows up[/COLOR]

Check root = bootarg cat /proc/cmdline ls /dev
or missing modules, devices: cat /proc/modules ls /dev

!ALERT!  /dev/mapper/ubuntuserver-root does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian v1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh/ can't access tty; job control turned off.
(initramfs)

Typing tty<enter> the shell replies:  /dev/console ... so I'm lost!

Ladies and gents I'll appreciate your feedback and direction.

Thanks
(initramfs)

Did you check disk/media to make sure it was good? There is a disk test on all install cd's.
As stated above the server has no gui. But if you want to get the most out of your hardware you should be running the amd64 version. Since its a server there is no down side.

---

### Post by jrtorrent on 2007-09-23
Yep! I checked the media. As a matter of fact, installing windows works fine, not a  problem so I don't believe I have a hardware issue. Furthermore since that was the first think I thought as it gives a disk error, I did change the drive and re-installed *easy to do so ...* but the results are the same.

Microsoft sent me an upgrade media to migrate from WinXP to Vista. Not only is  cumbersome but it trashed several machines so I finaly made the decision to move to Linux and here I am struggling.

---

### Post by Kilz on 2007-09-23
> **jrtorrent said:**
> Yep! I checked the media. As a matter of fact, installing windows works fine, not a  problem so I don't believe I have a hardware issue. Furthermore since that was the first think I thought as it gives a disk error, I did change the drive and re-installed *easy to do so ...* but the results are the same.

Microsoft sent me an upgrade media to migrate from WinXP to Vista. Not only is  cumbersome but it trashed several machines so I finaly made the decision to move to Linux and here I am struggling.

I think I may not have been clear. Im not saying the media you installed it to, but the CD you installed with. Did you check that the cd was good, or even the iso you burned with the [md5sum?]("http://en.wikipedia.org/wiki/Md5sum") [That should match the hash for the version you installed.]("http://ubuntu.cs.wisc.edu/pub/mirrors/linux/ubuntu/releases/7.04/MD5SUMS").

---

### Post by jrtorrent on 2007-09-23
Oops! yeah! I misunderstood that. The answer though is ... yes I ran a MD5. Later today I'm going to download a fresh copy, retest it and re-install again. Any advise on how to prep the hard drive?

---

### Post by Kilz on 2007-09-23
> **jrtorrent said:**
> Oops! yeah! I misunderstood that. The answer though is ... yes I ran a MD5. Later today I'm going to download a fresh copy, retest it and re-install again. Any advise on how to prep the hard drive?

Well the installer should do that. Are you installing the default file system? If so then just pop in the disk.

---

### Post by jrtorrent on 2007-09-23
Well, that's what I have been doing without any luck. Will I have to install windows and keep windows so Ubuntu works? Doesn't seem able to function without windows which defeats the purpose.

Can't get it!

---

### Post by Kilz on 2007-09-23
> **jrtorrent said:**
> Well, that's what I have been doing without any luck. Will I have to install windows and keep windows so Ubuntu works? Doesn't seem able to function without windows which defeats the purpose.

Can't get it!

I know from experience it works. I have 2 computers in front of me without windows on them(desktop and server). You still have to have grub or some other boot loader installed to start linux, but you dont need windows.

---

### Post by jrtorrent on 2007-09-23
Wait! Are you saying I need to install  grub (or another loader) before I install Ubuntu? Can you clarify ... I must confess eons ago I did some linux and I was using lilo but I assumed that all those manual and independent steps were taken care of in today's bundles.

So ... do I have to install a loader? If so ...which one is recommended?

---

### Post by Kilz on 2007-09-24
> **jrtorrent said:**
> Wait! Are you saying I need to install  grub (or another loader) before I install Ubuntu? Can you clarify ... I must confess eons ago I did some linux and I was using lilo but I assumed that all those manual and independent steps were taken care of in today's bundles.

So ... do I have to install a loader? If so ...which one is recommended?

Grub should install as the last step of the install process the install cd does. If you already have ubuntu installed you can insert the disk and chose rescue a broken install. At some poin it will have an option of installing grub again.

---

### Post by jrtorrent on 2007-09-25
> **Kilz said:**
> Grub should install as the last step of the install process the install cd does. If you already have ubuntu installed you can insert the disk and chose rescue a broken install. At some poin it will have an option of installing grub again.

Kilz, I already tried this option and it did not work for me. During lunch I'm going to try again before I nuke my hardrive and start all over. #@&(*&%# ... that felt good!-)

---

