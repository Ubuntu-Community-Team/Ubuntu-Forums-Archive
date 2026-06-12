---
title: "HP dv6t wireless hardware switch"
date: 2011-11-21
forum: Any Other OS
---

### Post by Dans564 on 2011-11-21
Hey guys I have a 2011 HP dv6t dualbooting with Windows 7 Ultimate and Linux Mint 11 64bit.  My problem is this, randomly for no reason the wireless disconnected and now says that the hardware switch is disabled.  Here is the problem, even when i push the wireless button on the keyboard it stays turned off.  So I booted into widows and it says a similar error!  I cant just push the button and turn it on for some reason, even in windows.  If anyone has any ideas on how to fix this that would be great!

---

### Post by Perfect Storm on 2011-11-21
Moved to Other OS/Distro Talk.

---

### Post by Sonsum on 2011-11-21
> **Dans564 said:**
> Hey guys I have a 2011 HP dv6t dualbooting with Windows 7 Ultimate and Linux Mint 11 64bit.  My problem is this, randomly for no reason the wireless disconnected and now says that the hardware switch is disabled.  Here is the problem, even when i push the wireless button on the keyboard it stays turned off.  So I booted into widows and it says a similar error!  I cant just push the button and turn it on for some reason, even in windows.  If anyone has any ideas on how to fix this that would be great!

I've had this problem on an HP G62. For me, to re-enable the wireless, you have to be in windows. Click the little wireless pop-up that shows when you press the hardware wireless switch. It should have an option in the following settings to re-enable to wireless. 

I just don't turn off the wireless anymore.

---

### Post by Dans564 on 2011-11-21
turned out a little "sudo rfkill unblock wifi" re-enabled wifi in both windows and mint.

---

### Post by Sonsum on 2011-11-22
> **Dans564 said:**
> turned out a little "sudo rkill unblock wifi" re-enabled wifi in both windows and mint.

*writes down* This looks useful! Thanks!

---

