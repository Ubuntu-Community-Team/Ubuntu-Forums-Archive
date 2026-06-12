---
title: "configuring a kernel"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-04-23
I would like to reconfigure my Ubuntu kernel (or recompile it) to get rid of an experimental USB_SUSPEND "feature" that prevents proper use of my scanner. I have no need for this feature and don't want any parts of it until it's implemented properly. 

So, since I am almost a beginner, this looks like the place to post this.

I want to recompile my kernel. How do I make a floppy (or CDROM) boot disk from where I can attempt to configure a new kernel?

Also, is there a set of directions for doing this? I have directions for Suse, Fedora, and Mandriva, but these may have different commands and file locations than Ubuntu.

I did this before, a long time ago, under Suse, I think. But rather than switch and start all over again just because a book on these three distros, I would like to get this one going.

I'd also like to know how to recompile a portion of Linux, specifically the libusb section. Apparently you can do just part of it???

---

### Post by igknighted on 2007-04-23
Check out this thread: [http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel](http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel).  There is no reason to create a boot disk.  You configure and compile the kernel while booted to the old one, then install the new one and reboot.  If you mess up and it doesn't boot, no worries, just leave the previous one in the grub menu and boot it instead.

---

### Post by t2000kw on 2007-04-24
I checked out several threads in different places and I always hit a snag somewhere, an erorr message pops up, etc. The last one I tried to follow through hit a snag at the make menuconfig line. Everything was fine up until there. All I really need to do is to disable the USB_SUSPEND feature. I suppose I can either live with the problem or go back, start over, and try installing Edgy Eft, the previous version.

I do need to find a partitioning program that will allow me to do something. I have the Gnome partition editor but it doesn't seem to want to do anything but show me what's there, no changes are allowed (all change options greyed out). I wanted to move my /home folder to another partition, have one free that's 55 gigs, and can't seem to do it. I can't find my Partition Magic 8 CDROM, either. The idea here is if I move /home to another partition, I can reinstall Ubuntu Edgy, then tell it where "home" is.

---

### Post by silverglade00 on 2007-04-24
Copy all of the files and folders inside /home over to the 55GB partition. Don't forget the hidden .files and .folders. Then reinstall and tell it where your new home is. Use the same username. Should pick everything back up and have all your settings, files, etc.

---

