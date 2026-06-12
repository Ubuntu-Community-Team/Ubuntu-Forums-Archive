---
title: "Internet, where to start?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by PartyTaco on 2007-10-24
I am using Ubuntu 7.10 .I have a Wireless-G PCI Linksys wireless card. 

Model: WMP54GS

I am a complete noob, don't know the terminology, and have just a little spare time to work with ubuntu each day. With the background done, all I need is some direction to get my internet working.

I've been reading threads for an hour and 1/2 and tried to do some stuff on my own but I really don't know where to start. Thanks in advance!

---

### Post by fain on 2007-10-25
check out this thread

[http://ubuntuforums.org/showthread.php?p=3596387]("http://ubuntuforums.org/showthread.php?p=3596387")

and this one second post down 

[http://ubuntuforums.org/showthread.php?t=581406]("http://ubuntuforums.org/showthread.php?t=581406")

i think you just need that deb maybe the firmware i dunno and it should work. I have a HP zv6000 and it worked on mine. I dont remember what i did though. just search for broadcom and Ubuntu or gutsy

that card WMP54GS has a Broadcom chipset which has crappy linux support. :(

---

### Post by PartyTaco on 2007-10-25
> **fain said:**
> check out this thread

[http://ubuntuforums.org/showthread.php?t=581406]("http://ubuntuforums.org/showthread.php?t=581406")

 :(

> **Zer0Nin3r said:**
> I rely on a wifi connection that I share (yes I pay) with my neighbor.  I upgraded the laptop first and had to boot to my windows partition to snag two files that were part of the restricted drivers Ubuntu was asking for.  One was the .deb file for the firmware cutter for Broadcom WiFi Cards (BCM 43xx) and the other was the "firmware" file that the cutter extracts from.  After these two steps the card is working flawlessly.  No need for Ndiswrapper either!


Once I have those files, what do I do with them? How do I install them or whatever.

---

### Post by PartyTaco on 2007-10-26
Bumpity Bump Bump

---

### Post by Nachtengel on 2007-10-26
To install a .deb file navigate to the directory housing the .deb file, then type
```
sudo dpkg -i *debpackagename*.deb
```

This uses the dpkg utility to install the debian package file (.deb).

---

