---
title: "VIA Unichrome Pro IGP on P4M800-M7"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Velenoso on 2007-09-03
Hi there,

I am brand new to the Linux OS. This is my first installation of Ubuntu 7.04. I would love to switch to from windows to Linux but I have just about given up.

All my hardware was detected correctly, even my printer. The only thing thats bothering me is I cannot obtain 85 refresh rate on my monitor. The flickering is most annoying. 

I can get a resolution of 1280 x 1024, the little GUI utility tells me its running at 85 refresh, but it isn't. Any help would be much appreciated.

---

### Post by oiler920 on 2007-09-03
Try running this in the terminal (found in Applications > Accessories > Terminal):
```

sudo apt-get install xserver-xorg-video-unichrome
```

After it finishes installing, hit CTRL+ALT+BACKSPACE on your keyboard.

---

### Post by Velenoso on 2007-09-06
Hi there, I get the following error after running that command.

oliver@oliver:~$ sudo apt-get install xserver-xorg-video-unichrome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-video-unichrome

Does the computer need to be connected to the internet for this to work? I have not yet connected that box up... 

Thanks in advance.

---

### Post by spydon on 2007-11-01
Yes you have to be connected to the internet :P

---

