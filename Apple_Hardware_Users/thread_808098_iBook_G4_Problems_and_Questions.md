---
title: "iBook G4 Problems and Questions"
date: 2008-05-26
forum: Apple Hardware Users
---

### Post by nugznmugz on 2008-05-26
I've got an iBook G4 1.2 Ghz PPC w/ a gig of RAM.  Now here's my question(s):

Does the 8.04 PPC "live disk" actually boot to a live environment on Apples?

I can't seem to get it to do much of anything.

I get an error message after the display is detected and very shortly after that the screen goes black and the backlight appears to flicker on and off very quickly.

This is the error message I'm getting:

"PCI: Cannot allocate resource region 0 of device 1:10:18"

The last set of numbers (1:10:18) is as close as I could get to the actual set before the screen went black and the disk stopped spinning.

Thanks a lot.

---

### Post by frog_pilot on 2008-05-26
on my ibook g4 800 640 MB the hardy live cd is running fine. from a prerelease live cd. but if this works, the final live cd should also work

Booting takes a long time and i get two of these "cannot allocate resource region" errors while booting since 6.10

[https://wiki.ubuntu.com/PowerPC](https://wiki.ubuntu.com/PowerPC)
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

could provide some helpful advice for adding bootparameters like
```
nosplash
```
at the bootpromt of the live cd

---

### Post by stream303 on 2008-05-26
> **nugznmugz said:**
> I've got an iBook G4 1.2 Ghz PPC w/ a gig of RAM.  Now here's my question(s):

Does the 8.04 PPC "live disk" actually boot to a live environment on Apples?

You have enough resources that it should, although sometimes they balk at the video card requiring one to pass special kernel parameters at the second-stage boot: prompt.

Unless you absolutely need the live environment, and want to proceed to install, most suggest using the "alternate" cd image.

Definitely see this thread:
[http://ubuntuforums.org/showthread.php?t=798974](http://ubuntuforums.org/showthread.php?t=798974)

Once you edit your /etc/yaboot.conf file, make it permanent with:

```
sudo ybin -v -C /etc/yaboot.conf
```

---

### Post by jukoz on 2008-05-26
I have an iBook like that. To boot it into liveCD you have to tell it which kernel to use. It is in the beginnig, with the first prompt. There just type:
```
live-nospalsh-powerpc
```

This sould work, since I am typing this from a LiveCD on an iBook.

I found this solution on this forum a few day ago.

Ajt!

---

### Post by stream303 on 2008-05-26
[QUOTE=jukoz;5048782]It is in the beginnig, with the first prompt. There just type:
```
live-nosplash-powerpc
```

Glad that worked! (fixed nosplash typo). :)

This is at the second-stage of the yaboot boot: prompt, where you can hit -tab- to stop the automatic countdown and enter your parameters like you did manually..

---

