---
title: "This is getting me down. Please Help!"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by chrispche on 2008-01-03
I have an nVidia Riva TNT card an old AGP type. No it keeps defaulting to the max of 800X600. When it says the Legacy driver is in use it isn't. I test this by looking a GL Screensavers.

Now it was suggested before that I run sudo dpkg-reconfigure xserver.xorg this I have done and it seems to pick up the nVidia card fine and also the res and colour depth of monitor.

However after rebooting. All reverts back to the same 800X600.

I'm am trying to achieve 1024X768. 

I know this can be done. Because I accidentally done it this morning, with I must say a quite fancy nVidia logo when switching user's and logging on or off.

What am I missing. I have re-installed Ubuntu. I'm about to again!!! Any reason I shouldn't what's changed? What am I missing?

It just seem's to be one problem after another.

I want a perfectly running system which I have had before. Only the HDD went up **** alley.

Anyone help out please. I've been going around in circles all day. I have work to do and have done nothing so far and it 18:15 South African Time. I started trying to get this damn machine up and running ten this morning.

---

### Post by stump138 on 2008-01-03
You need to edit xorg.conf.  Start here:)

[here]("http://ubuntuforums.org/showthread.php?t=83973")

---

### Post by Kobalt on 2008-01-03
Once you installed the nvidia-glx-legacy package you need to run this command line in order to properly configure X:
```
sudo nvidia-xconfig
```
After a reboot you'll get your fancy nVidia logo and hopefully the good resolution :)

---

### Post by lamalex on 2008-01-03
Just FYI, with that card you should be running the legacy nvidia driver, that's fine. Could you post your xorg.conf?

---

