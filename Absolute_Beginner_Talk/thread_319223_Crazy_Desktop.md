---
title: "Crazy Desktop"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by black_ice on 2006-12-15
hello all ,, 

i was doing some configuration and i restart X alt-ctrl-backspace and when i back to system i cannot find any item on my desktop every thing is gone and when  i want to add file or drag file to it ,, it refuse and there is nothing created and i cannot change my desktop background also i cannot make aleft click on it !!!! help plz 

thanx for all

---

### Post by Patrick-Ruff on 2006-12-15
restart your computer.

---

### Post by bodhi.zazen on 2006-12-15
> **black_ice said:**
> hello all ,, 

i was doing some configuration and i restart X alt-ctrl-backspace and when i back to system i cannot find any item on my desktop every thing is gone and when  i want to add file or drag file to it ,, it refuse and there is nothing created and i cannot change my desktop background also i cannot make aleft click on it !!!! help plz 

thanx for all

Drop to your CLI (Ctrl-alt-F1):

```
sudo /etc/init.d/gdm stop
```

Now I know you have a back up xorg.conf ;)

Restore from backup and re-start X !

If you do not have a back up:
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```

Now open a terminal and type:> I will back up system files before I alter them100 times :D

---

