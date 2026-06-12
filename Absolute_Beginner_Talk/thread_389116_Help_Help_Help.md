---
title: "Help Help Help"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by viola breedlove on 2007-03-20
I recently loaded ubuntu on my computer and It was working great on my monitor at work.  then I took it home and I can tell that it starts up, but right as the desktop should start, where it asks for your username and password, my monitor at home goes black and says no signal, I use my samsung hdtv as my monitor but it has the right cord and everything, can anyone please help me, I really want to start using linux because I hate windows but I can't see anything

---

### Post by taurus on 2007-03-20
You need to reconfigure your X again when you switch monitors.  Boot into recovery mode from GRUB menu and at the prompt, type

```
dpkg-reconfigure -phigh xserver-xorg
```
Then, you can reboot with

```
shutdown -r now
```

---

### Post by viola breedlove on 2007-03-20
thank you, thank you, I will try that when I get home, maybe you could help me with one more problem??  I backed up my old hard drive before installing ubuntu, but i did the backup disc with nero (a windows program) do you think ubuntu will be able to recognize the files on my hard drive since they are all saved with windows file systems??

---

### Post by taurus on 2007-03-20
Ubuntu should be able to read it.  Just insert it into a drive and see if the automout would mount it.  Otherwise, you can always mount the CD by hand from a terminal.

---

