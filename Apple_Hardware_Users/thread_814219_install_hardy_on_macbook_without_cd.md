---
title: "install hardy on macbook without cd"
date: 2008-05-31
forum: Apple Hardware Users
---

### Post by kenpokarateboy on 2008-05-31
hello! i installed feisty around this time last year on my first-gen macbook (specs [here]("http://support.apple.com/kb/SP23") - it's the middle-end model - 2 ghz white), and have, over the past year, upgraded to gutsy and hardy. However, lately i have noticed that my system is slow, and so i decided to do a clean install.

I backed up my files, but to install, i tried to use unetbootin to install, because my cd drive is broken. However, instead of choosing to netboot, i chose the option where it downloads the live CD, you restart, and select the live CD from the grub menu.

i started the installer, set up the partition table to have my EFI system partition, a 20-something GB mac partition, a 1GB swap partition, and the rest my ubuntu partition. however, when i went to install, it couldn't create the ext3 partition. after trying again, and realizing it had screwed up my existing ubuntu partition, i installed unetbootin on the system that was then running. i installed the "live cd" to a flash drive and restarted.

Now, when i try to boot (i'm using rEFIt), i can boot into mac (that's where i am now), but if i try to boot onto the usb, it gives me a black screen that says "boot error", and if i boot into ubuntu, it dumps me into a grub command line.

I have access to another mac, but it's a powerPC mac.

anyone have and ideas? the only things i can think of are setting up the other mac as a boot server, and network booting from it, or creating a new partition on my HD and running the installer from there. any idea how to do either of these?

thanks so much!

---

### Post by cyberdork33 on 2008-05-31
booting via usb or firewire seems not to work on Intel Macs (unless it is OSX), or unless it is an external CDROM.

---

### Post by Mon on 2008-09-30
I've been looking around for an alternative way to install Linux on my MacBook as well.

[LIST]
[*]It seems the Mac won't do a PXE or Bootp based boot, only Apple's "Apple Software Restore" (asr).
[*]You can't use the MacBook Air's "Remote disk" feature; this allows a MBA to boot from a cdrom from another Mac.
[*]I tried copying the Ubuntu cd to a USB disk using liveusb and install from there. Also no succes.
[/LIST]

I'm very interested whether anyone knows another way of installing Ubuntu on an Intel Mac without using the internal dvd-rom since mine is unfortunatly broken.

---

### Post by ModdTaco on 2008-09-30
LOL... Not to your problems but how so many people have their CD drives broken on there GREAT macbooks... But seriously now. If you can't get firewire working buying a USB CD/DVD drive would work just as good. There pretty cheap now and days.

---

### Post by Mon on 2008-09-30
That would be the most practical sollution, yes.
However it wouldn't be as "cool" as netbooting (why install linux on a Mac anyway, because i CAN that's why!)
Maybe i'll buy one some time but i pretty much never need to use my cdrom anyway.

---

