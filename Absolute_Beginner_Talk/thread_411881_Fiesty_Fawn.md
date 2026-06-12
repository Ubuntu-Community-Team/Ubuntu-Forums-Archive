---
title: "Fiesty Fawn"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by blublu on 2007-04-17
[FONT="Century Gothic"]I got the beta update to Ubuntu . Every  thing was fine till after the reset - now it is a black screen with the white circle and coffee beans spining inside . Any idea how I can get back to version 6.0[/FONT]

---

### Post by jem7v on 2007-04-17
You wouldhave to install 6.06 or 6.10 over top of your current installation... THere's no such thing as a downgrade: only clean installs of older versions.

However, you could try to make a new home partition with these instructions and move your personal information to that, because that lets you do clean installs without wiping out everything in your home directory.  [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

As for Feisty, I'd proabably recommend waiting for the official relaease instead of using the Beta.  Even then I'd wait a week or two so they can fix any last minute bugs they find after it's released.

---

### Post by Seisen on 2007-04-17
Did you install the beta version of Feisty from a CD  or did you do a dist-upgrade?

---

### Post by blublu on 2007-04-17
It was the dist- upgrade

---

### Post by kwaanens on 2007-04-17
> **jem7v said:**
> As for Feisty, I'd proabably recommend waiting for the official relaease instead of using the Beta.  Even then I'd wait a week or two so they can fix any last minute bugs they find after it's released.

The actual **install** will be the same after a week or two, the installation CD won't change after release (at least not that early). To get rid of bugs you'll still have to upgrade. For most users Feisty will probably not be a problem at this point, but, of course, that's impossible to predict beforehand.

- Ketil

---

### Post by Seisen on 2007-04-17
What kind of graphics card are you using, this could of caused the problem.

---

### Post by blublu on 2007-04-17
NVIDIA GeForce MX 440 (very old )

---

### Post by Seisen on 2007-04-17
Post what is says on Line 91 where it says what type of video card you are using.

```
sudo vim /etc/X11/xorg.conf
```

---

### Post by blublu on 2007-04-17
I think I will format and re-install

---

### Post by Seisen on 2007-04-17
The only reason I said that is because I have noticed a lot of people having problems with ATI  and  
Nvidia graphics in Feisty.

---

