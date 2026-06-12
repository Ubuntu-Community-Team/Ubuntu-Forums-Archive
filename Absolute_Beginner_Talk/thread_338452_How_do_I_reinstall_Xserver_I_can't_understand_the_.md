---
title: "How do I reinstall Xserver? I can't understand the posts"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by konungursvia on 2007-01-14
I go the message GDM: Xserver not found. I see some posts saying I have to re-install but when I try a sudo apt-get xserver-org nothing happens. Also, they deal with Edgy it seems. Can someone please help?

---

### Post by cilynx on 2007-01-14
```

sudo apt-get install xserver-xorg

```

What's the ouput of that?

---

### Post by konungursvia on 2007-01-14
> **cilynx said:**
> ```

sudo apt-get install xserver-xorg

```

What's the ouput of that?

Xserver-xorg is already the latest version

Thanks for answering! any idea what to do?

---

### Post by riven0 on 2007-01-14
To reinstall:

> sudo apt-get install --reinstall xserver-xorg

---

### Post by konungursvia on 2007-01-14
> **riven0 said:**
> To reinstall:

Thanks. Still says this---

GDM : Xserver not found. /usr/bin/Xgl/ :0 :0 -fullscren -ac -accel
glx: pbuffer -accel xv:fbo -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: command could not be executed!
Please install the X server or correct GDM configuration and restart 
GDM.

What next?

---

### Post by riven0 on 2007-01-14
Alright, have you tried a reconfiguration yet?:
> 
sudo dpkg-reconfigure xserver-xorg

---

### Post by cilynx on 2007-01-14
OK... 

You've been fooling with Xgl.  Do you have xserver-xgl installed?  That's what it's looking for.  If you're trying to get back to good old Xorg, remove xserver-xgl and do the reconfiguration of Xorg as stated above.

---

### Post by konungursvia on 2007-01-14
> **riven0 said:**
> Alright, have you tried a reconfiguration yet?:

Thank you so much for answering. I have now tried that, and guessed at some of the entries, mostly using defaults. Unfortunately, it returned to the same. Should I just go through config again with slightly different stuff till it works?

---

### Post by cilynx on 2007-01-14
Is it still looking for Xgl?  If so, which tutorial did you follow when trying to get Xgl working?

---

### Post by konungursvia on 2007-01-14
> **cilynx said:**
> Is it still looking for Xgl?  If so, which tutorial did you follow when trying to get Xgl working?

It is still looking for Xgl. I don't know that I followed any tutorial, and don't remember what xgl means. I did install the legacy nvidia driver to get 1280X1024 at some point. Does that help?

---

### Post by riven0 on 2007-01-14
Okay, cilynx may have the solution here. First, try removing xserver-xgl:

> sudo apt-get autoremove xserver-xgl

Reinstall the xserver (this is probably redundant, but its better to be safe than sorry :) )

> sudo apt-get install --reinstall xserver-xorg

Then  reconfigure everything:

> sudo dpkg-reconfigure xserver-xorg

---

### Post by cilynx on 2007-01-14
If you were ever trying to get the cool 3D stuff working (compiz, beryl, etc..), then you probably installed Xgl (a separate XServer than Xorg) somewhere along the lines whether you knew it or not.  To get back to the standard desktop and a working system, follow riven0 above.

---

### Post by konungursvia on 2007-01-14
> **riven0 said:**
> Okay, cilynx may have the solution here. First, try removing xserver-xgl:



Reinstall the xserver (this is probably redundant, but its better to be safe than sorry :) )



Then  reconfigure everything:

Aah, interesting. xserver-xgl wasn't installed, it said, so I installed it again. That did it! Thanks!

---

### Post by konungursvia on 2007-01-14
Well it runs, but I'm not sure it's 100% correctly configured. As before, I notice interference/ jumping on the lcd monitor, as though electrical surges or memory leaking were happening. Is it possible to be configured correctly enough to display all right in 1280x1024, but incorrect enough that the Hz rate or other setting is a bit wonky?

---

### Post by riven0 on 2007-01-14
It's possible, but you'll have to know your monitors vert and hz rate. Usually the reconfiguration should fix it for you...:-k  but if it doesn't, you may have to do a google search for your monitor's info.

Otherwise you can play around with the xorg.conf file yourself and input different values into you hit the right one. 
I've done this before on a different Linux distribution and I got it working fine, but be careful! Usually, the xserver will just throw you an error if you put in the wrong values, but if it doesn't, you may have a burned out monitor!  

Otherwise, someone else may have a better suggestion...

---

### Post by konungursvia on 2007-01-15
Thanks to all you great folks for the help, this is why Ubuntu is the best.

---

