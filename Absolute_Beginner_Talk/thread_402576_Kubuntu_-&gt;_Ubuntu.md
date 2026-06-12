---
title: "Kubuntu -&gt; Ubuntu"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Durden on 2007-04-05
I installed Ubuntu then used synaptic to install the kubuntu-desktop stuff which changed my loading screen (The blue kubuntu with the progress bar when the OS is loading, not the loading screen for the window manager). Anyway i've switched back to Ubuntu desktop due to some quirky behavior in KDE and was wondering where I would change this back to the regular Ubuntu loading screen. Any help would be greatly appreciated. Thanks

-todd

---

### Post by Razorback on 2007-04-05
I believe it is selected at the login screen.  Change using change session on the screen.

---

### Post by Durden on 2007-04-05
I'm not talking about the window manager loading screen. This is during the boot cycle.

---

### Post by Razorback on 2007-04-05
Sorry for that.  How about this?

[http://ubuntuforums.org/showpost.php?p=2395883&postcount=1](http://ubuntuforums.org/showpost.php?p=2395883&postcount=1)

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Durden on 2007-04-05
Don't want to uninstall kubuntu-desktop as there is a lot of stuff there worth keeping. Just need to switch the boot screen. Thanks though.

---

### Post by Razorback on 2007-04-05
ok, then how about this......

[http://ubuntuforums.org/showthread.php?t=402516&highlight=change+splash+screen#post2409067](http://ubuntuforums.org/showthread.php?t=402516&highlight=change+splash+screen#post2409067)

---

### Post by Neobuntu on 2007-04-06
> sudo aptitude install gdm

If you are talking about the login manager screen.

After install, Be sure to select from your DM's on the login menu before signing on.

---

### Post by Durden on 2007-04-06
I think i've said 3 times now "not the login screen". I appreciate the bumps but if you don't know what the boot screen is you're of no help here.

---

### Post by Razorback on 2007-04-06
> **Durden said:**
> I think i've said 3 times now "not the login screen". I appreciate the bumps but if you don't know what the boot screen is you're of no help here.

My last post tells you how to do it :)

[http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/](http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/)

---

### Post by Durden on 2007-04-06
Thanks for the link Razorback, that seems to be what I'm needing:

sudo update-alternatives --config usplash-artwork.so

---

### Post by Neobuntu on 2007-04-06
> sudo update-alternatives --config usplash-artwork.so

You should also run

> sudo dpkg-reconfigure linux-image-`uname -r`

---

### Post by Neobuntu on 2007-04-06
For those who don't know, I think of them in this order.

1. Grub splash screen(optional limited graphic).

2. Boot splash (kernel). Ubuntu, Kubuntu,Xubuntu or custom. (This post)

3. GDM or KDM login theme (NOT SEEN until "Log Out", IF you use auto login).

4. Gnome (optional) DM splash OR KDE (optional) DM splash

Optional because you may rather, just go straight to your desktop and it's background.

Isn't open software great!

---

### Post by Neobuntu on 2007-04-06
Here is a my link to Grub splash coolness!

WITH splash file links.

[http://ubuntuforums.org/showthread.php?p=2411900#post2411900](http://ubuntuforums.org/showthread.php?p=2411900#post2411900)

---

