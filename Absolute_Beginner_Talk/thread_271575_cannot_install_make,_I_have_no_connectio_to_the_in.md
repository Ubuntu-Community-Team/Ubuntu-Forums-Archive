---
title: "cannot install make, I have no connectio to the internet"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by gregpavy on 2006-10-04
I', trying to install make so that I can install a driver for a wireless card I recenlty got for my laptop. On another forum post it said I should type > sudo apt-get install make
however it  seems to try to go to the internet to download the file but at the moment that comp is noy connected to the net, thats why i got the wireless card:). I have a Ubuntu install cd. could someone give me a hint :)

---

### Post by sumguy231 on 2006-10-04
The package you'll want is 'build-essential' and it includes everything you need for compilation. I imagine it's on the install cd. If I remember correctly, you can do that with:
```
sudo apt-cdrom add
sudo apt-get update
```

---

### Post by aysiu on 2006-10-05
Don't forget to install it too: ```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by sumguy231 on 2006-10-05
> **aysiu said:**
> Don't forget to install it too: ```
sudo aptitude update
sudo aptitude install build-essential
```

Of course, that's the most important step. ;)

---

