---
title: "MAME in Ubuntu?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2006-09-30
Is there a way I can get the MAME emulator in Ubuntu?

Thanks.

---

### Post by reacocard on 2006-09-30
```
sudo apt-get install xmame-sdl
```

---

### Post by alex-desktop79 on 2006-09-30
alex@alex-desktop:~$ sudo apt-get install xmame-sdl
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xmame-sdl

---

### Post by madmetal on 2006-09-30
give a look at synaptic..

---

### Post by lukew on 2006-09-30
> **alex-desktop79 said:**
> alex@alex-desktop:~$ sudo apt-get install xmame-sdl
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xmame-sdl

Looks like you need to add some repos!

I use a gui called gxmame to browse through my ~= 6000 roms!! You can download snaps/flyers/titles etc!! Adds a lot to your mame experience!!

I hope this helps.

Luke

---

### Post by alex-desktop79 on 2006-10-01
wich repos do i want?

---

### Post by reacocard on 2006-10-01
Add the Universe and Multiverse repositories as described here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by fng on 2006-12-02
> **lukew said:**
> I use a gui called gxmame to browse through my ~= 6000 roms!! You can download snaps/flyers/titles etc!! Adds a lot to your mame experience!!Luke

that frontend isn't updated anymore since 2003
[http://gxmame.sourceforge.net/downloads.php](http://gxmame.sourceforge.net/downloads.php)

---

