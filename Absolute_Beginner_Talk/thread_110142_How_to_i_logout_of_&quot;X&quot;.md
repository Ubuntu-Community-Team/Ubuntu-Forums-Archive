---
title: "How to i logout of &quot;X&quot;?"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Glottis on 2005-12-30
Im trying to exit X to install Nvidia graphics drivers. I can run the packages from the terminal but it keeps saying that i need to exit X in order to install.

Ive tried logging in to a failsafe terminal session, as myself and root, but i get the same message there too. 

Help meeeeeeeee :(

---

### Post by kaamos on 2005-12-30
I think there are pretty good instructions here: [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

Note that if you don't need the newest driver the installation is very easy:
[quote=tseliot]
Make sure you have Universe and Multiverse repositories enabled.

Open Synaptic/Kynaptic
Press the Search button in Synaptic/Kynaptic
Type the word "nvidia" and press ENTER
Right click on the "nvidia-glx" and "nvidia-settings" packages and Mark them for installation:
Miscellaneous - Graphical (restricted) > nvidia-glx
Miscellaneous - Graphical (restricted) > nvidia-settings

Open Terminal or Konsole and type:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
```[/quote]

---

### Post by drfalkor on 2005-12-30
and then:
ctrl - alt - backspace (restarting X)

---

### Post by Glottis on 2005-12-30
you're superstars guys :D :D :D :D

thanks

---

### Post by Glottis on 2005-12-30
you're superstars guys :D :D :D :D

thanks

---

### Post by Suger on 2005-12-30
Should you need to leave X for anything,

Ctrl+Alt+F1 will bring you to a virtual console (and Ctrl+Alt+F7 back to X)
After login in, you can
```

sudo /etc/init.d/gdm stop

``` to stop gdm and X by the way.

Then

```

sudo /etc/init.d/gdm start

```

when you're ready to return to X.

---

