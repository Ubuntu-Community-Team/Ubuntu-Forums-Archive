---
title: "Joli OS 1.2 will nto boot after OS install on Asus EeePC 900A"
date: 2013-11-27
forum: Any Other OS
---

### Post by sahrjd on 2013-11-27
I am having an issue that appears to be identical to the one encountered [Metarune]("http://ubuntuforums.org/member.php?u=1735666") back in Sep 2012.  [Metarune]("http://ubuntuforums.org/member.php?u=1735666") [created a thread about the issue ]("http://ubuntuforums.org/showthread.php?t=2062348")but never received any answers and the thread has been closed so I am creating a new thread in the hopes someone has the solution.

The issue is:

I installed Joli OS 1.2 on an Asus EeePC 900A which has one hard drive: 4GB SSD (SM-ASUS-PHISON).

Install was accomplished using a USB drive with Joli on it.  Install proceeded with no issues.  Upon first reboot the system boots to a  blank screen with a flashing cursor in the upper left.  If I place the USB drive back in the computer and reboot the system it will boot from the installed 4GB SSD to the Joli login screen.  I am assuming that some how the install installed the boot info on the thumb drive or something.  While I have no idea how that would have happened I cannot understand any other way this is happening.

Any insight or assistance would be much appreciated.

---

### Post by Bashing-om on 2013-11-27
sahrjd; Hi !

I am not familiar with " Joli"; Does it recognize grub as the boot loader ?
Let's see what the operating system reports:
terminal command:
```

sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo grub-probe -t fs_uuid /boot/grub

```
Depending on the above output, might consider installing grub onto the MBR of the sda device - IF "joli" is the only operating system and only the one hard drive is installed:

Boot the operating system from the USB drive and install grub:
```

sudo grub-install /dev/sda

```
(un)mount/remove the USB drive and Reboot and see if now you are able to boot from the hard drive.

[INDENT][INDENT]maybe yes, maybe not so yes
[/INDENT][/INDENT]

---

### Post by Plumtreed on 2013-11-27
While this has nothing to do with 'booting' your Joli OS, are you aware that Joli's current iteration is as an 'on-line' operating system? Check out it's web site and it's name modification to Jolidrive! After signing on you are able access Joli and your files from any computer.....things are generally all in the cloud. I don't think Joli currently offers a version to 'install'.

I have Peppermint4 installed on my eeePC701, not dissimilar to your 900, which allows me to install a direct connection to Jolidrive thru their ICE package but, really, all you need is a conventional browser to access your own Jolidrive..........but more importantly, first have a look at Peppermint4 for your Asus900

---

