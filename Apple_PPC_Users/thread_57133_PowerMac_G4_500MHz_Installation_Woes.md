---
title: "PowerMac G4 500MHz Installation Woes"
date: 2005-08-15
forum: Apple PPC Users
---

### Post by emihatov on 2005-08-15
Hi, 

Just finished a completely beautiful seamles sinstallation of Ubunto onto a Lombard G3 PowerBook and then popped the same ISO burn CD into my G4 but no go. Ignores the "C" key on boot, the linux distro appears as a boot option when you hold the option key down on boot-up, but when you select it for boot, the screen quickly flahses red before reverting to the boot options screen again. 

I've trid USB - nothing. 
I've tried DHCP - couldn't find instructions easy enough for me to understand and implement. 
I tried booting onto the CD, a USD drive, you name it, all comes out with nothing. 

I heard that CD Media might be at fault, but I've burnt onto Verbatim, Imation, and some Itchie Dragon ones, same thing. G3 is ok, G4 is not. 

Any ideas? 


em

---

### Post by emihatov on 2005-08-15
An Update. 

Thanks to the forum archives ( [http://use.perl.org/~statico/journal/23392](http://use.perl.org/~statico/journal/23392) ), I've been able to get yaboot to work using my G3 laptop as a tftp boot, but now all I get is a list of 

MAC-PARTS: specified partition is now valid
MAC-PARTS: specified partition is now valid
...
MAC-PARTS: specified partition is now valid
MAC-PARTS: specified partition is now validcd:-1,/install/powerpc/vmlinux: Unknown or corrupt filesystem
boot: _

If anyone knows how I can proceed from here, it would be really great to hear from you., 

It's a 500MHz G4 Power PC Macintosh with AGP graphics, 768MB RAM, 1 IDE boot disk with OS9 and OSX boot partitions on it in HFS+ and a SCSI hard disk with three paritions of HFS that I want to use for my Linux installation. They're connected to an adaptec AHA2940 SCSI controller card in the first PCI slot... 

Thanks again...

em

---

### Post by emihatov on 2005-08-17
Another update... 

I now have a black screen. 

I've tried: 
a) zapping the P-Ram (It restarts when I hold down the keys, so I know it's doing something...
b) Holding down C with the OSX CD in the drive
c) Holding down X to boot into OSX
d) Holding CMD-OPT-SHIFT-DEL to boot from external drive
e) Holding CMD-OPT-O-F to boot into Open Firmware
f) Holding CMD-S to boot into single user
g) Pressing the ROM button on the MB for 10sec / 20 sec / 30 sec / 1 min
h) Removing the ROM battery for 20mins / 30mins / 1 hour / 6 hours. 
i) Replacing the AGP GPU with another. 

The only thing that actually makes some difference is zapping the P-Ram. All the others seem to do nothing. 

On boot, the screen detects a signal, powers up, the Caps-lock light on the keyboard comes on, but then goes out and the screen goes back into sleep without displaying anything. Drives are spinning, the NIC appears on my LAN (actually apparently serving on port 110!) but i can't VNC or Telnet into it. 
 
I'm at wit's end here... Anyone have any ideas? Please help! 

em

---

### Post by emihatov on 2005-08-18
A further update:

Connected a DVI monitor and foudn the display again. Seems for some reason the VGA output on the card decided to stop working... Now reinstalling Ubuntu. 

em

---

### Post by lubod on 2005-08-24
Sorry to hear you have problems with the G4, I sympathize.

In my (admittedly limited) experience, it seems Ubuntu will only boot New World Macs, which of course the G4 is, but even then only from the internal CD/DVD ROM (if this is incorrect I hope someone more knowledgeable corrects me). Are you by chance using a Firewire or USB external CD ROM drive? You mention trying USB in your post. If you can, try hooking up a CD/DVD drive to the G4 internal bus, assuming it's a desktop.

Assuming you have the non-working VGA solved or can deal with DVI of course.

---

