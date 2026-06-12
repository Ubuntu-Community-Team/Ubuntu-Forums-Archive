---
title: "Small Screen size"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by JoeyK232 on 2006-07-12
the Screen size of my desktop is only portion in the center of my screen. Mos t of the vertical space is used but there is a good inch on each side of the screen. How can i fix this?

---

### Post by dishrat on 2006-07-12
Have you tried adjusting you nonitor settings?

---

### Post by JoeyK232 on 2006-07-13
the only setting i could think of to change was my resolution, but the only option i have for that is 1024x768

---

### Post by slimdog360 on 2006-07-13
what sort of monitor do you have, widescreen? 15"? whats the natural resolution?I can tell you how to fix it but you will have to give some details.

---

### Post by Perfect Storm on 2006-07-13
press <ctrl>+<alt>+<F1>

```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```

if you are using KDE change gdm to kdm

---

### Post by JoeyK232 on 2006-07-13
<ctrl>+<alt>+<F1> just closed out of the desktop and left me with a command line.
----------------
i have a laptop with a wide screen

---

### Post by Perfect Storm on 2006-07-13
Yes, then write the commands that it's shown.

---

### Post by JoeyK232 on 2006-07-13
ah, sorry, dont know how i missed that, but how do i know if i'm using KDE?

---

### Post by JoeyK232 on 2006-07-13
ok, i figured out how to do that, and i put in what i think are all the right settings, but nothing changed.

---

### Post by tom407 on 2007-08-28
I have exactly the same problem. Once I put the code in what settings are the best?

---

### Post by johanvanzyl80 on 2007-08-29
Hi 

I just a got a HP Compaq 6910p notebook with a 14.1 widescreen. The display size is supposed to be 300 x 190 mm, but Gnome only uses a part of the monitor. It has two vertical black lines on both sides. I've played around with resolution in xorg, but only the 640x480 option works. 
I found out that the native resolution for this notebook is 1280x800. The video card is an Intel GM965/PM965/GL960.
Does anyone have any idea?

Thanks
Joe

---

