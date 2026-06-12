---
title: "Xubuntu Driver help"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by huviduc on 2006-11-09
i just installed Xubuntu and it seems that i need to update my video driver or something. everything is very large and when i go to display settings to change it, i do not have any better options. How would i go about either updating the driver, or somehow changing the resolution? by the way, it is a 3dfx voodoo3 video card. please be pretty specific because i have only been on the system about a half hour so i am pretty new to this. but i do know how to use it a little because i had fedora 4. thanks

---

### Post by Ecthelion on 2006-11-09
If you know the maximum resolution and refreshrate of our monitor you can do this:

Do ctrl-alt-F1 (ctrl-alt F7 will bring back the graphical interface)

So you do ctrl-alt-F1

then do
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
to backup your xorg.conf file

Then run
```
sudo dpkg-reconfigure xserver-xorg
```

When you dont know what option to choose, leave the default option.
You will eventually get to choose your resolutions and then add the right resolutions.
Be sure that those resolutions can work on your monitor.

If you messed up the dpkg-reconfigure, doing
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
will set everything back as it was before you tried what I just said.

---

