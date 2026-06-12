---
title: "new graphics card problems"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2007-06-17
well i dont know if its the wrong card or im just stupid.  i installed it correctly and im using the computer now...but the install cd that came with it wont do anything because its all .exe files.  i tried the restricted drivers manager and it doesnt do anything.  its a ati radeon x1050 card and i figured that it would work.  any help is greatly appreciated.  ati doesnt list this card under there linux supported systems but i find it hard to believe that this card will not work.  thanks in advance

---

### Post by starcraft.man on 2007-06-17
> **dragnazz5.0 said:**
> well i dont know if its the wrong card or im just stupid.  i installed it correctly and im using the computer now...but the install cd that came with it wont do anything because its all .exe files.  i tried the restricted drivers manager and it doesnt do anything.  its a ati radeon x1050 card and i figured that it would work.  any help is greatly appreciated.  ati doesnt list this card under there linux supported systems but i find it hard to believe that this card will not work.  thanks in advance

Try installing drivers with [Envy.]("http://albertomilone.com/nvidia_scripts1.html") I'm no ATI expert but if theres a driver Envy should install it for you. Download and install the stable debian, go to applications > System tools > Envy and then let it automatically install ATI drivers. Answer yes to anything that comes up and when you reboot it should work.

In the unlikely event anything fails at reboot, input this and remember to switch to the vesa drivers (you'll see the driver list):

```
sudo dpkg-reconfigure xserver-xorg
```

Thats it, best luck with that. ATI isn't as well supported as NVidia...

---

### Post by dragnazz5.0 on 2007-06-17
when i try to download it and install envy i get an error 

"error: dependecy is not satisfiable: build essential

edit: nevermind i think i figured it out.  i just reinstalled fiesty and i havent done any updates

---

### Post by starcraft.man on 2007-06-17
> **dragnazz5.0 said:**
> when i try to download it and install envy i get an error 

"error: dependecy is not satisfiable: build essential

edit: nevermind i think i figured it out.  i just reinstalled fiesty and i havent done any updates

It usually installs on its own... open up a terminal (Applications > Accessories > Terminal) and paste this in: 

```
sudo aptitude install build-essential
```

Then retry Envy, it will work after.

---

### Post by dragnazz5.0 on 2007-06-17
once i updated everything it installed fine.  ill check it out and let you know if it works.  thanks for the help

---

