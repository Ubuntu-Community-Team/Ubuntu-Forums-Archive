---
title: "Need help installing NVidia 1.0-9755 driver"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by cjl2301 on 2007-03-30
Ok guys - from what I understand to install this all I need to do is:

1) Get into run level 3
2) sh the .bin file

The problem I'm having is #1.  I rebooted into "recovery mode" and ran the file, but it complained saying that I was at runlevel 1 and needed to be at runlevel 3.   I then typed "init 3" and X Windows came up.  I tried to sh the .bin file again, but it could not run because I was in X Windows.

How can I easily get into a non graphical run level 3 session so I can install this driver?

Thanks!

P.S. This is in 6.10

---

### Post by taurus on 2007-03-30
You need to stop gdm so try

```
sudo /etc/init.d/gdm stop
```

---

### Post by NikoC on 2007-03-30
Just boot with your regular kernel, login to gnome and when all is loaded press ctrl + alt + f1 which will get you in CLI. You probably need to login again,  use your gnome user and password. Then type:
sudo /etc/init.d/gdm stop 

This is the command to stop gdm and X (at least this works for me).

Then type you can install the nvidia driver as you have described!

Edit: Taurus beat me to it ;)

---

### Post by cjl2301 on 2007-03-30
Nevermind, I found this:

[http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412)

I guess it's not quite as easy as i thought.   Just curious, what are these dependencies that we have to install?

---

### Post by r4ik on 2007-03-30
Try Envy,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It is an automated script.

---

### Post by Maestro23 on 2007-03-30
> **cjl2301 said:**
> Nevermind, I found this:

[http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412)

I guess it's not quite as easy as i thought.   Just curious, what are these dependencies that we have to install?

Or you could just use the Envy script: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by cjl2301 on 2007-03-30
Cool, thanks guys!  I'll try the envy script tonight.

---

