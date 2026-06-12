---
title: "Installing .bin files"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by patanjali on 2006-04-14
I have a copy of RealPlayer10GOLD.bin in my "Downloads" directory.  Could someone please tell me how I can install it?

Thanks in advance 

Patanjali :confused:

---

### Post by gingermark on 2006-04-14
I recommend you use the .deb package that is provided here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Much easier!

---

### Post by aysiu on 2006-04-14
Maybe [this](https://wiki.ubuntu.com/RestrictedFormats#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b) might help?

---

### Post by patanjali on 2006-04-14
The problem is that the BBC website only supports RealPlayer (I think.  Please feel free to prove me wrong)

Patanjali

---

### Post by aysiu on 2006-04-14
[QUOTE=patanjali]The problem is that the BBC website only supports RealPlayer (I think.  Please feel free to prove me wrong)[/QUOTE] Yes, and the link I gave you before tells you how to install RealPlayer. If you don't like that link, you can try [this one, too](https://wiki.ubuntu.com/RealplayerInstallationMethods).

---

### Post by patanjali on 2006-04-14
[QUOTE=aysiu]Maybe [this](https://wiki.ubuntu.com/RestrictedFormats#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b) might help?[/QUOTE]
I followed the above instructions (thank you), but when installing from the terminal I got the following error messages.  Help!

jack@sisyphus:~/Desktop$ sudo apt-get install libst dc++5
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libst
jack@sisyphus:~/Desktop$ sudo dpkg -i realplayer_10.0.6-0.0_i386.deb
Selecting previously deselected package realplayer.
(Reading database ... 56661 files and directories currently installed.)
Unpacking realplayer (from realplayer_10.0.6-0.0_i386.deb) ...
dpkg: dependency problems prevent configuration of realplayer:
 realplayer depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing realplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 realplayer

---

### Post by aysiu on 2006-04-14
```

jack@sisyphus:~/Desktop$ sudo apt-get install libst dc++5
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libst
``` I think you accidentally put a space between *libst* and *dc++5*. It's all one word: *libstdc++5*. That's why it couldn't find the package.

---

### Post by patanjali on 2006-04-14
Thanks.  RealPlayer all installed.

Patanjali :-)))

---

