---
title: "Display shows bars of color"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Quincy2you on 2006-02-05
When I installed Ubuntu it ended with some colorfull bars.
Keyboard doesn't do anything except numlock light.
I reboot hard and same problem.
I can get to prompt in recovery mode but I have absolutely no idea what to do in there.

---

### Post by Protex on 2006-02-05
I had a similar problem.

I needed to install the nVidia drivers. Do you have a nVidia card?

---

### Post by Quincy2you on 2006-02-05
[QUOTE=Protex]I had a similar problem.

I needed to install the nVidia drivers. Do you have a nVidia card?[/QUOTE]
Yeah i do actually.

I tried this command i found @ hardware support/visual:install latest nvidia drivers method 1
[http://ubuntuforums.org/showthread.php?t=75074:](http://ubuntuforums.org/showthread.php?t=75074:)

sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules- 'uname -r'

I get this message that he couldn't find linux-restricted-modules, is this the right command to install the drivers?

I have a 6600 GT.

---

### Post by Protex on 2006-02-05
I think so yes.

I have a 6600GT as well.

Try typing 'uname -r'. That will give you your kernel version. Then do the command above, replacing 'uname -r' with the version that the command prompt throws back at you.

---

