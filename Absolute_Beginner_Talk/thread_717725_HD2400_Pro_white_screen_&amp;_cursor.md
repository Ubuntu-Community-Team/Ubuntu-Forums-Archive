---
title: "HD2400 Pro white screen &amp; cursor"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by sniper5 on 2008-03-07
I've tried to install the latest ATI drivers for my HD2400 Pro AGP graphics card. When i start Ubuntu (7.10, Gnome desktop) the screen turns white. There is a cursor which i can move, but no sidebars and no icons at all. I can only get the system to work when i revert back to the original settings (VESA diver). I've tried several other possibilities, but no luck at all, either the white screen or a garbled screen.
I'm a relative newbie to Ubuntu. I've tried both the 8.02 driver and the 8.3 driver (dated march 5, 2008), but i get the same result for both. Can anyone help me with this?

---

### Post by Hospadar on 2008-03-07
you may try using the envy scripts to install your drivers.  Get "Envy Legacy" from [here]("http://albertomilone.com/nvidia_scripts1.html"), install it, and then run it from a command prompt.

Alternatively you can install if from a command line```
wget http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu6_all.deb
dpkg -i envy*.deb
```

Now that you've installed them, go to a command prompt (Ctrl-Alt-F1) login, and stop your x server ```
sudo /etc/init.d/gdm stop
``` (kdm or xdm if you use kde or xfce respectively).
Now run envy ```
sudo envy -t
```do the "remove" and "clean" operations on ati drivers, then do the installation for ati drivers.
Ideally this would plop you right back in your X server, though you might have to Ctrl-Alt-F7 to get there.  If it doesn't work, you can at least use it to easily remove the installation.

---

### Post by mikeyphi on 2008-03-07
I'm sorry to say that this looks like an ongoing issue. Look here: 

[http://ubuntuforums.org/showthread.php?t=648061](http://ubuntuforums.org/showthread.php?t=648061)

---

