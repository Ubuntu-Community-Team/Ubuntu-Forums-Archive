---
title: "Permanatly mounting fakeRAID, windows workgroup, nvidia driver -&gt; Monitor not working"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by spamalam on 2006-08-02
Hi I have just installed Ubuntu.  I am completely new to linux barring brief encounters here and there.  I am having problems though.  Although nix has made leaps and bounds towards simplicity, I'm afraid there's folks like me that are still *too simple* :lol:

Anyway, first up I'll start easy.  I have a software raid, and i've downloaded and installed the dmraid package, and can mount my ntfs partitions.

***How can i mount these permanantly and so I don't have to be logged in as root to view them?***

Next up, I have a windows network that is made up of various switches, routers and access points.  I'm on a wired network, with a set workgroup.  The router allocated DHCPs to most pcs, this one included.  It seems odd but i have a net connection but i can't connect to my windows workgroup.  Its weird, because when i was using the livecd i printed something to a network printer.  Now I can't even ping machines on the network, by name or ip, only my router responds to pings (192.168.1.1).  I have a machine that's always 192.168.1.100 with the computer name Jake.  This is the pc that had my printer i used too, so i have obviously been able to connect to it before but not after installing and running automatix, and the updates

***How can I connect to my windows workgroup?***

and a followup,

***How can I mount (permanantly) my network shares?***

Next up, nividia.  I have a 6800 GT.  I used the automatix (found in american mcgee's blog, seems he's been doing some advertising for you guys) and that grabbed a new Nvidia driver.  Problem is, it doesn't seem to detect my monitor which is a DELL 2001FP.  Before its installation, it puts the display to my 2001FP and puts some pink rubbish on my CRT (Which is placed above on a shelf).  However, when the nividia driver is installed as soon as i get to the login screen at bootup the main monitor turns off, and it puts the display on my CRT which is plugged into the second DVI port on my card.  I restored "nv" instead of "nvidia" to get the display back on again, but i understand the driver is slower and not as good for 3d?

***How can i use the nvidia driver to output to my primary DELL 2001FP monitor instead of my CRT?***

I'm wanting to dual boot to windows XP since i do a lot of software testing and gaming, I've attempted to setup grub to boot into my raid but it's not playing fair. I have two paritions /dev/mapper/nvidia_bcaiicde1 is c:\ and /dev/mapper/nvidia_bcaiicde5 is d:\, with the device obviously being /dev/mapper/nvidia_bcaiicde.

I attempted to follow the last task of [http://www.mepislovers-wiki.org/index.php?title=Fakeraid_mirror](http://www.mepislovers-wiki.org/index.php?title=Fakeraid_mirror), and I added:
```

title		Windows XP SATA RAID
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/mapper/nvidia_bcaiicde ro quiet splash
initrd		/boot/init_raid.img
boot
```

***How can i get a dual boot to a fake-raid with grub on an ATA drive?***


I guess that's a mixture of trivial to more complicated things, appreciate any help you can give :)

---

