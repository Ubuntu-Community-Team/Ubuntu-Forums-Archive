---
title: "Virtual Box"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-06-15
I have virtual box tagged with a green box in Synaptic but not showing anywhere else! How do I get it into applications so that I can use it?

---

### Post by Seisen on 2007-06-15
You can go into the terminal and type this

```
sudo VirtualBox
```

---

### Post by lazyart on 2007-06-15
Not in Applications>System Tools?

---

### Post by Benbow on 2007-06-15
No, I also have the same problem with gzip but when I used terminal for Virtual Box it opened but left this message -
benbow@benbow-desktop:~$ sudo VirtualBox
Password:
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
strange eh!

---

### Post by starcraft.man on 2007-06-15
Ok, this may be a bit basic but you did actually add the [right repo]("http://www.virtualbox.org/wiki/Downloads") and got the gpg key right? I mean Virtual Box isn't in the main repos by default or any of the universe... If you installed it properly, that is a weird message to get... maybe it needs reconfiguring.

Open a terminal and drop this in:
```

sudo /etc/init.d/vboxdrv setup 
```

Oh and run it twice, some people report it doesn't work first time. That should do it if its installed right.

---

