---
title: "1600x1200 Resolution with Samsung SyncMaster 193P"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by Nunyah on 2006-03-24
Hey all, I've a problem reaching 1600x1200 resolution with my Samsung SyncMaster 193P monitor. I've reconfiguered xserver serveral times enabling 1600x1200 resolution, but when i reboot the machine or xserver, i still can only reach 1200x1024, which is a little too low..

I've no trouble reaching this resolution in Windows XP, but preferred setting is 1200x1024 as XP's objects seems smaller than in gnome.. Is this correct?

Graphic card is POV nvidia 6800 GT.

Is there anything I can do?

---

### Post by akiro.yamamoto on 2006-03-24
Edit the /etc/X11/xorg.conf file manually
```

sudo gedit /etc/X11/xorg.conf

``` Find a section with the various resolutions listed and ADD the one you want.
Then you can select your resolution with:
System >> Preferences >> Screen Resolution
Hope this info helps ;)

---

### Post by akiro.yamamoto on 2006-03-24
You can check this out:[U][B]
[** CLICK ME!!!**](http://ubuntuforums.org/showthread.php?t=83973&highlight=Screen+resolution)

[/B][/U]

---

### Post by Nunyah on 2006-03-24
Tried editing the conf file, but it allready contain 1600x1200 resolution in it.
I could try to run the xorg wizard in console mode and see if it helps..?

---

