---
title: "HELP!! Acer monitor troubles...."
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by shadowber on 2008-01-13
Ok here is the prob... I have a lcd screen (acer AL2016w to be specific).

I tried to set it up, but did not find the specific screen in screens and graphics, so I selected a generic lcd screen with the correct size, and restarted.... now its messed up, it starts but there are only lines and I cannot see whats going on.... 

I don't know what to do so any help will be appreciated!!

---

### Post by moffa on 2008-01-13
In a shell, either recovery mode or ctrl-alt-f1 type:

```
sudo dpkg-reconfigure xserver-xorg
```

you should be able to select your resolution again

---

### Post by shadowber on 2008-01-13
I'm a complete beginner... can you give a little more instruction?
thanx...

---

### Post by shadowber on 2008-01-13
K I got on, but cannot get my resolution..... any ideas? (its stuck at 860x) 
also this happened after I tried to enable my video card through restricted drivers.
my video card is a nvidia geforce 8600 gts.
I'm not sure it's installing correctly...

---

### Post by shadowber on 2008-01-13
bump

---

### Post by moffa on 2008-01-13
To fix your video card, I recommend using the program envy.  The program is located here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

If you can't see anything and are just using a terminal window you can get it using
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu6_all.deb
sudo dpkg -i envy_0.9.9-0ubuntu6_all.deb
sudo envy -t

``` and selecting 1

The first line downloads the program, the second installs it and the third runs it.

If your window manager is working and you can use your web browser, just go to the website download the deb and install it.  Then go to Applications > System Tools > Envy.

Once your driver is up and running you can fix the resolution by using System > Administration > Screen and Graphics

---

### Post by shadowber on 2008-02-10
Thanks for replying.... I had already tried that, but it did NOT work...

---

### Post by shadowber on 2008-02-27
bump

---

