---
title: "Screen goes blank after the splash load up screen"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by cage27 on 2007-05-03
I am currently using a Dell Inspiron 5160 with a XGI Volari-XP5 v2 Graphics card. I have used Ubuntu 6.06 and everything worked well, however I recently tryed to upgrade to Ubuntu 6.10 and the screen goes blank after the splash load up screen, the same happens with Ubuntu 7.04 Live CD. . Any help would be appreciated. I have tried setting the driver in xorg.conf file to &#8220;vesa,&#8221;, from recovery mode, but I think I'm doing something wrong. At the comand promt I type:
 **sudo nano /etc/X11/xorg.conf** All I get is a Nano text blank screen and can't find were to change the driver. What am I doing wrong?

---

### Post by AtrejuT on 2007-05-03
there's a typo, I don't know if only in your post or also in the command you're issuing, it should be
/etc/ and not /ect/

---

### Post by cage27 on 2007-05-03
> **AtrejuT said:**
> there's a typo, I don't know if only in your post or also in the command you're issuing, it should be
/etc/ and not /ect/
only in my post, have fixed it:)

---

### Post by AtrejuT on 2007-05-03
it's pretty strange then that the file is empty.
what happens if you do
```

cd /etc/X11
ls

```
- does the file show up? can you post the output of that?

---

### Post by cage27 on 2007-05-03
This is the output

X,                                          Xwrapper.confg,                       gdm
Xressources,                         app-defaults,                            rgh.txt
Xsession,                              config,                                       xinit
Xsession.d,                           cursors,                                     xkb
Xsession.options,                 default-display-manager,          xorg.conf
XvMCConfig,                         fonts,                                         xorg.conf.20070419201037

---

### Post by AtrejuT on 2007-05-03
so there is an xorg.conf. what does
```

cat xorg.conf
cat xorg.conf.20070419201037

```
give?

sorry for being late, I had to work for a while.

---

### Post by cage27 on 2007-05-03
cat xorg.conf
gives



```
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
End SubSection 

SubSection   "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
End SubSection 

Section "DRI"
Mode 0666
End Section
```

I think there is more info, but am farly new to linux not sure how to see it all

---

### Post by K.Mandla on 2007-05-03
> **cage27 said:**
> cat xorg.conf
gives ...

I think there is more info, but am farly new to linux not sure how to see it all
There should be quite a bit more, really. It's possible that the file was damaged, which would explain why it's not quite working.

Try 
```
sudo dpkg-reconfigure xserver-xorg
```
I believe that will build you a new xorg.conf file, and set you back on the path. ;)

---

### Post by AtrejuT on 2007-05-03
but then if you try to edit this file with nano there should be something there. (cat just lists the content of the file), and resetting the drivers to vesa sounds like a smart idea to me...
so try again (from that directory were you can cat the file)
```

sudo nano xorg.conf

```

another thing you could try to do is restore that backup of xorg.conf that is there. so first rename the existing xorg.conf
```

sudo mv xorg.conf xorg.conf.backup

```
and then the backup.
```

sudo mv xorg.conf.20070419201037 xorg.conf

```

(oh, and don't forget to reboot...)

---

### Post by cage27 on 2007-05-03
I maneged to get into the file wiyh **sudo vim /etc/X11/xorg.conf**
but "vesa" was already the driver. Are there any alternative drivers that will work with ubuntu6.10 
How can I revert back to the driver that was on 6.06?

---

### Post by cage27 on 2007-05-03
I rebuilt the file with 
**sudo dpkg-reconfigure xsrever-xorg**
during reconfiguring a selection of vidio drivers came up:
sis
sisusb
tdfx
tga
trident
tseng
vesa
vga
via
vmware
voodoo.

I tryed the vmware, it didn't work but i can now get into xorg.config with nano.
any sugesgens which driver to use before i start the proses of elimination.

---

### Post by K.Mandla on 2007-05-03
Try vga next, or vesa again since you have a complete xorg.conf file now. 

The trick is to find out who the device manufacturer is, and then try the driver that should match that card. Perhaps the trident or sis drivers next?

---

### Post by cage27 on 2007-05-04
Have so far tryed
[B]sis
vga
vmware
vesa
trident[/B]
no luck yet, however I have found some more info about XGI Volari-XP5 v2 and Linux
**[www.linuxquestions.org/questions/showthread.php?t=248394](www.linuxquestions.org/questions/showthread.php?t=248394)**
and
**[www.webspawner.com/users/dell5160/index.html](www.webspawner.com/users/dell5160/index.html)**

---

### Post by cage27 on 2007-05-07
I have tryed all the options no luck. I went back to the ubuntu 6.06 live cd and had a look what driver it used and it was vesa. I think the problem I have is not a driver one. Its back to the drawing board, I am determined to get this thing working one way or another.
[http://ubuntuforums.org/showthread.php?p=2611027#post2611027](http://ubuntuforums.org/showthread.php?p=2611027#post2611027)

---

### Post by Nythain on 2007-05-07
possible fix... gksudo /boot/grub/menu.lst
remove quiet splash (or splash quiet, however it appears) from your grub entries

---

### Post by cage27 on 2007-05-12
> **Nythain said:**
> possible fix... gksudo /boot/grub/menu.lst
remove quiet splash (or splash quiet, however it appears) from your grub entries

I tryed that, the outcome was```
(gksudo: 8423:
Gtk-WARNING**:
Cannot open display
```

---

### Post by junjan on 2007-05-12
Check this out:

[XGI Volari not supported by Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/86550")

[black screen and console freeze when X starts - drm lockup]("https://bugs.launchpad.net/ubuntu/edgy/+source/xserver-xorg-video-ati/+bug/67487")

---

### Post by askmeabouttruth on 2007-05-20
I have the same problem on Fiesty. It just started locking up like this today - can't fix it and I turned the forum upside down.

---

### Post by markhelsby on 2007-11-14
Hi

Did you ever manage to resolve this?

Thanks

Mark

---

