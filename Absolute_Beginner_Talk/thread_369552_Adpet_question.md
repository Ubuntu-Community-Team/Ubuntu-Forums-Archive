---
title: "Adpet question"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Imsati on 2007-02-24
I tried adding two repositories and added them wrong. When I try to open Adept, I get this error message:

The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

So I tried apt-get update and got this message:

E: Malformed line 1 in source list /etc/apt/sources.list (dist)

How do I get rid of the last two repositories I entered? I tried opening /etc/apt/sources.list and deleting them, but it would not let me save it.

---

### Post by benfindlay on 2007-02-24
you need to open the file with super user priviliges type the following:

```
sudo gedit /etc/apt/sources.list
```

Then delete the relevent lines and click save before closing.

If you're editing via terminal or ssh or the like, then type this instead:

```
sudo nano /etc/apt/sources.list
```

This will open it in the terminal text editor

Hope this helps!

---

### Post by benfindlay on 2007-02-24
just had another thought, if you are editing with super user priviliges, are you doing it whilst a package manager or update program is running, this will present a problem also i believe as the file you're editing will be in use!

HTH

---

### Post by Imsati on 2007-02-24
I'm on KDE, so I used kdesu instead of gedit. Had this show up in the Terminal:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
sh: /etc/apt/sources.list: Permission denied

The nano command opened up the file in the Terminal, but how I go about saving it once I made the changes?

--Jay (Feels like a newbie again)

---

### Post by Imsati on 2007-02-24
Hey, I got it! Thanks so much for your help!

--Jay (who now knows ^ means Ctrl :P )

---

### Post by benfindlay on 2007-02-24
no problems.

I find that nano is really worth getting to grips with. I use KDE myself too (got bored of gnome), but I do most of my work on my box via an ssh terminal from a Winblows computer ](*,). As a result nano is the best way for me to edit stuff (short of vncing into the computer itself just to look at stuff graphically). Anyways, ciao for now

---

