---
title: "Screen Resolution, again"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by norm47 on 2008-04-02
Good evening,
Xubuntu 7.10, running on an old intel BX440 mobo.

After I first installed, I could select any resolution from 640 x480 up to 1280x1024. I selected 1024x768 to suit my 17'' HP CRT.

I rebooted today, after having shut down for some storms, and I get only 640x480 or 800x600 :confused:

No matter what I do in xorg.conf, thats all I get. xorg.conf seems to have identified the monitor and device ok as GEForce2 MX200 and HP D8901

So where do I look next? I've rtfm man xorg.conf and dont see any hints there. Maybe I dont understand where X gets its defaults from?

Norm

---

### Post by ajmorris on 2008-04-02
hi there,
you can try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

if this does not bring back your screen resolutions, could you please post your xorg.conf as i need to see whether you are using metamodes or the other method before i tell you how to change it manually.

AJ

---

### Post by norm47 on 2008-04-02
OK,
tried that once before and no joy. Did it again and it came up with a different monitor model, This time a whole spread of resolutions and rates:confused:

Cool. I'll stick with it for now, see what happens next boot... It's storming again


Norm

---

### Post by erginemr on 2008-04-02
You can also select the driver and modes yourself with:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by shadowtroopers on 2008-04-02
can you try this:
sudo dpkg-reconfigure xserver-xorg

---

