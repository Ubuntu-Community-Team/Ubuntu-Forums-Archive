---
title: "Linksys card problem in Gutsy"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by marbobj on 2008-02-14
I have a dual boot with Memphis (Ubuntu based) and Ubuntu 7.10 and using a Linksys Card(WMP54G).  Using a wep, hexademical key.  With Memphis everything works well, but I can't get the thing to go in Gutsy.  Need help.

I did the ndiswrapper (installed through synaptic), using the driver on the installation CD.  When I do the ndiswrapper -l, I get the driver installed and alternate driver dialogue.  When I do sudo iwlist scanning, I get a scan result with a mode of Master and other information.  But when I scan for networks with the Kwifi Manager, I get no networks available.

I did the sudo ndsiwrapper -m and get the alias is in already in place.

When Gutsy boots, though I get an error on modprobe.  There about 5 lines- all of which starts with"Modprobe problem", then it ends with "check dmesg".

Currently using the dialup connection on the same machine, which is how I got the synaptic download.  I can post outputs of commands, if I know which ones you need to help diagnose this.

Thanks a lot for any help,

---

### Post by dcstar on 2008-02-14
> **marbobj said:**
> I have a dual boot with Memphis (Ubuntu based) and Ubuntu 7.10 and using a Linksys Card(WMP54G).  Using a wep, hexademical key.  With Memphis everything works well, but I can't get the thing to go in Gutsy.  Need help.
.......

What kernel versions are used in each system?

---

### Post by marbobj on 2008-02-14
Gutsy Gibbon is 2.6.27-14 and Memphis is 2.6.15-26-386.

---

