---
title: "Nvidia resolution problem"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by 500sd on 2008-02-16
Well a couple days ago I booted up normally and arrived at my linux desktop. My resolution  is locked at 1600x1200...I can select other options but when i click apply, its  still 1600x1200

---

### Post by nikoPSK on 2008-02-16
could you try reconfiguring xorg please?
```

sudo dpkg-reconfigure --phigh xserver-xorg
```

That should work for your issue. :)

---

### Post by 500sd on 2008-02-16
this is the error I get:
```
Unknown option: phigh
Usage: dpkg-reconfigure [options] packages
  -a,  --all                    Reconfigure all packages.
  -u,  --unseen-only            Show only not yet seen questions.
       --default-priority       Use default priority instead of low.
       --force                  Force reconfiguration of broken packages.
  -f,  --frontend               Specify debconf frontend to use.
  -p,  --priority               Specify minimum priority question to show.
       --terse                  Enable terse mode.

```

---

### Post by nikoPSK on 2008-02-16
Try this I guess:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by 500sd on 2008-02-16
It brought up a setup type thing...i just skipped through it and nothing happened

---

### Post by 500sd on 2008-02-16
So any other solutions?

---

### Post by 500sd on 2008-02-16
Come on...any ideas?

---

### Post by nagius on 2008-02-16
Have you tried installing nvidia drivers with envy?

---

### Post by 500sd on 2008-02-16
Yea I have the nvidia driver

---

### Post by PmDematagoda on 2008-02-16
What resolution do you want?

Also, post the output of:-
```
cat /etc/X11/xorg.conf
```

One more thing, did you try making the required changes through Nvidia settings?
Nvidia settings can be brought up using:-
```
gksudo nvidia-settings
```

---

### Post by LacosteGirl23 on 2008-02-16
I have this driver. And I don't have a resolution problem. It just looks blurry to me. My laptop is brand new. I really don't understand what is going on. Any help would help!

---

### Post by 500sd on 2008-02-16
K I got the resolution working. Just reading fonts on firefox and stuff is slightly blurry

---

### Post by nikoPSK on 2008-02-16
> **500sd said:**
> K I got the resolution working. Just reading fonts on firefox and stuff is slightly blurry
Maybe enabling smooth fonts?
[http://nikopsk.wordpress.com/2008/02/14/smooth-fonts-in-ubuntu/](http://nikopsk.wordpress.com/2008/02/14/smooth-fonts-in-ubuntu/)

---

