---
title: "Removing nVidia Drivers"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Sable683 on 2007-04-02
I am having trouble with my nVidia driver. I am not sure what I did, but right now I have no access to the gnome desktop. I have access to terminals tty1 to tty7, but don't know where to go from here.
How do I, and is it possible to reload the generic video driver that I had prior to playing around with the nVidia drivers? Any help is appreciated.

Thanks,

John

---

### Post by Bachstelze on 2007-04-02
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf
```

Spot the line that says :

```
        Driver          "nvidia"
```

and replace it with :

```
        Driver          "nv"
```

Then save the file (Ctrl+O, Enter to confirm), exit nano (Ctrl+X) and restart X :

```
sudo /etc/init.d/?dm restart
```

---

### Post by Sable683 on 2007-04-02
Awesome, Thank you... it worked like a charm!

---

