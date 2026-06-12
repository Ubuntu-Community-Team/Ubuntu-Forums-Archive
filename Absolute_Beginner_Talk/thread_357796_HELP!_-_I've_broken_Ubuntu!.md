---
title: "HELP! - I've broken Ubuntu!"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by mells on 2007-02-10
I was playing with setting up my network drives and now I cant load gnome! Everytime I load the system. I log in and then as the gnome desktop is starting only half the screen loads and I get this message from bug buddy saying the gnome-pannels caused the crash.

I have tried to restore gnome with

> sudo apt-get update
> sudo apt-get upgrade

then 

> sudo apt-get install gdm ubuntu-desktop

I was hoping the above would fix what I had broken but it hasnt on reboot I get the same error message and no gnome.

Any ideas to how I can restore the gnome desktop back to its settings yesterday or load it with defaults?? I dont really want to reinstall the system (again).

Thanks

---

### Post by mendingo84 on 2007-02-10
try this. i hope it works since you have problems with your desktop...
> 
sudo apt-get install --reinstall xserver

---

### Post by mells on 2007-02-10
> **mendingo84 said:**
> try this. i hope it works since you have problems with your desktop...

Thanks, that doesnt work. It says

> E: Invalid Response

---

### Post by mells on 2007-02-10
> **mells said:**
> Thanks, that doesnt work. It says

got it to reinstall the 3 xserver modules.

rebooted and the same problem occurs still :confused:

---

### Post by Jussi01 on 2007-02-10
You could try:
```

sudo apt-get install gnome --reinstall
```

Cheers

Jussi

---

