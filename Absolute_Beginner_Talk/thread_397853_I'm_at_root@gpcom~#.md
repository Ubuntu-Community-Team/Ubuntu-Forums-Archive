---
title: "I'm at root@gpcom:~#"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-03-31
I restarted in the recovery mode and then after it does all the checks and whatever it ends up here: root@gpcom:~#  Now I don't know what I need to do. Thanks for the help.

---

### Post by Maestro23 on 2007-03-31
> **captgadget said:**
> I restarted in the recovery mode and then after it does all the checks and whatever it ends up here: root@gpcom:~#  Now I don't know what I need to do. Thanks for the help.

Why did you boot into Recovery mode? What are you trying to do?

---

### Post by captgadget on 2007-03-31
I followed the steps on a website on installing the latest ATI drivers. Now, I have a problem with X11 and I need to get in there and fix it. So I started in the recovery mode. Maybe I'm not working at it from the right direction.

---

### Post by Maestro23 on 2007-03-31
> **captgadget said:**
> I followed the steps on a website on installing the latest ATI drivers. Now, I have a problem with X11 and I need to get in there and fix it. So I started in the recovery mode. Maybe I'm not working at it from the right direction.

Got a link to the guide you are following?

---

### Post by captgadget on 2007-03-31
This is where I started:

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by arron on 2007-03-31
bleeding edge can = bad news for newer users.  I'm not sure how to get you up and going, but i can recommend a good how-to for ubuntu - ati drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

or (this one i like more, and has current drivers):

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Good luck.

---

### Post by Maestro23 on 2007-03-31
> **arron said:**
> bleeding edge can = bad news for newer users.  I'm not sure how to get you up and going, but i can recommend a good how-to for ubuntu - ati drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

or (this one i like more, and has current drivers):

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Good luck.

Beat me to it arron.  Getting ready to post these links myself.  Just installed the latest ATI driver myself.

---

### Post by arron on 2007-03-31
Hrmmm one thing i could recommend to try is to reconfigure the X server, at the prompt try:

```
 sudo dpkg-reconfigure xserver-xorg
```

Go threw the setup, and try to configure it best u know how.  then when its done run:

```
 startx
```

 to see if it will run.  If it does, take the cd out, and reboot and cross your fingers.

---

### Post by captgadget on 2007-03-31
When I started in recovery mode it tells me my error in X11. Is there a way to reboot in terminal so I can reconfig X11?

---

### Post by captgadget on 2007-03-31
It's not perfect yet but I'm getting closer. At least it got booted up. Thank everyone for all their assistance. This has gotta be the worlds greatest forum.

---

### Post by arron on 2007-03-31
> **captgadget said:**
> This has gotta be the worlds greatest forum.

:biggrin: agreed! this place rocks!  Good luck getting it backup and running.

---

### Post by captgadget on 2007-03-31
Well, I was ok until I rebooted. In configure xserver my video card is in an AGP slot but that is not one of the choices. I have to select a PCI and according to the lspci it tells me it's PCI 01:00:1, but xserver doesn't like that choice. Then, how do you save the resolution in xserver? I tried to place an asterisk there but I can't.

---

