---
title: "It is going to be bigger"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by arvacon on 2008-01-21
Sometimes when i log in,the desktop's resolution it is changed without reason,If i log off and log on again,then it is coming back to the normal condition.What is wrong? Is this a bug?

---

### Post by Black_Heart on 2008-01-21
i think its just the video card, cuz my radeon 9250 does the same thing. I had to update my opengl drivers, and change the resolution in both **Screen resolution** and **screens and graphics** to get it to stick to one resolution... what video card do you have installed?

---

### Post by arvacon on 2008-01-21
my graphics card is nvidia fx5700le agp 8x.

---

### Post by gangrelsurf on 2008-01-21
are you using the nvidia restricted drivers? If so try this:
```
sudo nvidia-settings
```
go to 'X Server Display Configuration' and make it like you want, then click 'save to X configuration file'

---

### Post by arvacon on 2008-01-21
I went there but I did't change something.I just made a save.Will this solve the problem?

---

### Post by gangrelsurf on 2008-01-21
I think so. Give it a reboot and see...

---

### Post by arvacon on 2008-01-21
it is not doing it every time,so we will see at next reboots.
thanks!

---

### Post by arvacon on 2008-01-22
It worked finally! Thank you very much for your help!

---

