---
title: "Multiple problems with Intrepid upgrade"
date: 2008-11-28
forum: Apple Hardware Users
---

### Post by zmjjmz on 2008-11-28
Let me go through the list:
Problem 1) GNOME screws up X, or something like that. Whenever I try to go to a GNOME-anything session, X will show weird lines and then turn purple, shutoff the screen and then go back to GDM.
[http://pastebin.com/f33932fa](http://pastebin.com/f33932fa) is the Xorg.0.log.old from when it happened.

Problem 1 isn't as bad as Problem 2, because I have an Xfce session lying around that I can use.

Problem 2) Wifi hardly works after resume from suspend. 
Wifi works fine after I reboot it, but after i wake it up from suspend the range goes from normal (don't really know how much that is) to near nothing. 
nm-applet reports one or two networks, neither of which are mine or I can connect to, and ceni reports -no values- and iwlist just says no scan results.

The computer is a 2006 MacBook, 1.8GHz Core Duo, Intel GMA950, and Atheros Communications Inc. AR242x wireless adapter (just reading what lspci says about it.)


In addition, the fan died (hardware problem) so it shuts off when it overheats.

---

### Post by cyberdork33 on 2008-11-30
upgrades tend to go badly. I would suggest a full install.

Please check the documentation for your mac. You can determine your specific mac version and the documentation for it in the "before you post" link in my signature.

---

### Post by zmjjmz on 2008-11-30
> **cyberdork33 said:**
> upgrades tend to go badly. I would suggest a full install.

Please check the documentation for your mac. You can determine your specific mac version and the documentation for it in the "before you post" link in my signature.

Well I just backed up /home so I can send it to the Apple people, so I'll probably end up doing that anyways.

---

### Post by joker77 on 2008-11-30
Consider making a live cd and booting with it. If things are fine then, a fresh install (WITHOUT RESTORING the . files/folders, except maybe .mozilla/ and .evolution/ and any other you need to preserve) may work well.

---

### Post by zmjjmz on 2008-11-30
> **joker77 said:**
> Consider making a live cd and booting with it. If things are fine then, a fresh install (WITHOUT RESTORING the . files/folders, except maybe .mozilla/ and .evolution/ and any other you need to preserve) may work well.

Unfortunately it is unable to boot from CDs too (hardware problem).
I'll have to wait until I get it back from the Apple store. I might just do an entirely fresh start, only copying over the necessary files.

---

