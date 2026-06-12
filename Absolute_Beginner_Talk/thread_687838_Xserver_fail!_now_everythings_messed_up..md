---
title: "Xserver fail! now everythings messed up."
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by michaelpagz on 2008-02-04
Okay. Heres my issue. Xserver failed. I reconfigured it and now gnome is working again but now everything is defaulted. I can't get AWN to work. I cant get advanced desktop effects. I dont even have a wallpaper anymore. I noticed that there is a backup file stored somewhere. Is there a default location for that file? anyone know where I can find it? or at least somehow undo everything that happened? 
hope someone can help. it would suck to have to figure all this different stuff out.
thank you so much.
michael

---

### Post by Blutack on 2008-02-04
Open a terminal and type in
> cd /etc/X11
Now type
> ls
and output the result.

---

### Post by michaelpagz on 2008-02-04
```
app-defaults             xinit                     Xsession
cursors                  xkb                       Xsession.d
default-display-manager  xorg.conf                 Xsession.options
fonts                    xorg.conf.20080204175414  XvMCConfig
rgb.txt                  Xresources                Xwrapper.config
X                        xserver
```

---

### Post by Blutack on 2008-02-04
Can you open the xorg.conf.20080204 file and see if it looks similar to the one you had before you mucked it up or is the one that was mucked up? :-)

---

### Post by michaelpagz on 2008-02-04
How can I find xorg.conf.20080204175414  or how can I open it from the terminal? I can muck stuff up with the best of them... but I'm still just a nooob.

---

### Post by Blutack on 2008-02-04
Sorry, it's in the folder /etc/X11
You can get there in Nautilus by going all the way up from your home folder.

---

### Post by michaelpagz on 2008-02-04
okay. I'm looking at xorg.conf.20080204175414 and I think its the one that is messed up, as in the one that I went through the xserver configuration prompts and just selected the defaults to get my desktop back.

---

