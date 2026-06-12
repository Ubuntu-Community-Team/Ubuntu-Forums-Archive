---
title: "New Kernel Kablooey"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by MonkeyWrench32 on 2005-06-08
I just got the latest 2.6.10-5-386 kernel from the update manager and now my sound and wireless network card don't work.  I've tried reinstalling the drivers for both, but no luck.  So how do I revert to the previous version of the 2.6.10-5-386 kernel?

Thanks in advance.

---

### Post by MonkeyWrench32 on 2005-06-09
[QUOTE=MonkeyWrench32]I just got the latest 2.6.10-5-386 kernel from the update manager and now my sound and wireless network card don't work.  I've tried reinstalling the drivers for both, but no luck.  So how do I revert to the previous version of the 2.6.10-5-386 kernel?

Thanks in advance.[/QUOTE]
 Bump.  Anybody?

---

### Post by N'Jal on 2005-06-09
When the machine turns on there should be an option in the grub menu to use your previous kernel. Select that then hit return, if that kernel still works then you know its a kernel problem. If so just remove then kernel version from the boot menu. Hope this helps.

---

### Post by MonkeyWrench32 on 2005-06-09
[QUOTE=N'Jal]When the machine turns on there should be an option in the grub menu to use your previous kernel. Select that then hit return, if that kernel still works then you know its a kernel problem. If so just remove then kernel version from the boot menu. Hope this helps.[/QUOTE]
 N'Jal, that is not the case because the updates that I downloaded overwrote the 2.6.10-5-386 kernel.  There's nothing in GRUB to fix this.

---

### Post by nocturn on 2005-06-09
[QUOTE=MonkeyWrench32]I just got the latest 2.6.10-5-386 kernel from the update manager and now my sound and wireless network card don't work.  I've tried reinstalling the drivers for both, but no luck.  So how do I revert to the previous version of the 2.6.10-5-386 kernel?

Thanks in advance.[/QUOTE]

I'm not on my Ubuntu box right now, so I may be a little vague.
Boot up and log in, start up synaptic.

Search for the kernel package (Called linux-image I think).
Right click on it, there should be some option that lets you pin on the previous version.

---

### Post by MonkeyWrench32 on 2005-06-09
[QUOTE=nocturn]I'm not on my Ubuntu box right now, so I may be a little vague.
Boot up and log in, start up synaptic.

Search for the kernel package (Called linux-image I think).
Right click on it, there should be some option that lets you pin on the previous version.[/QUOTE]
 Nocturn,

That did work for the downgrade, but the sound and the wireless are still not working.  I'm going to reinstall them once more and see if that will take care of it.

---

### Post by nocturn on 2005-06-09
[QUOTE=MonkeyWrench32]Nocturn,

That did work for the downgrade, but the sound and the wireless are still not working.  I'm going to reinstall them once more and see if that will take care of it.[/QUOTE]

That is strange!
At least the sound drivers should be in the kernel tree...  What soundcard do you have.

For the wireless, are you using a kernel module or ndiswrapper?

---

### Post by MonkeyWrench32 on 2005-06-09
Success!  Thank you so much!

---

### Post by MonkeyWrench32 on 2005-06-09
[QUOTE=nocturn]That is strange!
At least the sound drivers should be in the kernel tree...  What soundcard do you have.

For the wireless, are you using a kernel module or ndiswrapper?[/QUOTE]
 I have a Sony VAIO FS660/W notebook (fairly new) and I had to install the latest ALSA drivers for it to work (it wouldn't recognize in the default 1.0.8 set).  The wireless card is an Intel BG2200 and I have the 1.0.3 drivers installed (1.0.4 wouldn't work for some reason).  Both of these driver sets were installed from the source and not from packages.

---

### Post by nocturn on 2005-06-09
[QUOTE=MonkeyWrench32]I have a Sony VAIO FS660/W notebook (fairly new) and I had to install the latest ALSA drivers for it to work (it wouldn't recognize in the default 1.0.8 set).  The wireless card is an Intel BG2200 and I have the 1.0.3 drivers installed (1.0.4 wouldn't work for some reason).  Both of these driver sets were installed from the source and not from packages.[/QUOTE]

They were probably build against the kernel sources, so I guess you need to compile them again...

---

