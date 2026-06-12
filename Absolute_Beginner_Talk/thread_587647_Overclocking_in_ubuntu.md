---
title: "Overclocking in ubuntu"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-10-22
I need to overclock my GPU, but I don't believe ntune is available for linux.  Are there any other options

---

### Post by Dapman01 on 2007-10-23
bump?

---

### Post by Shazaam on 2007-10-23
From google...
[http://www.phoronix.com/scan.php?page=article&item=598&num=1](http://www.phoronix.com/scan.php?page=article&item=598&num=1)
[http://www.overclock.net/faqs/115417-how-overclock-your-nvidia-card-under.html](http://www.overclock.net/faqs/115417-how-overclock-your-nvidia-card-under.html)
[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

Many more hiding there. :)

---

### Post by Dapman01 on 2007-10-23
Thanks for posting
I downloaded nvclock, now how do I install it

---

### Post by nchase on 2007-10-23
there's actually a version of nvclock in the ubuntu repositories. type this into a terminal window
```
sudo apt-get install nvclock-gtk
```

alternatively, search for nvclock-gtk in synaptic.

---

### Post by DoorGunner on 2007-10-23
do you know what the comandline is to run nvclock? I have kubuntu and it doesnt show up in my menu..... tried nvclock nvclock-gtk. and it is installed

---

### Post by shad0w_walker on 2007-10-23
Install the officiall nvidia drivers and then run this when they are setup.

```
sudo nvidia-xconfig --cool-bits=1
```

This enables the overclocking options in nvidia-settings

---

### Post by DoorGunner on 2007-10-23
Ok I have the option in Xorg. but i still dont see the gui. Are you running the restricted module or other drivers?

---

### Post by shad0w_walker on 2007-10-23
Im running the restricted driver version, but its the same as the regular version of Nvidias drivers

Just try running 

```
gksu nvidia-settings
```

And look in GPU0 (Probably) and the clock frequencies section.

---

### Post by DoorGunner on 2007-10-23
thanks ..... works like a charm

---

