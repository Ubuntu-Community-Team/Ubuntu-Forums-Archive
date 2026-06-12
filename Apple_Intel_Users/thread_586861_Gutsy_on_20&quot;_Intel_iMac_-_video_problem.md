---
title: "Gutsy on 20&quot; Intel iMac - video problem"
date: 2007-10-22
forum: Apple Intel Users
---

### Post by ward83 on 2007-10-22
I'm having some trouble getting the video working correctly on my 20" Intel iMac in gutsy. It is barely useable right now, every time something on the screen changes (like moving a window), it's painfully slow. The video card is detected as a Radeon Mobility X1600, which driver should I be using? Any help would be much appreciated.

---

### Post by cyberdork33 on 2007-10-22
> **ward83 said:**
> I'm having some trouble getting the video working correctly on my 20" Intel iMac in gutsy. It is barely useable right now, every time something on the screen changes (like moving a window), it's painfully slow. The video card is detected as a Radeon Mobility X1600, which driver should I be using? Any help would be much appreciated.

Go into the restricted drivers manager and be sure to use the proprietary ATI driver.

---

### Post by ward83 on 2007-10-22
I have the restricted driver enabled, but uninstalling and reinstalling fixed the slow screen render problem. After inspecting the xorg.conf file, I found that disabling Xinerama fixes the problem. I thought 7.10 didn't use Xinerama, but when I use the Screens & Graphics utility to set up my secondary screen, it adds a Xinerama line to the xorg.conf file. Any ideas on how to set up a secondary monitory in Gutsy?

---

