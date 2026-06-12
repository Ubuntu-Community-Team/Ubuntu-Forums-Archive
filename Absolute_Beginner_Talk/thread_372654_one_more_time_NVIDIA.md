---
title: "one more time NVIDIA"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by ex_win_slave on 2007-02-28
I m just install nvidia drivers with envy..and everything goes good.but the problem is:when i reboot
my computer my settings 1152x864@75hz are gone. I make settings with Systemtools/Nvidia X 
server settings (1152x864 75 hz then:apply and saving "Save to X Configuration file)My graph card is GeForce 4200ti 128mb.So do i have make some editing to X Configuration file?How and why???
Or reinstall Nvidia drivers?How? So,you see I m newbie with this..but this is more better than windows..I think8...  -)  So save me!! :(

---

### Post by edwardLS on 2007-02-28
I have a different nVidia card than you, but when I did pretty much as you did, I still had to edit /etc/X11/xorg.conf.  I had to add the screen resolution that I wanted, which was not in the xorg.conf file even after running the nVidia configuration routine.  When I added my desired resolution to each place in xorg.conf that referred to other resolutions, I have been at my desired resolution ever since.

Good luck, hope it is that simple.

---

### Post by ex_win_slave on 2007-02-28
So i found that file... and stupid question:what program i can use to edit that xorg.conf file???
(i know that:i can edit with text editor like in windows)   :guitar:

---

### Post by Spr0k3t on 2007-02-28
First and foremost, make a backup before making any changes to the file.

```
gksudo gedit /etc/X11/xorg.conf
```

Make sure you have a backup, if you don't understand the importance, try without for a while.

---

### Post by bodhi.zazen on 2007-02-28
1. Save a back up : ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup_2_28_07
```

2. Then edit : ```
gksudo gedit /etc/X11/xorg.conf
```

Edit and save your changes ;)

---

### Post by old_geekster on 2007-02-28
Hey Ex, try this link:

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers)

I also have a different vid card than yours, but I have used this guide numerous times.  It installs "NVIDIA X Server Settings" tool in the System Tools area.

Follow the steps carefully, especially where he says to make notes for the last steps.  You will need them.

This tool allows you to adjust your resolution.

Hope this helps.

---

