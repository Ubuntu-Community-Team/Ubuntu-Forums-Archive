---
title: "FYI: Wireless broken in 2.6.24-16"
date: 2008-04-17
forum: Apple Intel Users
---

### Post by arijarot on 2008-04-17
[http://ubuntuforums.org/showthread.php?t=757325](http://ubuntuforums.org/showthread.php?t=757325)

[https://bugs.launchpad.net/ubuntu/+bug/218892](https://bugs.launchpad.net/ubuntu/+bug/218892)

---

### Post by cyberdork33 on 2008-04-17
if they updated the atheros code, then it may have removed support for your chipset. madwifi has been in the process of changing much of their code and have left out support for the chipset used in Macs. The older code works though.

Still a bug that should be addressed though

Have you tried compiling the madwifi snapshot?
[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

---

### Post by arijarot on 2008-04-18
> **cyberdork33 said:**
> if they updated the atheros code, then it may have removed support for your chipset. madwifi has been in the process of changing much of their code and have left out support for the chipset used in Macs. The older code works though.

Still a bug that should be addressed though

Have you tried compiling the madwifi snapshot?
[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

I have not tried to compile madwifi as I'm using kernel 2.6.24-15 and lower, which all have working wifi.

---

### Post by russo.mic on 2008-04-19
SO CLOSE!!!

I broke down and installed Ubuntu Remix 8.04 64 bit tonight, and the latest madwifi snapshot allows me to view all of the networks around me, but it always stops at 28%, activating hardware.  Any ideas?

NDISWrapper seems to be a bust.
Macbook Pro C2D
Atheros Card

Russo

---

### Post by ronocdh on 2008-04-19
ndiswrapper has always worked for me, I just feel so dirty using it. MadWifi works, but ugh, I hate recompiling after every kernel change. Also, the MWF drivers are considerably weaker than even ndiswrapper ones, so I don't get reception in some places where I generally would in OSX.

---

### Post by FlamingLips on 2008-04-19
Why would new versions remove support for previously supported machines?

---

### Post by arijarot on 2008-04-19
> **FlamingLips said:**
> Why would new versions remove support for previously supported machines?

They wouldn't; it's a bug.

---

### Post by cyberdork33 on 2008-04-19
> **FlamingLips said:**
> Why would new versions remove support for previously supported machines?
It's not quite like that. Usually it is an accident because of changes (bug) or something like what madwifi is doing, they are completely rewritting the driver to be completely open. They can only work on so much of it at once.

---

### Post by arijarot on 2008-04-24
FYI

A clean install from live cd solved this problem. Wireless works in 2.6.24-16-generic.

---

