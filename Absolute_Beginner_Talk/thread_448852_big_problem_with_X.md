---
title: "big problem with X"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-05-19
I ran a command given to me by someone, and it looked like it fixed my problems. it removed alto of packages, more packages then he or i assumed originally. My X Server is not disabled, i can only get into command prompt. and i dont knwo how to fix it. says no drivers enabled for my nvidia card. the default location /etc/X11/XDrg.conf does not exist.

i am currently on my damn windoze partition only way i can get on here at the moment.

all help is appreciated

---

### Post by k33bz on 2007-05-19
original problem is here [http://ubuntuforums.org/showthread.php?t=448775]("http://ubuntuforums.org/showthread.php?t=448775")

some one please help with this new problem i am facing

---

### Post by k33bz on 2007-05-19
anyone????

---

### Post by taurus on 2007-05-19
Maybe all you need is to reconfigure your X again.  Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure xserver-xorg
```
If you're not sure about a question, just use the default.  And use **vesa** for your graphic for now until you get X up and running again.  Then, install the driver for your card.  Once done, reboot.

```
shutdown -r now
```

---

### Post by k33bz on 2007-05-19
ok, thanx, just in case, how do i run in vesa?

---

### Post by taurus on 2007-05-19
Vesa is a generic driver for a graphic card and you can't run it by itself.  When you get to a section about driver for your video card, pick **vesa** from the list.

p.s.  And you may want to change the title of your thread.

---

### Post by k33bz on 2007-05-19
ok im in, so what else do i need to do, im running on the generic, didnt see the one that fits my card

and how do i cahnge the titel of the thread, :(

---

### Post by taurus on 2007-05-19
Which graphic card do you have?

```
lspci
```

---

### Post by k33bz on 2007-05-19
VGA compatible controller: nVidia Corporation NV43 [GeForce 6600]

so do i just go back into recovery mode and pick VGA ???

oh and thanx for changing the thread title

---

### Post by Bachstelze on 2007-05-19
No, the vga driver is even more outdated than vesa is, it's for really, really, really, *really* old cards. Use the nv driver if you don't want to install the nvidia ones.

---

### Post by taurus on 2007-05-19
Well, you can install nVidia driver by System -> Administration -> Restricted Drivers Manager and put a check on Enabled for  NVIDIA accelerated graphics driver.  Click Close and reboot.

---

### Post by k33bz on 2007-05-19
ok, thanks Hymn, again lol

---

### Post by k33bz on 2007-05-19
> **taurus said:**
> Well, you can install nVidia driver by System -> Administration -> Restricted Drivers Manager and put a check on Enabled for  NVIDIA accelerated graphics driver.  Click Close and reboot.

oh ya, duh, i cant think today, i forgot i did that before, 
thanks

---

### Post by siucdude on 2007-05-21
did you ever get it working, I have a geforce 6600 same card on my laptop and I can't run it under Nvidia drivers, under nv it works ok but the resolution is a bit off, but under nvidia it loads to through the boot and then goes to this black screen right before login and I can't press nothing, I tried ctrl+Alt+f* and no luck just have to do a hard reboot and then boot safe mode, 

anyways let me know if you get it working.

Thanks

---

