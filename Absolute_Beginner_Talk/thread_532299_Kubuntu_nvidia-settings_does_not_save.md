---
title: "Kubuntu: nvidia-settings does not save"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Dev'olution on 2007-08-22
Hey Guys,

I'm using Kubuntu 7.04 and an nVidia Geforce go 7300

However, whenever i go to write to xorg.conf it has a whinge saying it cannae right to it.

Basically it comes up with the following:

```
kristian@kristian-laptop:~$ sudo nvidia-settings
Password:
Sorry, try again.
Password:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
sh: pkg-config: not found
sh: pkg-config: not found

ERROR: Unable to determine valid vertical refresh ranges for display device
       'LPL' (GPU: GeForce Go 7300)!


ERROR: Failed to add display device 'LPL' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!

                                                     
```

HELP!

---

### Post by splintercellguy on 2007-08-22
Shouldn't you do gksudo?

---

### Post by bodhi.zazen on 2007-08-22
@splintercellguy : kde uses kdesu (rather then gksu)


Are you trying to configure your xorg for a newly installed nvidia driver ?

If so, ```
sudo nvidia-xconfig
```

If not, try **kdesu** , although I do not think that will make a difference. You may need to 

kdesu kate /etc/X11/xorg.conf and edit the settings manually.

---

### Post by Dev'olution on 2007-08-22
How do I do it manually?

---

### Post by bodhi.zazen on 2007-08-22
open the file with kdesu kate /etc/X11/xorg.conf and edit the file.

What are you trying to do exactly ?

---

### Post by Dev'olution on 2007-08-22
Apologies for not making myself clearer.

I basically aim to set my desktop resolution to 1280x800.

I am not proficient enough to edit my xorg.

Can someone please help?

---

### Post by bodhi.zazen on 2007-08-22
1. try ```
sudo nvidia-xconfig
```

restart X (log out and back in)


If that fails,

2. try ```
kdesu nvidia-settings
```

restart X (log out and back in) to test the setting took.


If that fails,

3. Manually edit xorg.conf

```
kdesu kate /etc/X11/xorg.conf
```

go to the screen section, it will look something like this :

> Section "Screen"
    Identifier  "xxx"
    Device      "yyy"
    Monitor     "zzz"
    **DefaultDepth 24**

    Subsection "Display"
        Depth       24
        Modes       **"1280x800" "1024x768" "800x600"**
    EndSubsection
EndSection

See the bolded setions above :)

Save and exit kate

restart X (log out and back in)

=======

Why 1280x800 ? Is that a non-standard resolution ? Why not 1280x1024 ?

---

### Post by schorsch on 2007-08-22
> **bodhi.zazen said:**
> Why 1280x800 ? Is that a non-standard resolution ? Why not 1280x1024 ?
.. perhaps he uses a widescreen laptop like me? I haven`t got it any larger than this but it is sufficient as I am getting older .... :D

---

