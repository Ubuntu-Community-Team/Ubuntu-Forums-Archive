---
title: "Multiple Monitor works as root, but not as myself"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Bif Powell on 2008-03-03
Newly installed Ubuntu Gutsy on AMD64
[LIST]
[*]NVidia 8800
[*]-LCD Viewsonic DVI interface
[*]-LCD Dell on CRT interface
[*]Nvidia 5200
[*]-LCD Samsung on CRT interfaceb
[/LIST]

The installation default only had the one Samsung working at native resolution, 1280x1024

I downloaded and ran Envy.  I was able to move around my displays and enable them.  When I rebooted, the system never showed me anything on my screen at all.  The Samsung danced between digital/analog a few times, but then ALL the displays ultimately stayed black - even the Samsung which had previously worked.  It seems like the machine is running properly; at some point the disk activity trailed off, the num/caps lock keys work, but I never get any display.  I have let it sit like this for 20 minutes or so with no change.

So I reboot (power-cycle) and select recovery mode.  I get to the command-line and type startx.  X launches perfectly, my screens are displayed according to my configuration options in Envy (even which is primary display) and all the displays seems to be working at their proper resolution.

I go into nvidia-settings and adjust things, but for the most part all looks as it should.  I save the configuration and exit.

When I reboot normally, I'm back to nothing being displayed on my screens.  If I select recovery and do startx, I get the behavior described above.  Seems like it's obviously some kind of permissions issue, but I have no idea where to even begin.

Any guidance on this matter appreciated!  Thank you!

---

### Post by PapaNerd on 2008-03-04
Two debugging ideas (not sure either will work, but can't do much harm):
1. Make sure the "Modes" entries for your monitors in the /etc/X11/xorg.conf file do not exceed 1280x1024.
2. Add your non-admin user into the "video" group in the /etc/group file.

---

