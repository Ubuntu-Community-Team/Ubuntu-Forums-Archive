---
title: "newbee help"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by jwazzz on 2007-01-25
I installed ubuntu edgy eft on my winxp pc, dual boot.  It installed and worked fine until I added the drivers for my nvidia geforce3, now it boots to a text screen. How can I back out the new drivers, would reinstalling ubuntu work? Im a total linux newbee.

---

### Post by dwblas on 2007-01-25
You should just have to reconfigure xorg.  If a backup of /etc/X11/xorg.conf was created by the install program, you should be able to copy the old version and be ok.

---

### Post by riven0 on 2007-01-25
To reconfigure xorg, run this command:

> sudo dpkg-reconfigure xserver-xorg

---

### Post by jwazzz on 2007-01-25
I appreciate you quick reply, but I've never used the text version, how would I check for a backup copy and use it?

---

### Post by halitech on 2007-01-26
I would guess it would be

```

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

```

but thats guessing at the backup name

you could also open nautilus as sudo

```

gksudo nautilus

```

so you could browse the ...never mind, X is broken

---

### Post by C-A on 2007-01-26
I can't help with your immediate problem. However, once you have rolled back to your old drivers check out [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install new/correct drivers.

---

### Post by dwblas on 2007-01-26
I think Gnome-Ubuntu comes with MidnightCommander.  Try sudo mc from the command line.  It's easier to use a GUI.  Become familiar with one of the GUI interfaces as they are very handy.  If it isn't there yet, key in
sudo ls /etc/X11/   (that's "el" and "es", not "eye" or one)
Look for an xorg.conf that ends with a "~", ".bak", or some other obvious backup file.  Also you could use apt-get install mc.  Hopefully this is the only time you get burned fingers.  Always back up before you change anything.

---

### Post by dwblas on 2007-01-26
I don't know what I was thinking - or rather not thinking.  The following is a link to to a Python program that configures the video card if you have an ATI or ***NVidia***.  I have not used it, so don't know if it needs xorg to run (which would be stupid since it sets up the video card).  A Python program does not.  Python + GUI does.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by jwazzz on 2007-01-26
Thanks all, I tried it all and still had problems so I reinstalled ubuntu, then ran ENVY, it worked!

---

