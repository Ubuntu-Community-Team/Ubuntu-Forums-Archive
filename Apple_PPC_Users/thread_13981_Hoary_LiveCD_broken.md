---
title: "Hoary LiveCD broken?"
date: 2005-02-04
forum: Apple PPC Users
---

### Post by jjramsey on 2005-02-04
I downloaded the LiveCD ISO from [http://cdimage.ubuntu.com/releases/hoary/array-3.5-live/](http://cdimage.ubuntu.com/releases/hoary/array-3.5-live/) and burned it using cdrecord from fink. The ISO dated from January 26, 2005. For me, the CD didn't work out too well. X couldn't detect the video, and I got dropped to a login prompt. This obviously doesn't seem to be everyone's experience, but for all I know maybe they used an earlier version of the CD and something broke later.

The MD5 sum for the ISO is fine. If I mount the ISO, cd to it and run "md5sum -c md5sum.txt", I get a *lot* of "can't open /path/to/really-long-filename-longer-than-32-characters.udeb" errors, and it appears that for every such error there was a file on the mounted ISO named "/path/to/really-long-filename-longer-tha", where the filename was truncated to 32 characters in length. For comparison, I downloaded the ISO for the i386 version of the LiveCD, and on the i386 CD, running "md5sum -c md5sum.txt" leaves no error message, and there were no issues with the filenames being truncated. As far as I can tell, the filenames aren't being truncated at my end, but they are like that on the ISO.

Whether this has anything to do with the LiveCD bombing on me, I don't know.

---

### Post by talkeetnik on 2005-02-04
Recent success with LIve ppc cd on my PISMO Powerbook (older 500mgz)

After several missteps a simple:' linuxpowerpc'  at the prompt got it up and
running, ATI grphics card, sound and Airport Wireless working.
browsing on the web and sending email in less than ten minutes.....
If I had tabbed to see the suggestions to start with, I probably would have
been up and running  in 5 minutes... Amazing...

All in all I was Very Impressed

With my small 12gb hd, I may decide to install this distro exclusively
and eliminate the proprietary one on it....

William (Bill) Bouterse
Talkeetna, Ak

---

### Post by jjramsey on 2005-02-04
[QUOTE=talkeetnik]Recent success with LIve ppc cd on my PISMO Powerbook (older 500mgz)

After several missteps a simple:' linuxpowerpc'  at the prompt got it up and
running, ATI grphics card, sound and Airport Wireless working.
browsing on the web and sending email in less than ten minutes.....
[/QUOTE]

Could you mount your LiveCD and check the contents of the directory "pool/main/l/linux-source-2.6.10" on the CD? I want to see if the file names in it are truncated. They should all be longer than 32 characters, and end with the extension ".udeb".

---

### Post by jjramsey on 2005-02-05
Figured out what's going on, more or less. I got bit by Ubuntu bug [4297](https://bugzilla.ubuntu.com/show_bug.cgi?id=4297).

---

### Post by talkeetnik on 2005-02-05
Out of curiosity I checked that bug posting out...

My xorg.conf file has a different "monitor" setting but works...

Did the suggested changes fix your problem?

What machine/graphics-card are you using?

---

### Post by jjramsey on 2005-02-05
[QUOTE=talkeetnik]
Did the suggested changes fix your problem?[/QUOTE]

Yes, they did. That's how I finally figured out that bug 4297 was the bug that hit me. (Well, that, and the fact that the error messages were identical to those in the bug report.)

> What machine/graphics-card are you using?

eMac with ATi Radeon 7500.

---

