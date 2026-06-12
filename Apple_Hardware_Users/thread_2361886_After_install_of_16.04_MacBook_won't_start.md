---
title: "After install of 16.04 MacBook won't start"
date: 2017-05-21
forum: Apple Hardware Users
---

### Post by brett7481 on 2017-05-21
I did a clean install on a new SSD of 16.04 on my old MacBook A1181 (1,1). Everything went fine, except when I use Ubuntu to shut down the computer... then it shuts downs but won't restart. Eventually it will turn on, no idea why or what caused it to suddenly work. Once it's running again, it runs great, Until I shut it down again...

Any thoughts?

---

### Post by deadflowr on 2017-05-22
*Moved to **Apple Hardware Users ***

---

### Post by brett7481 on 2017-05-23
OK, a bit more info.

If I swap out the hard rice for the old Mac OSX one... works fine.

When I get it to start, still randomly with Ubuntu, the power off option and suspend options behave oddly. Suspend just doesn't work at all, and when I click power off it just basically logs me off and I have to click power off again from the sign-on screen.

Also, the power button doesn't seem to work. I have it set to power off when pressed, but nothing happens if you press it. I tried switching to suspend, still nothing.

The most successful way of turning it on is having the battery out and holding down the power buttton, remove magcord while holding, place magcord back while holding, and then it starts... sometimes without pressing the power button again.

I installed the Mac 32-bit 16.04 flavor.

Any thoughts at all?

---

### Post by kevin160 on 2017-06-02
Sounds like a PRAM issue to me.  Have you "blessed" your boot loader?  

[Blessing rEFInd]("http://www.rodsbooks.com/refind/installing.html#osx")

If you've done that, I've definitely seen a PRAM reset speed up boot times on macs.  I'm reluctant to tell you to just reset your PRAM (CMD-OPT-P-R on boot), though.  I'm not completely sure that you won't lose your ability to boot linux,  depeding on how you have it set up.  Definitely have a rEFInd or SuperGrub2 rescue disk handy.

As for the power issue, yeah, I'm not a big fan of desktop window managers doing the power thing.  Whenever I install ubuntu, I move the etc/acpi/powerbtn.sh file aside and replace it with

```
#!/bin/sh
/sbin/shutdown -h now "Power button pressed"
```

A simple tap on the power button should give you a clean power-off shutdown with no prompts.  Of course, now you have to be careful about bumping it accidentally because you won't be prompted to save documents, etc.

---

