---
title: "How do I install from an installed system"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by tadiv on 2007-02-22
I have been having a lot of trouble insalling from the 6.10 live CD to a USB drive (60gb)...  Since I have a good install on a desktop machine, I was wondering if there is a way to install from that desktop's OS to the usb drive.  I wonder because I can't find the "Install" process on that desktop...

Thanks,
Tom

---

### Post by ^rooker on 2007-02-22
1) Although your installed system might look like the one from the live CD, I don't think it's even possible to simply use that system for installation

2) Please provide more details about your "problems" with your USB drive? 

I've heard that the live-CD tries to mount USB/Firewire devices automagically, thus causing problems during installation, since the partition's already mounted... You might want to try the "Ubuntu Alternate" version for installation on your USB drive. There's a plain text-mode installer, so no background things to worry about. :)

---

### Post by tadiv on 2007-02-22
I have a few posts in this area - typically the failure happens while creating the ext3 filesystem - the install progress is at about 15% and either the FS creation fails, or fails to mount.  I have tried using the partition tool to create partitions ahead of the installer then using the "maunal mode" to set up the drive for the installer - but the installer insists on formatting some partitions and it fails during that process...  At one point I had the system loaded to the usb drive, but could not get that drive to boot...  See my entries at:

[http://ubuntuforums.org/showthread.php?p=2187265#post2187265](http://ubuntuforums.org/showthread.php?p=2187265#post2187265)

and that links to my problems trying to boot from the usb...

Thanks for your help...

Tom

---

### Post by tadiv on 2007-02-23
> **^rooker said:**
> 
I've heard that the live-CD tries to mount USB/Firewire devices automagically, thus causing problems during installation, since the partition's already mounted... You might want to try the "Ubuntu Alternate" version for installation on your USB drive. There's a plain text-mode installer, so no background things to worry about. :)

You hit the nail on the head as far as my installation problem goes -- the installer could not mount the newly created FS because it was already mounted.  All I had to do was unmount the usb drive before I started the installer.

I have successfully installed to the usb drive (including grub) but I guess my laptop will not boot from that drive - end of story.  SO I have to live with grub on the internal HD of the laptop and I'll just have to have the satellite around to boot that other OS...

Thanks for the help!

---

