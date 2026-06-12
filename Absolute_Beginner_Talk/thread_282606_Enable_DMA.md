---
title: "Enable DMA"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-23
How do I enable DMA? My DVD playback is very choppy. I tried using the following:

[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

But when I enter:

   sudo hdparm /dev/hdc

I get:

/dev/hdc: No such file or directory

Thus, I am not sure what to do to enable DMA or even check if I have DMA. Thanks!

---

### Post by amitroy5 on 2006-10-23
I have a Dell Inspiron E1405 with the DVD-ROM /  CD-RW combo drive.

---

### Post by jorn on 2006-10-23
To find the correct hd for your cd-drive, look into:
> gedit /etc/fstab

---

### Post by Perfect Storm on 2006-10-23
The choppy-ness can also be that you need dvdcss2 lib installed.

---

### Post by amitroy5 on 2006-10-23
I have dvdcss2 installed.

Also, I entered gedit /etc/fstab and got the following output in the text:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I am not sure which is correct, or what to do. Thanks!

---

### Post by jorn on 2006-10-23
That means your cd-drive is mounted on /dev/scd0.
You might use that instead of /dev/hdc in the first command in your mentioned link.
> #

See the what the settings are on /dev/hdc

    *

         sudo hdparm /dev/hdc
         



---

### Post by amitroy5 on 2006-10-23
Jorn, thank you for the idea, however, I am still having problems:

```

amitroy5@Amit:~$ sudo hdparm /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
amitroy5@Amit:~$    sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
amitroy5@Amit:~$

```

Not sure what is causing this. :(

---

### Post by amitroy5 on 2006-10-23
bump - still need an answer. Thanks!

---

### Post by Perfect Storm on 2006-10-23
You might check this troubleshooting: [http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

### Post by amitroy5 on 2006-10-23
I tried the troubelshooting tips, however, no matter what I type for DRM, I still get the same problems. Is it even possible that DMA cannot even be enabled on my computer?

I really want to enable DMA on my compter so I can watch DVD movies. I don't want to go back to Windows XP for this. Thanks!

---

### Post by Lord Illidan on 2006-10-23
You have a scsi disk or a SATA disk? hdparm is meant for IDE drives.

Could it be your video performance? Can you run 3D well on your system?

---

### Post by amitroy5 on 2006-10-23
I am not sure if I have SCSI or SATA. How do I check? Also, if I do have one of these, does it mean it is impossible for mey to properly watch DVDs?

---

### Post by mcglnx on 2006-10-23
Hi,

I got exaclty the same issue - it seems to be something recurrent. 
I'd love to be find the solution!

Is there a way to prevent Ubuntu from mapping the hard drive as a SCSI one? It seems this is the problem?
or is there any way to configure a SCI drive with a tool like hdparm?

Thanks,
M.

---

### Post by amitroy5 on 2006-10-23
I just realized that my Ubuntu sees my DVD-ROM CD-RW Combo is SCSI. How do I enable DRM to avoid the choppy playback, if it is possible?

What if I get a second DVD-ROM drive that is external via USB? Would I be able to watch movies though that?

---

### Post by mcglnx on 2006-10-23
Yes, you can try.
It seems the bug was reported long time ago by Redhat team: [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=163418](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=163418) 
The latest Kernel is 2.6.18,. I think we need to re-compile a custom kernel to get rid of this... 

Let's try!

---

### Post by amitroy5 on 2006-10-23
But I am not sure if it is really SCSI or if Linux just sees it as it. I just bought this Ispiron E1405 from Dell.com, and I don't think they would make SCSI CD-RW/DVD-ROM combo drives.

---

### Post by amitroy5 on 2006-10-23
I was wondering if it is possible that this issue will be fixed in the new Ubuntu?

---

### Post by jamesrl on 2006-10-24
Hi,
I have a E1505 that i've had for 6 months or so that has the cd-rom as 
/dev/sdc.  I can play and burn DVDs fine on my machine without doing anything special to enable DMA.  

The s in sdc means you have serial (SCSI/SATA) drives, and according to another thread with input from hdparm writer (see link below), you don't need to enable DMA, it is enabled by default in the kernel.  

[http://www.ubuntuforums.org/showthread.php?t=207780&highlight=scsi+dma+hdparm]("http://www.ubuntuforums.org/showthread.php?t=207780&highlight=scsi+dma+hdparm")



So if dvd's won't play properly, here are some guesses at possible fixes:

Maybe your xserver.xorg is configured wrong.  (From the command-line you can reconfigure it with "sudo dpkg-reconfigure xserver-xorg").  Though then that should effect all video not just played from a dvd, so you might want to see what the video playback quality is on a download video file (high quality mpeg/avi).  

IIRC, the E1405's are dual-core processors.   If you have dual-core, you should make sure you are running a SMP (Symmetric Multi-Processing; aka dual-core) kernel.  Go to synaptic and install linux-686-smp, and reboot and run off of that.  (I also keep the 386 and 686 versions installed in case something goes wrong but nothing has yet, so I haven't needed to use them).  [I mention this, as I ran my laptop for about a month and a half in linux on just one processor, before I found out about SMP].

Finally, maybe just try some different dvds and some different settings on the players.  I prefer VLC to the other players (install vlc, wxvlc, and appropriate plug-ins from synaptic).  I believe you haven't manually change the dvd "Device Name" to /dev/dvd in the preferences to get it to open a disc though.
Hope this helps.

---

### Post by mcglnx on 2006-10-24
Thanks for your answer Jamesrl.

However I did have enable SMP under Linux (I have a Inspiron 6100) but the issue persists.

I tried other DVD but I doubt it is related to the dics.

Regarding the xserver configuration, I've ran the reconfigure for the ATI card as described on other pages. But may be you right: some settigs are not correctly set.

I'lll check this ASAP. would be better than switching to other disitribution or recompiling the Kernel... :)

Thanks.

---

### Post by mcglnx on 2006-10-24
:D :D :D :D :D :D :D 

Very good news! I'm able to play DVD.

***and this was not a DMA issue***!!!

In fact I have an ATI Radeon card and the DRI was not enabled. I removed all the fglrx drivers, re-installed the ATI driver as well as the restricted kernel module for ATI and it works!

glxgears gives a good indication of a 'sick' video driver.

Thanks a lot to everybody!
McG.

---

### Post by Lord Illidan on 2006-10-24
Excellent, glad to see it was resolved.

---

### Post by thephotoman on 2006-10-28
I've been looking for a DMA help thread, and am currently away from my Ubuntu box.  I'm putting a post here to mark my spot.  Please don't get offended.

---

