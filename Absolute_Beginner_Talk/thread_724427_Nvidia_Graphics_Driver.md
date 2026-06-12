---
title: "Nvidia Graphics Driver"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by RyviusRan on 2008-03-14
Decided to install new drivers, but ran into a problem when I was installing.

when I ran the command through the terminal it said "must run as root"

can anyone tell me how can I do that?

---

### Post by taurus on 2008-03-14
Just put a **sudo** in front of the command if you need root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by {BzF}~JOKesTER on 2008-03-14
Type "sudo" Before The Command.

Example:

sudo apt-get autoclean

Hope This Helps!!!

If It Does Than Hit "Thanks" {You Can Always Hit It Over And Over If You Really Like Me:):):biggrin:}

---

### Post by thisismalhotra on 2008-03-14
> **RyviusRan said:**
> Decided to install new drivers, but ran into a problem when I was installing.

when I ran the command through the terminal it said "must run as root"

can anyone tell me how can I do that?

Or why bother ... use ENVY it does all for you .. 

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by SpenceMakesSense on 2008-03-14
Sudo might sork but last time I tried installing NVIDIA drivers that I got from the webtsite it wouldnt get very far. I think they want you to leave the GUI and install from CLI. ctrl+alt+F1  should get you there and ctrl+alt+F7 will get you back to GUI

---

### Post by SOULRiDER on 2008-03-14
> **SpenceMakesSense said:**
> Sudo might sork but last time I tried installing NVIDIA drivers that I got from the webtsite it wouldnt get very far. I think they want you to leave the GUI and install from CLI. ctrl+alt+F1  should get you there and ctrl+alt+F7 will get you back to GUI

The best way to do it is to install from the repositories.
```
sudo aptitude install nvidia-glx
```should install the drivers, all thats left is to make xorg use them by changing "nv" to "nvidia" in the driver section of
```
/etc/X11/xorg.conf
```

---

