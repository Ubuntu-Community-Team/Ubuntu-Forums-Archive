---
title: "suddenly non-graphical login screen -- then no GUI"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by gregconquest on 2006-09-17
Last night I was having problems shutting down Ubuntu 6.06. I clicked on one of the commands in the upper left menu -- I think it was "signout" and then I forced it to shutdown using the power button, I think.

This morning, when I boot into Ubuntu, I get a non-graphical login screen. After I login there, I have a command prompt:
:~$

What do I do from here, and why did this happen? Is "signout" to blame?

Thanks for any help.
Greg Conquest

keys: gui, text, start

---

### Post by bodhi.zazen on 2006-09-17
What happens when you type (give the commands):

[list=number][*]X
[*]startx
[*]sudo gdm[/list]

Error message?

You can try:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by gregconquest on 2006-09-17
Thanks for the reply, bodhi.zazen;

> What happens when you type (give the commands):

> 1. X
-bash: x: command not found

> 2. startx
The screen flashes to the low-res gui, then back down to:
Waiting for X server to shut down FreeFontPath: FPS "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing"

> 3. sudo gdm
gdm: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

> sudo dpkg-reconfigure -phigh xserver-xorg
x server-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20060918122517

Greg

---

### Post by Najand on 2006-09-17
Try to reinstall libgtk2.0-0 and try again:
```

sudo aptitude reinstall libgtk2.0-0

```

---

### Post by bodhi.zazen on 2006-09-18
LOL :lol: The first command was with a capital X not a small x.

I should have mentioned it should start a gray screen with a large black "X" cursor. To exit do the three finger salute: Ctrl-Alt-Backspace.

Let us know if you are still out in the cold cli. :)

---

### Post by gregconquest on 2006-09-19
Capital "X"? OK. Got it. Tried this all, then, this worked:

```
sudo aptitude reinstall libgtk2.0-0
```

Thanks to all of you :-)

Greg Conquest

---

### Post by whizbaby on 2006-09-19
Conclusion: use shutdown to shut down.

---

### Post by gregconquest on 2006-09-21
> Conclusion: use shutdown to shut down.

Are ther any other GUI menu choices that I shouldn't try? I thought there was a general sense of encouragement about checking out the commands available. Using "Signout" hardly seems to be something that dropping to a command line would be required to fix.

BTW, I can't find the menu choice I used before. There is no "signout" or anything like it visible in my menu choices now. In my previous situation, had my system already crashed some component that caused a new menu item to appear? Was clicking "signout" really the cause of all this?

Greg

---

### Post by whizbaby on 2006-09-22
> **gregconquest said:**
>  and then I forced it to shutdown using the power button, I think.
This is what I referred to. Of course you can try any command available to shut down.

---

### Post by Perfect Storm on 2006-09-22
> **gregconquest said:**
> 
BTW, I can't find the menu choice I used before. There is no "signout" or anything like it visible in my menu choices now. In my previous situation, had my system already crashed some component that caused a new menu item to appear? Was clicking "signout" really the cause of all this?

Greg

Is it the Applications,places, System that is vanished or the stuff in them?

---

