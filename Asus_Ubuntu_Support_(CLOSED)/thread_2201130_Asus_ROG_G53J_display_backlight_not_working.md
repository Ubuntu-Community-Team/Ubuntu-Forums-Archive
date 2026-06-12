---
title: "Asus ROG G53J display backlight not working"
date: 2014-01-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by SonWon on 2014-01-22
Asus ROG G53J laptop cannot adjust display brightness running Ubuntu 12.04.  How do I fix?

Things I tried that failed:
[http://ubuntuforums.org/showthread.php?t=2033273](http://ubuntuforums.org/showthread.php?t=2033273)
[http://askubuntu.com/questions/128463/how-to-control-brightness](http://askubuntu.com/questions/128463/how-to-control-brightness)

Useful website:
[https://wiki.archlinux.org/index.php/Backlight](https://wiki.archlinux.org/index.php/Backlight)

I can now adjust the screen brightness by following these steps:

1. sudo gedit /etc/X11/xorg.conf
2. add this line just above the 'EndSection', Option "RegistryDwords" "EnableBrightnessControl=1"
3. save the file
4. reboot or restart xorg.
5. install 'xbacklight' with Ubuntu Spftware Centre or Synaptic Package Manager
6. map this command to your preferred keys, I used 'Ctrl+-', xbacklight -dec 10
7. map this command to your preferred keys, I used 'Ctrl++', xbacklight -inc 10

Enjoy!

Now I want to know how to map this to the function keys F5 anf F6?

---

### Post by SonWon on 2014-01-28
Found the fix, hope this help some in the future:

1) Go to Nvidia settings and save config into xorg.conf (the file will be at /etc/X11)
2) In xorg.conf in the "Device" section for your GPU add (use sudo to edit with your favorite editor)
	Option "RegistryDwords" "EnableBrightnessControl=1"
3) restart X and brightness works or reboot

---

