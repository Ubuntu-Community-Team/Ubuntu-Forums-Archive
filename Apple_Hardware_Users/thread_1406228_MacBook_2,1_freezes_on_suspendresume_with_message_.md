---
title: "MacBook 2,1 freezes on suspend/resume with message &quot;Resume: libgcrypt version: 1.4.4&quot;"
date: 2010-02-13
forum: Apple Hardware Users
---

### Post by likesalmon on 2010-02-13
I'm running Ubuntu Karmic 64 bit 9.10 on a MacBook 2,1.  My computer doesn't resume after suspend.  9.10 is the first version I've tried running on this machine, so I don't know if suspend/resume worked with past versions of Ubuntu or not.

I've followed the instructions from [http://ubuntuforums.org/showthread.php?t=1215928](http://ubuntuforums.org/showthread.php?t=1215928) to no avail.  After installing the ```
uswsusp
``` package and running ```
sudo s2ram --force
``` the screen turns black and reads ```
resume: libgcrypt version: 1.4.4
```  The computer hangs and I have to reboot.

I haven't been able to find anything that helps, but I know I'm not the only one with this problem (see the comment from lubuntu at [http://it.newinstance.it/2009/11/25/suspendresume-in-karmic-2/](http://it.newinstance.it/2009/11/25/suspendresume-in-karmic-2/)).

Any help would be greatly appreciated.  I've been living with this for months.

---

### Post by sentient6 on 2010-02-19
I am having the same problem on a MacBook 2,1 with 32bit Karmic. Suspend worked fine under Jaunty... Should we file a bug report somewhere?

---

### Post by linuxopjemac on 2010-02-19
I have 32-bit Karmic Koala running on a MacBook 2,1 too, for me it works swell...The only thing I need to do (which I hadn't in the past), is that I have to reload ath9k.

---

### Post by sentient6 on 2010-02-19
From what I can tell it seems that the failure to suspend and the resume: libgcrypt messages are separate issues. When I try to switch to tty1 with ctrl-alt-f1 the screen flickers and displays the resume: libgcrypt version: 1.4.4 message. Hoping to track down a solution to that  somehwere.

Anyway, I assume that what is happening is that s2ram is crashing and dumping me to the console. When I suspend from the gnome panel all I get is a blank, backlit screen.

linuxopjemac, do you mean that you have to reload the ath9k driver after you resume or do you unload it before you suspend?

---

### Post by linuxopjemac on 2010-02-19
I reload it after resume. The wireless is broken after resume.

---

### Post by sentient6 on 2010-02-20
Alright. Thanks. Just for reference, did you upgrade from Jaunty or do a fresh install? I'm thinking of just doing a clean install of karmic and copying back my home directory.

---

### Post by sentient6 on 2010-02-20
Just a quick update. In an attempt to fix some graphics issues I updated my graphics driver with sudo aptitude install xserver-xorg-video-intel. Upon reboot I'm no longer seeing corruption on my terminals and suspend seems to be working...

---

### Post by linuxopjemac on 2010-02-21
FYI: I installed Karmic over the old Jaunty partition, so basically a fresh installation.

---

