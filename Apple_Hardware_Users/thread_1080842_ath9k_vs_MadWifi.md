---
title: "ath9k vs MadWifi"
date: 2009-02-25
forum: Apple Hardware Users
---

### Post by tiagobt on 2009-02-25
I've just installed Ubuntu 8.10 in a 2nd generation MacBook and the WiFi connection worked out-of-the-box, since the new kernel (2.6.27-11) comes with ath9k. However, I noticed that the signal strength and stability are significantly lower than the ones I had with Ubuntu 8.04 and MadWifi. For instance, I'm no longer able to connect from my bedroom, which worked relatively well with MadWifi.

Did anyone notice the same? Is this a known issue? Any workarounds?

Thanks a lot,
Tiago

---

### Post by Rog-Mahal on 2009-02-25
Hmm, I also have a second gen. macbook and had the opposite experience. Madwifi was much more buggy, and I had a problem where I was unable to use the current revision and had to use an old snapshot. I suppose you could unload the ath9k driver, download and compile the madwifi, load it, and then see if you see a difference.

---

### Post by cyberdork33 on 2009-02-25
there were some speed issues that have been recently addressed. Have you tried the Jaunty alpha?

---

### Post by Twitch6000 on 2009-02-25
I am not sure if it is just me,but I always seem to have more trouble with madwifi then good....

It might because of the distros or because of the times I tried it,but either way I would suggest either sticking with what you got or use the windows driver.

---

### Post by tiagobt on 2009-02-25
> **cyberdork33 said:**
> there were some speed issues that have been recently addressed. Have you tried the Jaunty alpha?

I haven't. Is there anyway I can test the new driver in Intrepid?

---

### Post by cyberdork33 on 2009-02-25
> **tiagobt said:**
> I haven't. Is there anyway I can test the new driver in Intrepid?
well, I don't even know if it is in jaunty, but jaunty has a newer kernel. You can just boot the livecd and the wifi should work from there...

It looks like the update was actually in the updates at some time:
[https://bugs.launchpad.net/bugs/297965](https://bugs.launchpad.net/bugs/297965)

---

### Post by Romu on 2009-02-26
Yes, I'm facing similars issues.

When Intrepid was released, I downgraded back my Macbook Pro 2G to Hardy because of the sssllllloooooowwwwwwwww connection speed (about 10% of the speed with madwifi on Hardy).

I created some bug reports in Launchpad and Linux Kernel, and the problem as been adressed.

But the current situation is far from perfect, the speed seems ok, but the connection is awfully unstable, so I created a bug in Launchpad and Linux Kernel about that issue.

And, I still can't watch TV through my internet connection. Is there a way to use madwifi on Intrepid?

Is Jaunty Alpha stable enough to replace Intrepid and being my default OS?

---

### Post by cyberdork33 on 2009-02-26
> **Romu said:**
> And, I still can't watch TV through my internet connection. Is there a way to use madwifi on Intrepid?yes compile it, but that can have better / worse results.

> **Romu said:**
> Is Jaunty Alpha stable enough to replace Intrepid and being my default OS?I wouldn't do the full replacement yet, but unless anyone out there tests it now, it could end up being completely incompatible on release day with a whole new slew of bugs.

---

### Post by tiagobt on 2009-02-27
I've tried to boot the live CD for Ubuntu Jaunty Alpha 5, but didn't have much luck. First, the Ubuntu logo screen appeared and the loading bar kept moving for a pretty long time (at least 5 minutes). Then, some text output showed up, but most of it was "SQUASHFS error" or "buffer I/O error". Some of the error messages I can remember were "unable to read page," "unable to read sector," and "unable to read block." Those error messages kept showing up for a long time as well, alternated by a few regular boot messages. After that, a "fail" message appeared briefly and the screen just froze. I had to press the power button to turn the notebook off. To make a long story short, I didn't get close to testing the new ath9k driver... Is there anything else I could try?

Thanks again,
Tiago

---

### Post by cyberdork33 on 2009-02-28
> **tiagobt said:**
> I've tried to boot the live CD for Ubuntu Jaunty Alpha 5, but didn't have much luck. First, the Ubuntu logo screen appeared and the loading bar kept moving for a pretty long time (at least 5 minutes). Then, some text output showed up, but most of it was "SQUASHFS error" or "buffer I/O error". Some of the error messages I can remember were "unable to read page," "unable to read sector," and "unable to read block." Those error messages kept showing up for a long time as well, alternated by a few regular boot messages. After that, a "fail" message appeared briefly and the screen just froze. I had to press the power button to turn the notebook off. To make a long story short, I didn't get close to testing the new ath9k driver... Is there anything else I could try?

Thanks again,
Tiago
sounds like it may have been a bad burn / download. Did you verify the disc?

---

### Post by tiagobt on 2009-03-01
> **cyberdork33 said:**
> sounds like it may have been a bad burn / download. Did you verify the disc?

You're right. My download was fine (according to the MD5 sum), but K3b burnt me two bad CDs in a row :mad:. I think I've finally got a good CD (at least the command "md5sum -c md5sum.txt" reports that all files are OK).

I tried to boot the new live CD and the loading process was much faster this time. Besides, no error messages were displayed. GDM also loaded properly, but after the login, a black screen appeared and nothing else happened... The mouse works, but the system seems irresponsive to all commands (I even tried Ctrl + Alt + Backspace, but nothing happens).

Any other choices? Is there a way to test the Wi-Fi driver using the command line?

Tiago

---

### Post by cyberdork33 on 2009-03-01
> **tiagobt said:**
> You're right. My download was fine (according to the MD5 sum), but K3b burnt me two bad CDs in a row :mad:. I think I've finally got a good CD (at least the command "md5sum -c md5sum.txt" reports that all files are OK).

I tried to boot the new live CD and the loading process was much faster this time. Besides, no error messages were displayed. GDM also loaded properly, but after the login, a black screen appeared and nothing else happened... The mouse works, but the system seems irresponsive to all commands (I even tried Ctrl + Alt + Backspace, but nothing happens).

Any other choices? Is there a way to test the Wi-Fi driver using the command line?

Tiago
there is an option in the boot menu to verify the disc. You should try that. Burning very Slowly will help you get a good bootable disc.

It should boot to the desktop fine on your hardware, so I don't know what the issue might be. you can use 'iwconfig' on the commandline to control the wireless card. (and at least see if the driver is loaded and the hardware is listed there.)

---

