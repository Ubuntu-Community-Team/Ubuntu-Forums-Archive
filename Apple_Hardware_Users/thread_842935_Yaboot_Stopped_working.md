---
title: "Yaboot Stopped working?"
date: 2008-06-27
forum: Apple Hardware Users
---

### Post by gphaze on 2008-06-27
I spent a pretty  happy week using my Ubuntu/PPC installation, then had to return to the OS X environment to get some work done.

I have noticed over the course of several reboots that I no longer get the screen at startup which gives the option of booting into linux or OS X and wonder what up with that.

Any clues?

thanks!

gphz

---

### Post by stream303 on 2008-06-28
I'd try reapplying the yaboot.conf file again by going into a rescue shell (or if you can get the live-cd to work, no problem) and doing:

```
sudo ybin -v -C /etc/yaboot.conf
```

To get to the rescue shell with the alternate-installer, at the second stage of the yaboot boot: prompt, just hit -tab- to stop the automatic countdown. Then type "rescue-powerpc" or "Linux single" which will eventually prompt you for the root partition to drop your shell into.  Dedicated installs start at /dev/hda3, but you can work your way up from there if yours is different.

---

