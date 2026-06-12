---
title: "DVD play isn't smooth"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by jhamer9 on 2005-11-19
hello.  I have been trying to play a few different DVD's and have a problem with the playback.

The video is not playing smoothly.  The audio is fine, but the video will briefly pause and jump ahead to catch up with the audio every 2 seconds or so.

I am on kubuntu and am using kaffeine to play the video.  When I first launced kaffeine, I received a few error messages that I didn't have the proper codecs installed so I installed libdvdcss2 and executed the following command:

```
 sudo dpkg -i libdvdcss2_1.2.9-0.0_i386.deb 
```

I then received the following error:

```
sudo dpkg -i libdvdcss2_1.2.9-0.0_i386.deb
Selecting previously deselected package libdvdcss2.
(Reading database ... 61073 files and directories currently installed.)
Unpacking libdvdcss2 (from libdvdcss2_1.2.9-0.0_i386.deb) ...
dpkg: dependency problems prevent configuration of libdvdcss2:
 libdvdcss2 depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
dpkg: error processing libdvdcss2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdvdcss2
```

Is there something else I need to install or configure for smooth playback or is my hardware a limitation.  I am using a Compaq M700 w/500Mhz PIII and 192MB of RAM.  I know it's no speed demond, but watching a DVD shouldn't cause this much skippage (is that a word?).

Is there a better player than kaffeine, or is it the codecs?  Thanks for any help.

---

### Post by JurB on 2005-11-19
you have to enable DMA, check [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514447](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514447).

---

### Post by basscad on 2005-11-19
same problem here

i installed libdvdcss2, missing packages i got
[here]("http://mirror.nus.edu.sg/Debian/pool/main/g/glibc/libc6_2.3.5-8_i386.deb")
and
[here]("http://ftp.uk.debian.org/debian/pool/main/i/initrd-tools/initrd-tools_0.1.84_all.deb")

but even with libdvdcss2 installed dvds dont play smooth

---

### Post by bionnaki on 2005-11-19
did you enable dma?

---

### Post by jhamer9 on 2005-11-20
Enabling DMA did the trick.  Thanks for the help!

---

