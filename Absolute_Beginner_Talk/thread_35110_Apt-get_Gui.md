---
title: "Apt-get Gui?"
date: 2005-05-17
forum: Absolute Beginner Talk
---

### Post by astronerd on 2005-05-17
Is there anything similar to Yum-ex in FC for Ubuntu and apt?  I just dont know much if anything about apt and packages and where to look/which ones to install and it would be easier if there was a gui or something that could describe what each package does and help you look for specific packages etc.  Anything like that for ubuntu?  Thanks,
Charles

---

### Post by kvidell on 2005-05-17
[QUOTE=astronerd]Is there anything similar to Yum-ex in FC for Ubuntu and apt?  I just dont know much if anything about apt and packages and where to look/which ones to install and it would be easier if there was a gui or something that could describe what each package does and help you look for specific packages etc.  Anything like that for ubuntu?  Thanks,
Charles[/QUOTE]
 You are looking for "synaptic" I believe :)
- Kev

---

### Post by telmo on 2005-05-17
Wellcome newbie!  :)

Ubuntu is beautifull!!!

---

### Post by Sam on 2005-05-17
You can find a menu entry in System / Administration / Synaptic Package Manager

---

### Post by astronerd on 2005-05-17
[QUOTE=telmo]Wellcome newbie!  :)

Ubuntu is beautifull!!![/QUOTE]
 Thanks guys, found it.  Just one more quick thing.  I just installed gkrellm via synaptic, but I cant seem to find it.  I looked everywhere, is there somewhere it puts it after the download?  I just assumed that it would install it and it would be ready to go....

---

### Post by kvidell on 2005-05-17
[QUOTE=astronerd]Thanks guys, found it.  Just one more quick thing.  I just installed gkrellm via synaptic, but I cant seem to find it.  I looked everywhere, is there somewhere it puts it after the download?  I just assumed that it would install it and it would be ready to go....[/QUOTE]
 I'm not sure if it puts it in a menu somewhere, probably under "system" or something though.
Hit Alt+F2 and type in "gkrellm" there and see if it runs.
It should have installed it's binaries to /usr/bin though.
- Kev

---

### Post by Knome_fan on 2005-05-17
It probably doesn't install an entry in the menu.
Simply open a terminal and type gekrellm (if that doesn't work, type gekr and press tab and it should complete the right name for you), or use the run application dialogue.

---

### Post by Sam on 2005-05-17
[QUOTE=astronerd]Thanks guys, found it.  Just one more quick thing.  I just installed gkrellm via synaptic, but I cant seem to find it.  I looked everywhere, is there somewhere it puts it after the download?  I just assumed that it would install it and it would be ready to go....[/QUOTE]
You can install [smeg](http://ubuntuguide.org/#menu-editor) for editing your menu and adding new programs.

You can also add a launcher in /usr/share/applications/. Paste the following lines in /usr/share/applications/gkrellm.desktop:
```
[Desktop Entry]
Encoding=UTF-8
Name=GKrellM
Comment=GKrellM
Exec=gkrellm
Icon=
Terminal=false
Type=Application
Categories=GNOME;Application;System;Utility;
```

---

