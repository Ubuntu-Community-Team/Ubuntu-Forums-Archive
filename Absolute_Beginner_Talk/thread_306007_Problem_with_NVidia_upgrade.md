---
title: "Problem with NVidia upgrade"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by rek on 2006-11-24
I am new to Ubunto Dapper. I attempted to update my NVidia drivers for my 7300GT card following these [instructions]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper").

After completing the update, I hit the CTRL+ALT+BACKSPACE and everything seems fine with the upgrade, including the NVidia splash screen.

The problem occurs when I reboot. I can't get back into X. The following is my log file:

---

### Post by Bachstelze on 2006-11-24
Please paste your xorg.conf as well. In case you don't know, it's in /etc/X11 (mark the capital X).

---

### Post by rek on 2006-11-24
Sorry about not uploading it initially. 

Here it is...

---

### Post by Bachstelze on 2006-11-24
Nothing wrong here as far as I can tell... Maybe use dpkg -l to make sure nvidia-glx and the restricted-modules matching your kernel are still installed.

Or you could also remove them and try installing from the official nvidia installer, I've found it to be less buggy sometimes.

---

### Post by rek on 2006-11-24
I used the official NVidia installer and had the same issues. I am using an AMD64 system and kernel. Maybe theres some bug in the AMD64 version. Thanks for reviewing my config and log!

The interesting thing is that it did work after initially restarting the Xserver, but not after reboot.

---

### Post by Bachstelze on 2006-11-24
If you installed form the official nvidia installer, be sure you removed linux-restricted-modules and nvidia-glx !

---

### Post by SlySmiles on 2006-11-24
> **HymnToLife said:**
> be sure you removed linux-restricted-modules!

When I attempt this synaptic says it has as a dependency linux-386. Surely that doesn't want to be removed as well ???

My current problem is this :

I've changed my card from ATI to nVidia, and spent a few hours installing the offical nVidia drivers from the nVidia website (I was getting nothing but a black screen until I realised my output was going to the turned off projector). Now when I boot I get cannot start X server, the log says bad version. When I recompile the kernel module everything works correctly (hardware acceleration, X etc), but on each reboot I get the same symptom.
I'm currently trying to remove the installed packages and try again, but get the problem of dependencies.

This is on 386 kernel under edgy...

---

### Post by rek on 2006-11-24
HymnToLife, thanks for your suggestions! I made sure that I removed the 2 modules that you suggested and then the NVidia installer worked fine. I am up and running with up-to-date drivers.

---

