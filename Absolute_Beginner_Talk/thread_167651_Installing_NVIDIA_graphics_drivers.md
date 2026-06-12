---
title: "Installing NVIDIA graphics drivers"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by j0eb0b on 2006-04-28
I just downloaded the latest Nvidia graphics drivers for a FX 5500 graphics card.  The package that downloaded to my desktop was "nvidia-linux-x86-1.0-8756-pkg1.run" .  The instructions with the package tell me to run from terminal "sh nvidia0linux-x.86-1.0-8756-pkg1.run".  This results in a file/directory not found.  How do I install these graphics drivers?

Thanks,
joe

---

### Post by OffHand on 2006-04-28
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

### Post by bluevoodoo1 on 2006-04-28
Check out method 2 here...
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

if the file is on your desktop, you have to change directories (cd) there first...
cd ~/Desktop

then your... sh nvidia0linux-x.86-1.0-8756-pkg1.run    ...command will work. (first you have to drop to a command line.... ctrl+alt+F1)


edit: forgot the last line.

---

### Post by gingermark on 2006-04-28
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074) should explain everything. Will depend on which version of gcc are available for Hoary though (hopefully someone else can tell you that).

---

### Post by j0eb0b on 2006-04-30
Thanks for the good advice and links.  I was able to update my drivers (via Synaptic, not from the nvidia website download).  Question now is this, where is the Nvidia control panel, it does not show up in the applications area of unbuntu desktop.  An nividia splash screen loads at boot time so i apparently loaded something.

Thanks,
Joe

---

### Post by bluevoodoo1 on 2006-04-30
[QUOTE=j0eb0b]Thanks for the good advice and links.  I was able to update my drivers (via Synaptic, not from the nvidia website download).  Question now is this, where is the Nvidia control panel, it does not show up in the applications area of unbuntu desktop.  An nividia splash screen loads at boot time so i apparently loaded something.

Thanks,
Joe[/QUOTE]

try ...

nvidia-settings

---

### Post by j0eb0b on 2006-05-02
I'm sorry to be so dense.  I found the package nividia-settings and installed it.  Where is it?  Do I have to call it from terminal?

Thanks,
joe

---

### Post by tseliot on 2006-05-02
[QUOTE=j0eb0b]I'm sorry to be so dense.  I found the package nividia-settings and installed it.  Where is it?  Do I have to call it from terminal?

Thanks,
joe[/QUOTE]
Click on the following menus:
applications/System tools/Nvidia Xserver Settings

If you can't find it, I suppose it's because you skipped this step in Method 1 of my guide:
```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
OR (if you use KDE)
sudo kate /usr/share/applications/NVIDIA-Settings.desktop

Insert the following lines into the new file:

Code:

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;
```

---

