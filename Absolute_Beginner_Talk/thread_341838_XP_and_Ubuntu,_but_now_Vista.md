---
title: "XP and Ubuntu, but now Vista?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by infernon on 2007-01-19
I am currently running a dual-boot machine with XP and Ubuntu 6.10.  I love Ubuntu, but I work as a consultant and need to support Windows.  With the release of Vista, I now have to become familiar with Vista so that I can support it.  Shed a tear for me.

Now that I must upgrade my machine, is there anything that I should be concerned about as far as the Vista upgrade overwriting the boot sector and messing up my lovely dual boot world?  If not, will GRUB still work properly and boot my Vista machine when it no longer XP?  Has anyone been down this road yet?

---

### Post by SunnyRabbiera on 2007-01-19
I havent, but I suggest you back up all your ubuntu data before upgrading to vista... much less installing any MS OS as all of them are space hogs.

---

### Post by bluefrog on 2007-01-19
easier way: install vista in vmware

James

---

### Post by bodhi.zazen on 2007-01-19
You will likely need to restore GRUB after you install vista.

Here's how:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I do not Vista, but as far as I know it cohabitates as well as XP.

---

### Post by peter_brewer on 2007-01-19
I don't think you are legally allowed to install Vista in any virtualisation environment unless you are on the Microsoft Developer Program or something similar.  Can never remember names.

---

### Post by bluefrog on 2007-01-19
yep indeed, now that you are talking of it, I may have read something about that.

---

### Post by BarfBag on 2007-01-19
As it is, XP clears the MBR when you reinstall it.  You'll definitely need to reinstall Grub afterwards.  Just be sure it doesn't formate the entire drive.

---

