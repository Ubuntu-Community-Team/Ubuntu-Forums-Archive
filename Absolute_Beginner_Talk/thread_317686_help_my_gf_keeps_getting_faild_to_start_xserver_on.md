---
title: "help my gf keeps getting faild to start xserver on bootup"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2006-12-12
every time she starts her computer "failed to start xserver"

---

### Post by neemz on 2006-12-12
login using the console and type this

sudo dpkg-reconfigure xserver-xorg

---

### Post by TheForkOfJustice on 2006-12-12
Break up with her. Problem solved.

---

### Post by cosmoshell on 2006-12-12
> **neemz said:**
> login using the console and type this

sudo dpkg-reconfigure xserver-xorg

tried it with vesa and vga dosent work

---

### Post by cosmoshell on 2006-12-12
> **TheForkOfJustice said:**
> Break up with her. Problem solved.

ya some solution. moron....

---

### Post by neemz on 2006-12-12
okies, can you provide us with some detailed output from the xserver log?

(/var/log/Xorg.log)

---

### Post by cosmoshell on 2006-12-12
> **neemz said:**
> okies, can you provide us with some detailed output from the xserver log?

(/var/log/Xorg.log)

i dont have accses to her computer anything in particular you need to look for in there? im trying to help her over the phone

---

### Post by neemz on 2006-12-12
I'd be looking for error messages, usually have EE at the beginning of the line, anything along the lines of Error: screens not found or something.

PS: Being tech support over the phone... I feel your pain :p

---

### Post by Biggus on 2006-12-12
> ya some solution. moron....

I say, that's a little bit off, old boy, the chap was only having a little joke, I'm absolutely, 100% certain, that no offence was meant.

Disrespecting other people is never a nice thing.

---

