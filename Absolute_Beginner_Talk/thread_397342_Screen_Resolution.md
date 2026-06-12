---
title: "Screen Resolution"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by c-breakdown on 2007-03-30
Everything is way too big on the screen.  While I was running the install I couldn't even see the Forward and Back buttons without hiding the bottom menu.  

I'm not sure what resolution I need so is there an easy way to try some different ones out?

---

### Post by gwoodard on 2007-03-30
First can you see the top menu bar? if you can then go to system ---> preferences ---> screen resolution...

---

### Post by c-breakdown on 2007-03-30
The only options it has are 800x600 (what it is currently) and 640x480 (which is makes everything even bigger).

Is there any way to make it so I have more options available to me?

---

### Post by ed-j on 2007-03-30
Hi !

What version of Ubuntu are you using and what is your grahics card or adapter and your monitor?

Glad to help if I can!  :-)

---

### Post by c-breakdown on 2007-03-30
I'm using ubuntu 6.10.  I have a basic Dell monitor and I don't know my video card.  Is there somewhere I can look to find that information?

---

### Post by c-breakdown on 2007-03-30
Ubuntu: 6.10
Video Card: GeForce4 MX
Monitor: DELL E772c

Anyone know how to add resolutions that aren't showing up as options?

---

### Post by kc5hwb on 2007-03-30
This makes a backup of the file you're about to change.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

This will stop GDM

```
sudo /etc/init.d/gdm stop
```

This will auto detect everything and you will be able to select the resolutions you wish to use.

```
sudo dpkg-reconfigure xserver-xorg
```

Will restart your GDM

```
sudo /etc/init.d/gdm start
```

---

### Post by ed-j on 2007-03-31
kc5hwb

Thanks for the codes!:)

---

