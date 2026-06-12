---
title: "Installed Feisty, xorg not working, don't know what to do"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by GrantShoe on 2007-04-20
yeah i installed it and restarted and now i have text which is great but no xorg.  i don't know where to start in getting this setup

---

### Post by taurus on 2007-04-20
Did you use the desktop CD or the server CD?  What happens if you run this command after you log in?

```
startx
```

---

### Post by GrantShoe on 2007-04-20
I used the update manager so... server

and when i ran startx ti's telling me that it couldn't open /lib/modules/2.6.20-15-generic/volatile/nvidia.ko

I've messed with my xorg.conf file in the past a bunch because i have a legacy nvidia card and need the driver to work.  maybe that's why?  is there a way to 'reset' the xorg.conf file?

---

### Post by taurus on 2007-04-20
Yes.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by GrantShoe on 2007-04-20
i went through all of the options in that and then it said that it wrote the old one to a backup and kept me in terminal .  so i typed in startx and got the same error

---

### Post by taurus on 2007-04-20
Which driver for your graphic card did you choose?  Pick **vesa** for now until you get X running again.

---

### Post by GrantShoe on 2007-04-20
> **taurus said:**
> Which driver for your graphic card did you choose?  Pick **vesa** for now until you get X running again.

AHHHH yeah i picked nvidia.  lets see how this works...

---

### Post by paulfryer on 2007-04-20
Troll.

---

### Post by paulfryer on 2007-04-20
Troll.

---

### Post by GrantShoe on 2007-04-20
> **taurus said:**
> Which driver for your graphic card did you choose?  Pick **vesa** for now until you get X running again.

ok, so that worked and it kept my resolution! (the problem before was getting a resolution greater then 800x600)

thanks a bunch!

---

