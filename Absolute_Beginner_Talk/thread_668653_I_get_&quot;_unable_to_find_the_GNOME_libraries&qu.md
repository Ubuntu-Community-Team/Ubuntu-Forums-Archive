---
title: "I get &quot; unable to find the GNOME libraries&quot; when i want to use ./configure"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-15
Hi
Thank you for reading my post
I have Ubuntu 7.10 and I want to install [http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/) version 5, problem is that when I issue ./configure it progress to some steps and then return :

" unable to find the GNOME libraries"

I googled and I found some suggestions but they looks to be old and not working.

for example:
```

sudo apt-get install gnome-core-devel
sudo apt-get install libgnome2-dev
sudo apt-get install libgnome-dev

```

did not help me.
what should I do?
Thanks

---

### Post by AndyCooll on 2008-01-15
Have you got build-essential installed?

IIRC you need to do this before you can use the make/configure process.

:cool:

---

### Post by legolas_w on 2008-01-16
Hi, thank you for reply.
I have build essential in place and the error come out when I try ./configure command, it is what the manual says.


thanks

---

### Post by Tenken on 2008-01-16
You can install it with apt-get (it's in the universe repository)

```
sudo apt-get mail-notification
```

and if you still want to build it yourself [this]("http://packages.ubuntu.com/gutsy/gnome/mail-notification") page has a complete dependency listing for the package.

---

### Post by Ripfox on 2008-01-16
bump this...the new version has all kinds of bells and whistles i want. I am stuck at "gnome libraries" too

---

### Post by Ripfox on 2008-01-16
I think it's looking for gnome-devel

---

### Post by Ripfox on 2008-01-16
configure: error: unable to find the GNOME libraries
????

no go so far...

---

### Post by Ripfox on 2008-01-16
It was libnotify-dev.

---

### Post by legolas_w on 2008-01-17
Hi
I installed libnotify-dev and I am still getting the same error.

Thanks.

---

### Post by Ripfox on 2008-01-17
Make sure you:

./configure --prefix=/usr (unless for some reason your GNOME
libraries are installed someplace weird).

And:

sudo apt-get build-dep mail-notification

Refer to this thread [http://ubuntuforums.org/showthread.php?t=135522](http://ubuntuforums.org/showthread.php?t=135522) for help, I hacked around with it and actually got it to make and install. Works awesome, AND there are lot's of cool features.

Hit me back if I missed anything.

---

### Post by macogw on 2008-01-17
> **Tenken said:**
> You can install it with apt-get (it's in the universe repository)

```
sudo apt-get mail-notification
```

and if you still want to build it yourself [this]("http://packages.ubuntu.com/gutsy/gnome/mail-notification") page has a complete dependency listing for the package.

Or, instead of reading the dependency list and manually getting them individually, you can do ```
sudo apt-get build-dep mail-notificatin
``` to install all of the build dependencies.

---

### Post by Ripfox on 2008-01-20
Make sure you:

./configure --prefix=/usr (unless for some reason your GNOME
libraries are installed someplace weird).

And:

> sudo apt-get build-dep mail-notification


                                ^
                                ^
                                ^
                                ^

---

### Post by jeremykendall on 2008-02-18
I just went through trying to build Mail Notification 5.0 on Gutsy and I ran into "unable to find the GNOME libraries" myself.  I resolved that by installing gnome-core-devel, libnotify-dev, and libgnome2-dev via Synaptic.

In order to ./configure without any errors and with SSL enabled, I also had to install build-essential, libgmime-2.0-2-dev, and libssl-dev, all via Synaptic.

Don't forget to log out (or reboot) before using mail notification or you may get some unexpected behavior out of the app.

---

