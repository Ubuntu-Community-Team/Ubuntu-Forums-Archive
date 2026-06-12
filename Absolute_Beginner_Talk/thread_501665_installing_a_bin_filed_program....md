---
title: "installing a bin filed program..."
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by manuleka on 2007-07-15
ok so i've downloaded realplayer 10 

[http://www.real.com/linux/](http://www.real.com/linux/)

its a bin file... 

can anyone direct me on how to install this into ubunutu feisty fawn??

---

### Post by Vague on 2007-07-15
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29)

Instructions on installing it from repositories and from real.com.

---

### Post by univremonster on 2007-07-16
OK that's great for Real Player... I just got Google Earth and it also is a .bin.... in general what is the solution for this kind of file type?

---

### Post by Vague on 2007-07-16
> **univremonster said:**
> OK that's great for Real Player... I just got Google Earth and it also is a .bin.... in general what is the solution for this kind of file type?

The instructions for installing from the .bin there are pretty much the general instructions.  ```
cd /path/to/file
sudo chmod +x filename.bin
sudo ./filename.bin
```  If you do that you should be set.

---

### Post by manuleka on 2007-07-16
> **Vague said:**
> The instructions for installing from the .bin there are pretty much the general instructions.  ```
cd /path/to/file
sudo chmod +x filename.bin
sudo ./filename.bin
```  If you do that you should be set.

yip thats how i installed my realplayer

---

### Post by univremonster on 2007-07-17
OK that works.. I was confused because the link takes you straight to the apt-get solution to the problem which is far less versatile.  Should have read that a little more closely... at any rate, it's working great now, thanks for the help!

---

