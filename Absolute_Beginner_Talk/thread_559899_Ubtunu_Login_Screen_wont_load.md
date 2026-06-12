---
title: "Ubtunu Login Screen wont load"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by eamrhein on 2007-09-25
Hi, I'm very new to Ubuntu and Linux and I seem to have made my first major mistake messing with it and now the login screen wont load. I changed some accessibility settings trying to get access to my usb flash drive, Im not sure exactly what I changed but now have now access to the user interface. It boots up perfectly fine but when it gets to the loading screen the little loading wheel pops up but it isn't loading. I do have access to the terminal when I hit Ctrl-Alt-F1 but I don't know how to change the settings so I can access the interface again. I tried some of the commands from older threads but none seem to work.

Also, if it turns out I have to reinstall ubuntu? will a reinstall wipe all my documents and files?

---

### Post by overdrank on 2007-09-25
> **eamrhein said:**
> Hi, I'm very new to Ubuntu and Linux and I seem to have made my first major mistake messing with it and now the login screen wont load. I changed some accessibility settings trying to get access to my usb flash drive, Im not sure exactly what I changed but now have now access to the user interface. It boots up perfectly fine but when it gets to the loading screen the little loading wheel pops up but it isn't loading. I do have access to the terminal when I hit Ctrl-Alt-F1 but I don't know how to change the settings so I can access the interface again. I tried some of the commands from older threads but none seem to work.

Also, if it turns out I have to reinstall ubuntu? will a reinstall wipe all my documents and files?

Hi you don't remember what settings you changed, then what commands did you try and why?
If you have to reinstall there is a chance you can save your data with the live cd.

---

### Post by eamrhein on 2007-09-25
I tried removing the gnome settings files If I remember correctly, but that did not help,

---

### Post by overdrank on 2007-09-25
> **eamrhein said:**
> I tried removing the gnome settings files If I remember correctly, but that did not help,

Well then try to install you desktop again
```
sudo apt-get install ubuntu-desktop
```

---

### Post by eamrhein on 2007-09-25
> **overdrank said:**
> Well then try to install you desktop again
```
sudo apt-get install ubuntu-desktop
```

Tried that, got this error

E: sub-process /usr/bin/dpkg returned error code.

---

### Post by eamrhein on 2007-09-25
hmmm it seems the reason im getting this error is because it wants to install gaim, but some of the packages that are used for gaim are being used for pidgen (makes sense, but I dont know how to fix it)

---

### Post by eamrhein on 2007-09-25
I know it's a bit rude to triple post, but I've got an important paper due tomorrow which is saved on the Ubuntu partition of my HD. If I can fix this without reinstalling the whole distro, then I need to know soon, or else I will have to start retyping from scratch.

---

### Post by dn_desaku on 2007-09-26
Well, do you have any external hard drives? I'd say back up all your important stuff (ie your paper) onto it with the live CD and reinstall Ubuntu. This may be needed in a last resort. Also, if all the configuration you have done so far is minor (like change wallpaper, or tweak icons just right), just wipe it out. Wait until you take my advice because some other dude may come up with a better solution.

---

