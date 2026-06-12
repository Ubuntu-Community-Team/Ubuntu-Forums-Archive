---
title: "Mysterious hanging and then some.."
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by VoiceOvGod on 2006-04-13
I have Breezy 5.10 for my amd64 3400+ installed, and every time that I lock the workstation, it freezes (Unsure how long it takes before it actually does freeze). When I do a hard shutdown and reboot (in an attempt to recover the logs) I get an error stating that the keyboard is not detected. After I manually remove and replace the keyboard, it will load quickly, but, once GNOME starts, it runs rather slowly. It takes a few minutes to load a browser window, and it took several more minutes to load the log viewer.

I have only installed the base system for workstations, all updates, the nvidia driver that came in the package manager, and firestarter. Firestarter was installed after the first time it hung up.

I have not been able to check the logs yet, so I don't know what the cause is. 

As a relatively new user of Linux, I have no idea where to actually start looking to properly troubleshoot and then resolve this issue. Any assistance would be greatly appreciated.

*edit* X-posting to AMD-64 forum.

*Edit* : Trying first with different keyboard. Current one is an old one (having to use adapter to convert to PS2)

---

### Post by VoiceOvGod on 2006-04-15
Update: Swapped keyboard. Still produced same results.

Checked logs, unsure of what I should be looking for in logs, did not see anything that seemed to raise a mental flag.

---

### Post by VoiceOvGod on 2006-04-15
Is it possible that this could be related to the Nvidia drivers? I only used the ones from the package manager. I have not used the drivers provided by nvidia.

---

### Post by taurus on 2006-04-15
If you thing it's nvidia driver that you installed, you can test it out.  Open a terminal and edit /etc/X11/xorg.conf and replace the "nvidia" with "vesa" driver...
```

Driver                    "vesa"

```
Now, reboot or restart X and see if your machine still freezes when you lock it!

---

### Post by VoiceOvGod on 2006-04-18
That worked. Thanks!

---

