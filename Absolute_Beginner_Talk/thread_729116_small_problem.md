---
title: "small problem"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by RyviusRan on 2008-03-19
I was trying to download a game called flight gear on ubuntu.

I downloaded the right version but when i go to install it.

it says dependency ins not satisfiable:  libc6

anyone know what that means?

---

### Post by philinux on 2008-03-19
You dont need to download it. It's in synaptic, install it from there.

---

### Post by eragon100 on 2008-03-19
You have to install the development version of libc6, libc6-dev, through synaptic. Then it should work :)

---

### Post by RyviusRan on 2008-03-19
yah but for some reason when i download this game using sudo apt-get install flightgear

whenever i tried to mess with the folders install it said permission denied it wouldn't let me  even move folders around which were inside the game folders.

what was the command to bypass that. Since when i open up the folders from properties I can't select anything on the permission.

---

### Post by donnyblaze1 on 2008-03-19
chmod is the command you will need to change the permissions.  Have a look-sie at [http://catcode.com/teachmod/]("http://catcode.com/teachmod/")

---

