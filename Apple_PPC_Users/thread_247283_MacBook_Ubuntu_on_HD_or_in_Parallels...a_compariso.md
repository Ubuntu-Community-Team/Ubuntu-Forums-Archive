---
title: "MacBook: Ubuntu on HD or in Parallels...a comparison."
date: 2006-08-30
forum: Apple PPC Users
---

### Post by hajk on 2006-08-30
I have in the past few weeks installed Ubuntu Dapper both directly to the HD of my MacBook (using Boot Camp and rEFIt), and in a Parallels VM running under Mac OS X. Apart from the installation procedures, which differ markedly (with the direct HD installation being much the more complicated), how do these implementations compare once the installation is done?

1. Ubuntu runs slower in the Parallels VM, both because of the additional software layer between it and the hardware and because the Parallels VM recognizes only a single core of the Core Duo processor. The next version of Parallels (due out by the end of 2006) will support both cores.

2. High operating temperature when running Ubuntu (whether in Parallels or on the HD) is no longer an issue after the recent (18 August 2006) firmware update by Apple.

3. More features of the Apple keyboard are available in the Parallels VM, among which are: two-finger scrolling with the touchpad; the special function keys F1 - F5 for screen/sound; the F6 NumLock key; the F9 and F11 display dimming/clearing keys; and the F12 Dashboard key. Most of this functionality will either not work with Ubuntu on the HD, or requires additional (non-obvious) configuration.
                   
4. The VM has access to the OS X wireless (AirPort) interface by means of a sub-LAN with NAT (or alternatively a dedicated wired Ethernet connection). Getting the ath0 wireless interface to activate in Ubuntu installed directly on the HD is a painful procedure,to be repeated everytime you boot (caused by the problematic madwifi-ng drivers).

5. No need to run a mail programme (like Evolution) in the Ubuntu VM, because the OS X mail programme keeps running while using the VM, and it will chime when new mail has arrived.

6. No need either to worry much about installing multimedia codecs, since the underlying OS X can play multimedia sources much better than Ubuntu Linux anyway, with a more elegant interface -- in fact using the strenghts of both OS'es at the same time.

7. Easy switching between the Ubuntu VM and OS X obviates the need to shut down and reboot to go from one OS to the other; the VM can also be suspended to HD, something that does not work when installing Ubuntu directly to the HD (nor does sleep).

8. The Parallels VM supports only SVGA (VESA) graphics right now, so no accelarated graphics; wheras Ubuntu on the HD is capable of running Xgl/Aiglx/Compiz. The next version of Parallels will have support for OpenGL, though.

So, there you have it, both pros and cons. FWIW, I have now removed the HD version of Ubuntu and reverted the whole HD to Mac OS X, using Parallels to run Ubuntu in a VM whenever I need to do some work (mostly programming) that can't be done well in OS X. Speed is not much of an issue for me, since I still have my AMD Opteron desktop machine that's a 100% amd64 Ubuntu speed monster.

See my sig for a link to my HOWTOs on the above issues.

---

### Post by hajk on 2006-09-01
Updated info, link to HOWTOs added in sig. Enjoy!

---

### Post by goneskiing on 2006-09-01
How do you get/install Apple firmware update ?

---

### Post by hajk on 2006-09-01
> **goneskiing said:**
> How do you get/install Apple firmware update ?

Click on Finder, then on the blue Apple logo, then on Software update... or
[http://www.apple.com/support/downloads/macbooksmcfirmwareupdate.html]("http://www.apple.com/support/downloads/macbooksmcfirmwareupdate.html")

---

### Post by mjukr on 2006-10-07
Thanks for posting your very helpful guide, hajk!

---

