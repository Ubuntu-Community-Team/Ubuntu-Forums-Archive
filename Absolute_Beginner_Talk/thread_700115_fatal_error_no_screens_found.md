---
title: "fatal error no screens found"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by theman1389 on 2008-02-18
I recently used Envy to install the driver for my NVIDIA  graphics card.  When I rebooted afterwards, there was no sidplay on my laptop screen once I got to the login screen, but I could plug it in to an external monitor and see it. So, I went to the restricted drivers menu, disabled the NVIDIA driver, and restarted my laptop. When I did, it gave me a message about the X server not bein properly installed, which ended in something like "fatal error no screens found"

Please help me restore my laptop.

---

### Post by mikeyphi on 2008-02-18
> **theman1389 said:**
> I recently used Envy to install the driver for my NVIDIA  graphics card.  When I rebooted afterwards, there was no sidplay on my laptop screen once I got to the login screen, but I could plug it in to an external monitor and see it. So, I went to the restricted drivers menu, disabled the NVIDIA driver, and restarted my laptop. When I did, it gave me a message about the X server not bein properly installed, which ended in something like "fatal error no screens found"

Please help me restore my laptop.

Boot into the recovery mode...eventually you will be presented with the Command prompt:
enter the following
dpkg-reconfigure xserver-xorg

There will be several pages of text with a question at the end of each section - accept the default answers unless you know better!
Reboot into normal mode, use the System/Administration/Restricted Drivers Manager to reset the video driver - if necessary
Also - if necessary - use System/Administration/Screens & Graphics to set the correct resolution etc.

---

