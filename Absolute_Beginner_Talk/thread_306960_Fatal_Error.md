---
title: "Fatal Error?"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by CtrlAltDelete on 2006-11-25
I started ubuntu yesterday. I got confident today enuff to download beryl. After the reboot it got this error 

"Failed to start the x server (your graphical interface) it is likey that it isnot setup corectly would you like to the view the x server output to diagnose the problem.

bcm43xx:error: microcode :bcm43xx_microcode5.fw not availalbe or load failed




please help

---

### Post by CtrlAltDelete on 2006-11-25
Well I didn't really fix my problem but was able to do a "startx" command. How do i fix this problem? I realize (maybe) it has something to do with my video card

---

### Post by junglepeanut on 2006-11-25
See if it is repeatable, if startx works I don't know why it crashed the first time. Did you alter something in gdm?

---

### Post by CtrlAltDelete on 2006-11-25
ok the computer does start bu now it s going incredible slow. For example i can type this whole sentice before i see it.  I upgrade my version from beezy recently . How would i reinstall dapepr so i don't have to start fromm all the way in the start. Man thishas been an up and down day... get dvd to work ..then get drapper to work, then get autmatix to work... then crash teh system trying to use beryl../ I wish there was an undo butotn i culd use.. or a restore to an earlier time.

---

### Post by junglepeanut on 2006-11-25
If you can point to the how to you  used and then we just undo everything done, it almost sounds like it is slow because you have the wrong drivers installed.

BUt I am guessing before following the how-to you did all the tests to make sure you had everything set up so that it would work?

One quick way to remove some of the stuff would be go up entries in the terminal history and undo those beryl options

i.e. change 

sudo aptitude install beryl beryl-manager blah blah blah 

to

sudo aptitude remove beryl beryl-manager blah blah balh

then in your startup stuff remove the auto start compiz if you did that?

---

### Post by CtrlAltDelete on 2006-11-25
[http://www.ubuntuforums.org/showthread.php?t=268036&highlight=beryl+dapper](http://www.ubuntuforums.org/showthread.php?t=268036&highlight=beryl+dapper)

I followed this procedure to the period. Its the last step where teh reboot occured that the maddnes began.

---

### Post by junglepeanut on 2006-11-25
Ouch, that is not the way I would recommend it as it removes your normal way, next time go to the beryl forums and follow the method listed there for having a gnome session and a xgl session, that way if beryl crashes other stuff will still work.

OK,
If you want, Just for now so you can work in a faster enviroment (since gnome is so slow now) you can always remove this, install icewm,```
sudo aptitude install icewm
``` this way we can get some work done and things will move quickly, then restart and choose to boot into icewm at the login prompt. otherwise continue from here after the first step below as it is for point and click in gnome

Go to System –> Preferences –> Sessions –> Startup Programs
remove ```

xmodmap -e "keycode 22 = BackSpace"
beryl-manager
```

Ok then we will remove some apps via
```

sudo apt-get remove  xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

remove this 
```

0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```
from /etc/gdm/gdm.conf-custom according to the howto you should have pasted this at the bottom.
then we should be back to how it started.
Hopefully if you were in icewm you can move to gnome and it works now, if not in icewm and did all in gnome then just restart and see if it fixes the issue.

If not we will try some other stuff (Beryl is alpha so it might have messed up some settings..not likely though)

---

### Post by junglepeanut on 2006-11-25
Also some of that how to is not for XGL it is specific to his computer, so if you do not have dual cores and you did everything he did you might have issues, or if you did nt have the wireless issue. I would stick with the generic kernels for now as that is the way things may be moving, feisty and edgy are going back and forth.

---

### Post by CtrlAltDelete on 2006-11-26
sudo aptitude install icewm

this was a great idea..what does it do. my computer is now moving a bit faster and beryl is working. I want to play with it for a little bit. Its been my dream since for the last 48 hours to get this point. Then i will follow through. I just may need more memory. I have 256 kb

---

### Post by junglepeanut on 2006-11-26
Ouch 256MB is barely enough for gnome let alone xgl, (if I read this correctly.) You could lower the requirements of gnome, or use xfce (xubuntu) or "gnome-core or kde-core" to lighten things. Or just use icewm or fluxbox. They should fly on your system. I use icewm a lot, and my computer can handle xgl. Why?, it is plain fast, I can make it look like anything. And it is simple.

---

