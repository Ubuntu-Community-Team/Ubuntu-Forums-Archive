---
title: "Configure ATI driver"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Luffer on 2008-03-30
Right, so I've managed to install the ATI driver for the website, but after installing it tells you to use aticonfig to setup options.

Running aticonfig lists a load of commands, the main one (I think) being:

 1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf

Now when I type that command into the terminal it tells me:

james@james-laptop:~$ aticonfig --initial --input=/etc/x11/xorg.conf
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

So what's up with that? I do have an xorg.conf file in etc/x11/ but it seems it can't find it.

---

### Post by overdrank on 2008-03-30
> **Luffer said:**
> Right, so I've managed to install the ATI driver for the website, but after installing it tells you to use aticonfig to setup options.

Running aticonfig lists a load of commands, the main one (I think) being:

 1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf

Now when I type that command into the terminal it tells me:

james@james-laptop:~$ aticonfig --initial --input=/etc/[COLOR="Red"]x[/COLOR]11/xorg.conf
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

So what's up with that? I do have an xorg.conf file in etc/x11/ but it seems it can't find it.

Hi and that should be a capital X

---

### Post by Luffer on 2008-03-30
Thanks for spotting that, not used to case sensitive filenames! But it still didn't work:

james@james-laptop:~$ aticonfig --initial --input=/etc/X11/xorg.conf
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

so what now?

---

### Post by Luffer on 2008-03-30
To answer my own question and help others with a similar problem, it turns out you need to run it as super user. So:

$ sudo aticonfig --initial --input=/etc/X11/xorg.conf

Then it works perfectly! Now I've got the proper widescreen resolution and 3D support, fantastic..... It all looks brilliant.

It's a shame these things are never explained properly to begin with, new users like myself have to spend so much time just trying to figure out these basic things. If only they just said you need to use sudo to start with!

---

