---
title: "Running ubuntu off a disk"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by rox1547 on 2008-04-09
Warning: Noob alert. I am (was) a Vista user until the hard drive on my laptop croaked last week.. so I have been running ubuntu off a disk and flash drive. It takes a while to load, but it's not a huge problem, I just don't turn my laptop off anymore. But, I have had to reboot once or twice, and it's annoying having to re-install programs. There aren't many I use anyway, mainly VLC for music and films. My question is, I have a 500 gig usb external drive hooked up to my laptop. Can I install VLC and whatever else I want to try, to the external drive so I don't have to reinstall if I have to reboot?

---

### Post by StOoZ on 2008-04-09
first try
sudo apt-get clean
sudo apt-get audoclen

in terminal

---

### Post by rox1547 on 2008-04-10
ubuntu@ubuntu:~$ sudo apt-get clean
ubuntu@ubuntu:~$ sudo apt-get audoclen
E: Invalid operation audoclen

---

### Post by eternicode on 2008-04-10
Lol, eazy there, stooz.  Not exactly what they were looking for :)

The comand is actually "sudo apt-get autoclean", but that won't help your case here.

I don't think it's possible to install apps to external drives for a live system.  Might check out this link: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) .  Not sure it'll help much, though.

Alternatively, if you feel up to a good challenge, you could modify the live image itself to include the apps you use: [http://edoceo.com/liber/ubuntu-live-usb](http://edoceo.com/liber/ubuntu-live-usb) .  Unfortunately, I think this method requires a working computer.  You might be able to mount and store the files on the external drive, using the live system as your "working computer".  You'd then have to transfer the new image to the flash drive somehow; not sure if you can overwrite that file while using that image, or if you;'ll have to use another comp to transfer it.

Iideally, this is the way to go if you don't plan on installing, but I've tried modding the squashfs image several times, all with little or no luck.  I think the main issue was logging in to the live system -- it booted fine, but didn't recognize any users, default or otherwise.

Best of luck :)

EDIT:
Also, you might try partitioning off some of the external drive and installing Ubuntu on that part.  Then, you could boot off the external and have all your apps etc saved there as well.  Unless you plan on taking Ubuntu mobile with you, in which case an external drive might be a little bulky :)

---

### Post by rox1547 on 2008-04-16
I haven't had a chance to try any of these suggestions yet. Stupid job, I work too much. But I have another question, regarding installing Ubuntu on my external drive and possibly being able to use it as my "working computer". Would I have to format it before I could partition and do an install? I'd rather not lose the stuff I have stored on it. How would I go about installing to the external drive? I don't mind being chained to the external drive, since I gave my router the boot about a month ago and I'm already tied down with an ethernet cable.

---

### Post by mikewhatever on 2008-04-16
No, you wouldn't need to format the whole HDD, just the partition you install Ubuntu to.

---

### Post by eternicode on 2008-04-16
Like mike said, you wouldn't need to format the whole thing.  Use GParted, which should be available on your livecd, to shrink the current FAT32 partition (assuming it's a standard drive) and add a new EXT3 partition for linux.  GParted is a non-destructive partitioning program, meaning it can repartition a drive without having to wipe it clean first.

You should try to backup what you can from the drive before you start, though.  While I've never had it happen, GParted itself warns that it can cause permanent filesystem damage if used improperly.  Also, if you have a windows computer available, hook the external up to that and run [jkdefrag](http://www.kessels.com/JkDefrag/) at least once (it'll take a while, depending on how much data you have and how fast the computer is).  JKDefrag is a free windows defrag utility, and, in my opinion, is much better than Windows' standard defrag utility.  Unfortunately, I don't think you can specify which disk it works on; it just does all drives that it finds attached to the computer.

Once you're partitioned, boot the livecd up and click the install icon on the desktop.  Go through the regular options.  When it asks where you would like to install (it usually has options like "guided installation - use entire disk", "guided installation - use free space", and "manually select partitions"), choose the "manual setup" option.  Then choose to edit the EXT3 partition on the external drive, and specify the "mount point" to be "/".  Also check the "format" box for this partition.

---

### Post by philinux on 2008-04-16
Stick a new Hard Drive in the laptop. They just slot in I believe. Screwdriver only required.

---

### Post by Paqman on 2008-04-16
You might want to try Knoppix. It's a LiveCD distro that allows you to create an image on a disk that makes it a persistent installation. I've not tried installing the image on a USB drive, but I don't see why it shouldn't work.

The major downside is that it's hideously ugly to look at.

EDIT: [How to install a Knoppix disk image to a USB drive](http://www.pendrivelinux.com/2006/08/20/knoppix-linux-live-cd-and-usb-flash-drive-persistent-image-how-to/)

---

### Post by eternicode on 2008-04-16
There's a similar guide for ubuntu: [LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent).  Not the best-named article, but I use it regularly to setup a "Live USB" system for installations (minus the "persistent" aspect).

Best I can tell, the squashfs image, which is where the /usr, /boot, etc directories are, is what is actually used by the system.  Most packages that you install get installed into the /usr subdirectories (/usr/bin, amongst others).  Since the squashfs file is read-only, these changes are written to memory only, not the system itself.  The persistent aspect comes from saving your settings and files and such on the extra partition, which I assume is probably mounted as /home.

It's worth a try, but I doubt it'll work for applications.

---

