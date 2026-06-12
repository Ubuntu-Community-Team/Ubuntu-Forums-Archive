---
title: "Kino raw1394 ?? how to install make work ?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by lupgop on 2007-10-27
I have downloaded Kino - it doesnt seem to see my camera - i looked in help but it a bit over my head ... went into preferenecs as i gather i should have raw1394 ? under the IEEE 1394 tab it says - 
 The IEEE 1394 Subsystem is not responding. 
 The raw1394 module must be loaded, and uou must have read and write access to /dev/raw1394
 
 i am logged in with the only password and under permissions on the file /dev/raw1394 it says owner and group have read/write others are forbiden ??? (tried letting others have read write too , but it said access denied to /dev/raw1394 ??????????
 
 so i guess what im asking is a/ how do i load the raw1394 module and b/ do i have acces ???

---

### Post by louieb on 2007-10-27
Did you use Synaptic or aptitude or apt-get get to install it? Its in the repositories.

---

### Post by e1_ang on 2008-02-09
Just do this as root. 

It works for me. I'm using Ubuntu 7.10

gksudo kino

The problem is it requires root access, so the above command run Kino with root user ID.

---

### Post by teledyn on 2008-04-12
There still must be something magical about your system; I have 7.10, installed kino 1.1.0 from the aptitude command, ran "modprobe raw1394" and got "ieee1394: raw1394: /dev/raw1394 device initialized", there is a /dev/raw1394 (owned by root.disk with perms 660), but when I run Kino as root, I get "cannot read /dev/raw1394" and in the preferences tab for ieee1394 devices, the pulldown list is empty :(

---

### Post by teledyn on 2008-04-13
Many hours later ...

ok, lspci says...
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

linux1394.org says the Ricoh R5C552 works, and the Ricoh *unknown* works, but no mention of this particular (Dell Inspiron 1521) chipset is supported; it would seem reasonable, and all the system hardware readouts identify it completely without warnings or errors.

and when I modprobe raw1394, dmesg says ...
0532.460000] ieee1394: raw1394: /dev/raw1394 device initialized

and /dev/raw1394 exists, it is owned by root.disk on which there is a substantial thread over on [Ubuntu's Bug Tracker]("https://launchpad.net/ubuntu/+source/kino/+bug/6290") explaining why this must be and what they hope will be in the future and the current workaround which is to either reassign the device to a new unique group or to simply run kino as root, of which I've tried both :(

dvgrab says there is no camera, kino says there is no AVC and when I roll the camera manually kino detects no signal; in the kino output I see ...

>>> Using iec61883 capture
>>> iec61883Reader::StartThread on port 0

the last line is repeated over and over and I get no digital video flowing :(

Is there some way to test the port?  I tried using a known-good cable to connect the laptop Firewire port to the port on the desktop computer which I had previously used for Kino, so I know that port and that cable work, but the Kino on that machine refused to export over IEEE 1394 saying "no camera attached" -- that could mean it saw no response, or merely that the response did not include AVC and was rejected.

Could someone who has Kino working on 7.10 please post their configuration, the dmesg/lspci report, lsmod lines for *1394?  I might help in figuring out just what it is that is preventing the glorious experience of DV on these other machines :)

---

