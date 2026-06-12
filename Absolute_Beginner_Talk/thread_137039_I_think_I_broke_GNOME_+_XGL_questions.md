---
title: "I think I broke GNOME + XGL questions"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-02-27
Hi,

I recently followed a combination of Poofy's XGL guide and the Breezy XGL guide. While I installed Kubuntu Breezy originally, I like GNOME better now. I have since then changed /etc/X11/default-display-manager to use /usr/sbin/gdm instead of /usr/bin/kdm.

1. After getting XGL working via Poofy's "thefuture" script, I noticed something strange: newly opened windows don't appear on GNOME's taskbar (at the bottom)! I can still add and remove elements from it, but if I minimize a window, it totally disappears. This also happens when I first boot, before starting the "thefuture" script. :neutral: Is there any way to fix that?

2. With XGL running, going to System->Preferences->Windows returns this error: "Window manager 'compiz' has not registered a configuration tool." What's up with that?

3. How can I disable "show window contents while dragging"? In some applications, redrawing is painfully slow. *cough*firefox*cough*

4. Does XGL require an X11 display to already be active when it's launched, or can /usr/X11R6/bin/Xgl be run directly for a speed improvement?

5. Is this bad?

>  cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.

Does that mean my XGL and Quake 3 aren't running as fast as they possibly can? (I'm still getting insane FPS in Q3 in 1600x1200)

xorg.conf (my video card is a AGP 8x nVidia GeForce FX 5600 256 megs)
> Section "Device"
        Identifier      "NVIDIA Corporation NV31 [GeForce FX 5600]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "NvAGP" "1"
        Option          "RenderAccel"   "true"
        Option          "AllowGLXWithComposite" "true"
EndSection

Sorry about all the questions, I know relatively little about how displays in linux work, but I'm learning. :D

---

### Post by Kurt` on 2006-02-27
[QUOTE=Kurt`]1. After getting XGL working via Poofy's "thefuture" script, I noticed something strange: newly opened windows don't appear on GNOME's taskbar (at the bottom)! I can still add and remove elements from it, but if I minimize a window, it totally disappears. This also happens when I first boot, before starting the "thefuture" script. :neutral: Is there any way to fix that?[/QUOTE]

Ok, that one was pretty simple to fix. Apparently, the lower taskbar was somehow completely cleared off (I never actually touched it to my knowledge), and I didn't realize in the Right-click->Add to panel menu that you could scroll down. ;)

---

