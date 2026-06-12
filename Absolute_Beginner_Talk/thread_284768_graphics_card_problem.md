---
title: "graphics card problem"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by kman14 on 2006-10-26
very much a linux newbie.
i was basically copying terminal commands from this forum to activate my graphics card.
i ended up in xorg (i think).
i had to swap "nv" to "nvidia" and then reboot.
i very stupidly typed "nvida" and then control alt b/space as instructed.
when it restarted i'd lost the gui(?) because it didn't know what "nvida" was.

i don't have any clue how to fix this.

any help would be much appreciated

---

### Post by RoyArne on 2006-10-26
> **kman14 said:**
> 
i had to swap "nv" to "nvidia" and then reboot.
i very stupidly typed "nvida" and then control alt b/space as instructed.
when it restarted i'd lost the gui(?) because it didn't know what "nvida" was.


Log in at the console and edit you xorg.conf file with 

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by kman14 on 2006-10-26
thanks for that.
now i haven't done this yet - basically because once i do i will have to come back here and ask what i need to do next.
i'm really new to this.
thanks for the speedy reply though.

---

### Post by CatKiller on 2006-10-26
> **kman14 said:**
> i will have to come back here and ask what i need to do next.

As before, find the Device section and change the driver to "nvidia". Page Up/Down to scroll, Ctrl-X to quit.

Good luck.

---

### Post by kman14 on 2006-10-31
thanks for the help guys.

all's good.

---

