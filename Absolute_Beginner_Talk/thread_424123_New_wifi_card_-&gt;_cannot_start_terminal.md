---
title: "New wifi card -&gt; cannot start terminal"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-04-26
I replaced the old broadcom wifi card in my laptop with a new intel pro wireless card. Then I started up the laptop and logged into Ubuntu.

Wifi is working, but I noticed that I can't start the terminal. I click on the terminal icon, it gives me the round clock thingy icon but nothing happens.

Would really appreciate some help to find out what's wrong.

---

### Post by annda on 2007-04-26
is it only the terminal? or are there any other apps not starting?

try the terminal with ALT+F2 and typing xterm.

i've had a similar problem with a malconfigured nvidia driver and glx problems. to see if it is the same, go to console (xterm or CTR+ALT+F1 - you can go back with CTR+ALT+F7) and type glxinfo. see if you have any errors there.

---

### Post by PartisanEntity on 2007-04-26
Interesting, I disabled Xinerama and went back to having two seperate X displays then restarted X server and now the terminal will load.

---

### Post by PartisanEntity on 2007-04-26
> **annda said:**
> is it only the terminal? or are there any other apps not starting?.

Seems to be the terminal only

> **annda said:**
> try the terminal with ALT+F2 and typing xterm..

This worked, it loaded a terminal window with black background.

> **annda said:**
> i've had a similar problem with a malconfigured nvidia driver and glx problems. to see if it is the same, go to console (xterm or CTR+ALT+F1 - you can go back with CTR+ALT+F7) and type glxinfo. see if you have any errors there.

There were no errors for glxinfo.

I tried re-enabling Xinerama and again the terminal would not load. Ever since replacing my wifi card the terminal wont load with Xinerama enabled.

---

### Post by PartisanEntity on 2007-04-26
Okay looks like it is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232)

Strangely it only showed up by me after I replaced my wifi card today.

---

### Post by annda on 2007-04-26
good that you are so thorough. i've had this with gentoo. same symptopms, slightly different solution, but we know nvidia is to blame ;-)

intel's wifi uses the restricted modules package in ubuntu, so maybe that is what triggered the problem...

---

