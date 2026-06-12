---
title: "Drivers"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by sbell on 2008-03-25
I started using Ubuntu back during 5.10 but gradually migrated back to windows during the 6.10 era.  I hope to learn some more things and blend in with the community but first I have some questions.

Drivers
Will I need as many Drivers as I do on my Windows machine? How do I know these drivers are installed?

---

### Post by herbster on 2008-03-25
You just need the nvidia driver for your card, which can be installed with

```
sudo apt-get install nvidia-glx-new
```

And there's nothing about your sound card there, but the driver will be loaded with ALSA when you install Ubuntu, you may just need to configure/tweak it, as you would on Windows.

---

### Post by kellemes on 2008-03-25
O man, you shouldn't have problems getting Ubuntu to run at all..
You may need to install the restricted driver for your videocard, in Ubuntu it's a click away..

You know your drivers are installed when you have a functioning system.
Try the livecd first.. it'll give you a clue on how well your hardware is supported.

---

### Post by smartboyathome on 2008-03-25
The only complications I see is with the NVidia card, but that can be taken care of with the Restricted Drivers program. I don't know about the network card, though (it will probably be your biggest holdup if it is incompatible), as it wasn't included with the specs. Most drivers install automatically, so it won't be like on windows. :)

---

### Post by stchman on 2008-03-25
> **sbell said:**
> I started using Ubuntu back during 5.10 but gradually migrated back to windows during the 6.10 era.  I hope to learn some more things and blend in with the community but first I have some questions.

Drivers
Will I need as many Drivers as I do on my Windows machine? How do I know these drivers are installed?

That system will run fine.  You will need to install Envy 0.9.10 and have it install the 169.12 nvidia drivers.  Everything else will work OOB.  The 169.xx drivers are needed to support the 8xxx series of nvidia cards.

Installation should take you under an hour.

The gigabit ethernet is done by Marvell which is Linux friendly.

---

### Post by Paqman on 2008-03-25
Ubuntu has changed the way it handles drivers since 6.10. Any hardware that doesn't work automatically will now be listed in a new feature called the Restricted Drivers Manager. With a mouse click it will download and install any non-free drivers that you hardware requires. For most people this is all they have to do to get their hardware working.

When it works it's actually a lot easier than installing Windows drivers.

---

