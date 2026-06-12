---
title: "Display Options - Save to X Configuration?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by OhioYJ on 2007-05-16
In my Nvidia driver panel I have to setup my dual monitors everytime I reboot. When I first turn my PC on I have to enable the second monitor in the Nvidia control panel. (I do have two video cards installed in SLI, and I know the second card just sits idle when using dual monitors)

My question being, why doesn't the "Save to X Configuration File" button in the Nvidia control panel work? I click save but it doesn't seem to save, because once I reboot I'm back to a single monitor?

---

### Post by netwerx on 2007-05-16
if your nvidia utility can run as a program, try running it from a command line with sudo.  perhaps the way you have it running, it doesn't have permission to change the settings in the file? 

Just a guess.  I have a ATI card myself.

---

### Post by nicepants on 2007-05-16
> **netwerx said:**
> if your nvidia utility can run as a program, try running it from a command line with sudo.  perhaps the way you have it running, it doesn't have permission to change the settings in the file? 

word. when you run it as a user, it defaults to saving your config in ~/ and complains about not being able to back up your original .conf. just ```
sudo nvidia-settings 
```and everything should get saved.

you can ```
cat /etc/X11/xorg.conf
``` to check it out, the one nvidia-settings generates is commented as such at the beginning of the file.

---

### Post by OhioYJ on 2007-05-16
> sudo nvidia-settings

That right there worked great, Thanks NicePants!

---

