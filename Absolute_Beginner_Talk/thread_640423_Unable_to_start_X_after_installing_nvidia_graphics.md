---
title: "Unable to start X after installing nvidia graphics card"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by prototype_angel on 2007-12-14
Hi, I was running ubuntu for a few days on VIA chrome graphics with the vesa driver(or something like that)

I bought a new nvidia graphics card, and installed it, and x is not starting. I can go into recovery mode and even bulletproof x isn't kicking in.

In regular mode, it shows some verbose while booting and doesen't respond. In administration/recovery mode, startx doesen't work saying no screens have been found.

I wish to run my monitor on this card, and use a restricted driver. Please help.

---

### Post by rajeev1204 on 2007-12-14
Have you tried setting the new card as the primary graphics adapter in the BIOS?

---

### Post by Jimmey on 2007-12-14
From the console try 
```
sudo dpkg-reconfigure xserver-xorg
```

When it asks which driver to use, select the "nv" driver.

If this fails, try the same command again, selecting the "vesa" driver.

---

### Post by prototype_angel on 2007-12-14
> **Jimmey said:**
> From the console try 
```
sudo dpkg-reconfigure xserver-xorg
```

When it asks which driver to use, select the "nv" driver.

If this fails, try the same command again, selecting the "vesa" driver.

that might work, will give it a shot. thanks

---

