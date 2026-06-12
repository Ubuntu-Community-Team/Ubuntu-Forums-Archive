---
title: "compiz trouble gutsy"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by viperskunk on 2008-04-16
hi 
i have gutsy, and i have compiz-fusion.
all a sudden today my compiz doesn't work. i run "compiz" in the terminal and this is what i get:


viperl@viper-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/texture_filter. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/texture_filter. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
inotify_add_watch: No such file or directory


any ideas what might be wrong. i reinstalled the comiz packages through synaptic and still i get the same message.

---

### Post by mbadawi23 on 2008-04-16
> Checking for nVidia: not present. 
Make sure that your nVidia driver is enabled. I don't know what may cause to stop working by itself!

---

### Post by bumanie on 2008-04-16
> **viperskunk said:**
> hi 
i have gutsy, and i have compiz-fusion.
all a sudden today my compiz doesn't work. i run "compiz" in the terminal and this is what i get:


viperl@viper-laptop:~$ compiz
Checking for Xgl: [COLOR="Red"]not present[/COLOR]. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: [COLOR="Red"]not present[/COLOR]. 
Checking for FBConfig: present. 
Checking for Xgl: [COLOR="Red"]not present[/COLOR]. 
Starting emerald
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/texture_filter. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/texture_filter. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
inotify_add_watch: No such file or directory


any ideas what might be wrong. i reinstalled the comiz packages through synaptic and still i get the same message.

[COLOR="Black"]I am definitely no expert on compiz or video card matters, but the lines highlighted in red make me suspicious that something has happened to your video card drivers. May be you should try to uninstall and reinstall the nvidia driver. Don't know if I am on the right track or not, but nvidia 'not present' , 'xgl' not present would seem to be video card related.[/COLOR]

---

### Post by viperskunk on 2008-04-18
how do i enable my video drivers? i am quite new to this.

---

### Post by bumanie on 2008-04-18
Go to System--> Aministration --> Restricted Drivers
Clicl on the check box and a driver should automatically download.

---

