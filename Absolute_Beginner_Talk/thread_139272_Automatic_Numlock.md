---
title: "Automatic Numlock"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by 1337sithlord on 2006-03-03
Every time i start ubuntu, numlock is on and its a pain to constantly switch the keys back... especially when i type my password to download updates and i cant figure out why the password is wrong lol.  Is there any way to disable this "feature"?  Ty.

---

### Post by Pragmatist on 2006-03-03
Check this out:
[http://www.linuxjournal.com/node/4370/print](http://www.linuxjournal.com/node/4370/print)
Looks like you use the **setleds** program and to make it permanent you put it in a startup script.

---

### Post by 1337sithlord on 2006-03-04
Its probably some file saying keycode this = keycode that.  I checked every file for the phrase "Setleds" and commented each one and it didnt fix it.  Im not doing that for every file that contains "keycode" lol so i guess il just live with it.

---

### Post by aysiu on 2006-03-04
This shouldn't be happening. The default behavior in both Gnome and KDE is to have numlock **off**.

Do you have numlockx installed? Try ```
sudo apt-get remove numlockx
```

---

### Post by BoyOfDestiny on 2006-03-05
[QUOTE=aysiu]This shouldn't be happening. The default behavior in both Gnome and KDE is to have numlock **off**.

Do you have numlockx installed? Try ```
sudo apt-get remove numlockx
```[/QUOTE]

I don't think it's Ubuntu... Check your bios. Some machines have numlock on by default at boot (first thing I disable too =) )

---

