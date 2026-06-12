---
title: "ubuntu game instalation."
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by endo666 on 2007-08-12
well im trying to install ut2k4 and it asks for the installation path. which it defaults to /usr/local/games/ut2004

problem is that it says i have no write permission. so what do i need to do

---

### Post by eapache on 2007-08-12
install it as root (sudo).

---

### Post by endo666 on 2007-08-12
i apologize but i need very specific instructions

---

### Post by eapache on 2007-08-12
what command are you using to install it now?

---

### Post by djchandler on 2007-08-12
What's the format of the file you are downloading?

---

### Post by endo666 on 2007-08-12
this is what a budy of mine told me to do

Copy the file linuxinstaller.sh off the install disc onto your desktop. Right click on it, and select "Properties". A Properties window comes up, click on the "Permissions" Tab. Check the "Allow executing this file as a program", then click "Close". Then double click on the "linuxinstaller.sh" on your desktop, and it should start an installer, and you just need to follow the on screen instructions (usually just clicking next a couple times works).

then i went into the terminal and typed sudo /endo/desktop/linux-installer.sh

im think this is wrong though

---

### Post by endo666 on 2007-08-12
> **djchandler said:**
> What's the format of the file you are downloading?

im trying to install ut 2004

---

### Post by eapache on 2007-08-12
in terminal type```
cd Desktop
```and then```
sudo ./linux-installer.sh
```

cd is used to change directories, so it navigates to your desktop. ./ runs the program, and sudo runs it as root. If the installer is graphical, I would replace sudo with gksudo though.

---

### Post by endo666 on 2007-08-12
looks to be working. but why wouldnt the way my friend told me work. thats how he installed it.

---

### Post by eapache on 2007-08-12
he probably changed the location to somewhere he had access to. It is best to run it from root thought so that it ends up in the right spot.

---

### Post by endo666 on 2007-08-12
ok it installed but it goes to the splash screen then that just goes away and the game doesnt start

---

### Post by djchandler on 2007-08-12
Old post edited. I have no idea what you are doing, but I'd like too. I found an old website about a conversion at [http://www.thehaus.net/AltOS/Linux/ht-utlinux.shtml](http://www.thehaus.net/AltOS/Linux/ht-utlinux.shtml).

DJ

---

### Post by endo666 on 2007-08-12
> **djchandler said:**
> Old post edited. I have no idea what you are doing, but I'd like too. What version are we talking about? I found an old website about a conversion at [http://www.thehaus.net/AltOS/Linux/ht-utlinux.shtml](http://www.thehaus.net/AltOS/Linux/ht-utlinux.shtml).

DJ

im using ubuntu 7

and i couldn't find the version number for the game. but im sure it is the first version.

---

