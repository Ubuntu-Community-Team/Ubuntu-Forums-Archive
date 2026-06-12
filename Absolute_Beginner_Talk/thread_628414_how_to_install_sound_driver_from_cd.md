---
title: "how to install sound driver from cd?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Gobbie on 2007-12-01
This is doing my head in!  I've lost sound & I don't think my onboard sound card is recognised.  I've got the drivers on cd but have no idea how to install them.  This is what I get..............

owen@owens-desktop:/media/cdrom0/LinuxDrivers/Realtek_Audio/realtek-linux-audiopack-3.5-6$ ./install
bash: ./install: /bin/sh: bad interpreter: Permission denied

I'm sure this should be easy.......please help!

---

### Post by szymon_g on 2007-12-01
try this : 

chmod +x /patch/.install

than
sudo sh /directory/.install

btw, are you sure your computer doesnt recognise it? try to install alsa-related packages

btw, what kind of card is it?

---

### Post by Gobbie on 2007-12-01
> **szymon_g said:**
> try this : 

chmod +x /patch/.install

than
sudo sh /directory/.install

btw, are you sure your computer doesnt recognise it? try to install alsa-related packages

btw, what kind of card is it?

What does that mean?  I genuinely appreciate the support but I am an absolute beginner which is why I'm in here.  I don't understand all the code.

---

