---
title: "iBook 700mhz freezes"
date: 2008-06-26
forum: Apple Hardware Users
---

### Post by Scientia on 2008-06-26
I've got ubuntu running on this old 700mhz iBook G3, 384mb ram. Somehow, my computer constantly freezes, sometimes with many programs on, sometimes with one running. When it freezes i can hear the computer running and can move the mouse pointer, but thats about all. It might be a hardware issue because i've got a iBook G4 800mhz(OSX 10.4) that does the same thing too.
Any ideas?

---

### Post by stream303 on 2008-06-26
Maybe just a resource issue - maybe you can catch it before you lock up.  Have you tried load a system-monitor-applet, or even easier, use apt-get or synaptic to install HTOP  (regular top will do the job, but **Htop** is far nicer, imho.)

I caught Network Manager misbehaving on my G4 ibook in this manner...  not saying that is your problem, but NM took 100% cpu time, so I had to do something about it.

I really dig Htop's ability to be resized down pretty small so you can keep an eye on the major parameters while running other stuff.

---

### Post by Scientia on 2008-06-26
Yup, i've used htop.. But the problem is that the freezing seems random.. I can run a whole host of progs at the same time(including resource hog openoffice) and not jam but another time i just have firefox and pidgin going and poof.

---

### Post by Scientia on 2008-06-26
Nevermind that last one.. Firefox running alone already has 100% cpu usage, with others on its worse. I still can't be sure if this is what causes the freezes, though. I tried a simpler browser kazehakase but it doesnt have some useful features..

---

### Post by stream303 on 2008-06-26
It's kind of hard to pin down since you mention that your other ibook running OSX does the same thing?  Power issues?

Some generic things that have bitten me in the past:

Instead of waiting for 28 or so reboots to occur to fire off an automatic filesystem check, force it at the next reboot with:

```
sudo touch  /forcefsck
```

Upgrading ram from an existing install and not making sure that the swap file is at least 1x the new amount of ram.

```
sudo fdisk -l
```

Making sure that glx and/or dri is disabled for those cards that don't need it:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

Reseating memory chips

If it is truly a Firefox issue, alternates like you have tried is one way of troubleshooting.  There are many browsers - perhaps try Epiphany-Browser and Epiphany-Extensions.  (a normal search for just Epiphany will turn up a game program.. :)

These are just some generic ideas and wish I could pin it down....

---

### Post by Scientia on 2008-06-27
filesystem check does not turn up anything.

---

