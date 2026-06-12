---
title: "Best distro for an hd5450?"
date: 2013-12-04
forum: Any Other OS
---

### Post by mamamia88 on 2013-12-04
I have an older computer with an hd5450 connected to my tv I'd like to use as an htpc.   I'm wondering which distro will give me the best performance with this video card? Edit it's already running xubuntu.   It experiences screen tearing in vlc but i didn't notice any in xbmc this is using the catalyst driver.

---

### Post by sudodus on 2013-12-04
It is great that Xubuntu and xbmc play video without issues.

Maybe Lubuntu, LXDE or Openbox sessions can play more difficult video clips without issues. Which version are you running, 13.10 or 12.04 LTS? Unfortunately Lubuntu 12.04 has passed end of life, but there are other respins, LXLE and Bodhi Linux with LTS, that you might try.

---

### Post by mamamia88 on 2013-12-04
I don't particularly care for lxde tbh.  I'm thinking arch maybe just because it will always have the latest driver and kernel.   But then again if i want to use catalst it looks like a pia after every udate

---

### Post by mips on 2013-12-04
Have a look at OpenELEC but I have no idea how well they support AMD GPUs. These days s GT610 will do the job if you are prepared to splash out a bit of cash.

---

### Post by mamamia88 on 2013-12-04
> **mips said:**
> Have a look at OpenELEC but I have no idea how well they support AMD GPUs. These days s GT610 will do the job if you are prepared to splash out a bit of cash.

Yeah not really willing to spend too much.  I'm actually thinking of just copying the files onto my ps3 via usb and not worrying about it tweaking everything to try and get best performance or scrutinizing everything.

---

### Post by mips on 2013-12-04
Just try the generic or generic oss builds I'm pretty sure you will be fine. Openelec is really cool.

---

### Post by mamamia88 on 2013-12-04
> **mips said:**
> Just try the generic or generic oss builds I'm pretty sure you will be fine. Openelec is really cool.

But can you do other stuff besides just xbmc?  I'd rather use a full distro

---

### Post by sudodus on 2013-12-05
Bodhi linux uses the Enlightenment desktop. You might like it.

[http://www.bodhilinux.com/](http://www.bodhilinux.com/)

---

### Post by mikewhatever on 2013-12-07
Screen tearing in XFCE is, apparently a known problem, because the window manager has had no [sync to vblank support]("http://www.webupd8.org/2013/10/xfwm4-4110-released-with-sync-to-vblank.html").

---

### Post by mips on 2013-12-07
> **mikewhatever said:**
> Screen tearing in XFCE is, apparently a known problem, because the window manager has had no [sync to vblank support]("http://www.webupd8.org/2013/10/xfwm4-4110-released-with-sync-to-vblank.html").

As far as i know thenew version has vblank support an yould always use something like compton or compiz to get rid of tearing.

---

### Post by mastablasta on 2013-12-08
i would also give openelec a go. it's a stripped down version of OS with XBMC. works great on RapberryPi.

---

