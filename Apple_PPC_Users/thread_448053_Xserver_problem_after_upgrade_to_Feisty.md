---
title: "Xserver problem after upgrade to Feisty"
date: 2007-05-18
forum: Apple PPC Users
---

### Post by pellsen on 2007-05-18
Hello!

I'm using a Dual-G4 PowerMac (mirror drive door). I used OS X 10.2.8 and ubuntu Edgy Eft in a dual boot setup, and it worked just fine, although I had to use the terminal in ubuntu to get the maximum screen resolution (ATI Radeon + Samsung Syncmaster).

Today, I tried to upgrade to Feisty Fawn. Everything seemed to work fine. But, after I restarted, first the ubuntu startup screen (with the orange status bar) appeared, and then the screen went in text mode again and I was told that the Xserver could not be started and that it's probably not configured right. I looked at the report, but I'm totally new to everything Linux, so I didn't really understand it. I'd guess that this has got something  to do with my video card, as there were some minor problems with it in Edgy Eft (see above). But I'm not sure.

Can anybody help me?

Thanks,
Pellsen.

---

### Post by didjital1984 on 2007-05-21
[This]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/93271") is your bug.

I had this problem too, on a similar setup. A temporary solution is to boot using the kernel argument "video=ofonly." This should allow you to startup almost normally.

The best "solution" right now is to downgrade your xserver-xorg-video-ati package to the latest version from edgy. Once X fails to load and kicks you back to the command line, login and make sure you have the edgy repository listed in /etc/apt/sources.list, along with the feisty ones. The line should look something like this:

```
deb http://archive.ubuntu.com/ubuntu/ edgy main
```

Then do "sudo apt-get update" to update your package lists. Once that completes, type "sudo apt-get install xserver-xorg-video-ati/edgy". Once you have successfully downgraded the package, you should be able to start up normally.

The next thing you'll want to do is use synaptic to lock that version in, so you don't automatically get upgraded to the non-working version. Open up synaptic and search for "xserver-xorg-video-ati" to locate that package. Select it, then choose "Lock version" from the package menu. You'll want to keep it locked until you know the bug is fixed.

Hope this info helps!

---

### Post by pellsen on 2007-05-23
> **didjital1984 said:**
> Hope this info helps!

It did! Thank you very much!

p.

---

