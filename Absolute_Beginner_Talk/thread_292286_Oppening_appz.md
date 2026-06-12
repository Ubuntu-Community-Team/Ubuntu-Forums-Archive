---
title: "Oppening appz"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Luj0 on 2006-11-03
Hi all again... Im having a problem, i have instaled tv time, but when i click on it, on icon, nothing happens, like i newer did click on icon. i tried to reinstall it...
What can be the problem??
](*,) ](*,) ](*,)

---

### Post by Fully216 on 2006-11-03
how did you install it?  It is important that you installed all the dependencies.  If you used the rpm, then you are probably missing a dependency.

you should also try running it from the cli, to see if the error is with the icon path or the program itself.

---

### Post by Luj0 on 2006-11-03
god i have this, istaled linux first time 3 days ago... and im such a newbie... i have instaled it from SPM, what does it mean to start it from cpi? how can i find dependenci?

Such a n00b :(

---

### Post by taurus on 2006-11-03
Open a terminal (Applications -> Accessories -> Terminal) and type in the command.  If there is a problem with the program, it will print out some error message.  You need to include that exact error message (you can use cat 'n paste) here so somebody can tell you what's wrong with it...

---

### Post by Luj0 on 2006-11-03
what do i type in terminal... is there some comand for oppening appz or? full name is tvtime television viewer
tnx

---

### Post by taurus on 2006-11-03
Try

```
tvtime
```

---

### Post by Luj0 on 2006-11-03
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/s3rial/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

---

### Post by taurus on 2006-11-03
Well, what video card do you have then???

---

