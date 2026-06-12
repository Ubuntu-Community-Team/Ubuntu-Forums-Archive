---
title: "inter-system use"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Nemesis1278 on 2007-10-09
I was wondering is wine a program like Parallel desktop for for mac.  If so this would be great because I would like to use ubuntu on a dual boot system.  I've used Freespire and it was ok.  I'm going to be installing ubuntu server on my computer and I want to be able to access files on my windows system without having to reboot and put it on a usb flash drive.  Thanks for any info.:)

---

### Post by jfinkels on 2007-10-09
> **Nemesis1278 said:**
> I was wondering is wine a program like Parallel desktop for for mac.  If so this would be great because I would like to use ubuntu on a dual boot system.  I've used Freespire and it was ok.  I'm going to be installing ubuntu server on my computer and I want to be able to access files on my windows system without having to reboot and put it on a usb flash drive.  Thanks for any info.:)

wine is an application layer that allows Windows programs to run on Linux systems.

I think Parallels is a virtualization application, that allows you to boot a separat, 'virtual' system in it's own discrete instance within an already running operating system, similar to VMWare, Virtualbox, etc.. 

You don't need wine to access files on a separate partition, you only need to mount it using the 'mount' command. You may need the ntfs-3g drivers if you have an NTFS formatted partition (see here for more info [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)).

---

