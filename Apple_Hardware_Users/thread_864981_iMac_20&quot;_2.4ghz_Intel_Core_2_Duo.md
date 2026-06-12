---
title: "iMac 20&quot; 2.4ghz Intel Core 2 Duo"
date: 2008-07-20
forum: Apple Hardware Users
---

### Post by Secrest on 2008-07-20
I have been reading the posts trying to figure out my problem and have saved several links in my bookmarks but can't seem to figure this out.  I have installed Ubuntu 8.04 a couple of times on the iMac to do a dual boot with boot camp but no matter what I do I can't get sound.  It won't play a DVD and I can't get it to wake up from sleep.  Right now Ubuntu is not on my iMac, I got tired of messing with it.  There doesn't seem to be a lot of info on the iMac's with Ubuntu that I could find.

I have installed it on a few PC's with no problems and I know that Apple is more proprietary and thats probably why I am having more problems.

If anyone has any good info that would be appreciated.  If I can't get Ubuntu working properly I am just going to go and get me a non apple laptop for myself and let my wife takeover the iMac.  My wife hated linux and I loved it on our pc.  Did not want to go back to windows so I sold the dell and got the iMac hoping I could dual boot with linux and my wife could use OS X.

I am wondering if all the problems would go away if I just installed it using VMWare Fusion.

---

### Post by DonnieP on 2008-07-20
Does sound work from the LiveCD before you install?

---

### Post by DonnieP on 2008-07-20
For your sound problem, check out the FAQ in this forum.  There's a fix in there that might apply to your situation.  As to VMWare Fusion, any virtualization solution is certainly an option.  I ran Ubuntu on an iMac with Parallels for several months before installing it to a partition.

---

### Post by paullinux on 2008-07-20
Just include

options snd_hda_intel model=imac24

at the end of alsa-base and options (in /etc/modprobe.d).

Works, but sound is like listening to a cheap radio...

This is at this moment the best solution available ... until someone comes up with another idea...

By the way, I've been running Ubuntu 8.04 with virtualbox on OSX (=free), works ok, including sound and proper screenresolution  if you install the virtualboxlinuxadditions.  But no video-acceleration, so no compiz-things...

---

### Post by cyberdork33 on 2008-07-21
I assume this is an aluminum iMac... Sound fixes are posted. You should also check the sound levels by running 'alsamixer' in the terminal and making sure that the Master and PCM channels are turned up and unmuted.

Your suspend problems are probably due to the ATI drivers.

---

