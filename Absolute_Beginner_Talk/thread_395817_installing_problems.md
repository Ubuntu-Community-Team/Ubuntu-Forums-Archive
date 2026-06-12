---
title: "installing problems"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by mondoman89 on 2007-03-28
i am trying to install ubuntu 6.10 on a dell xps t500. it has a pentium III processor. every time i boot up with the cd i select "start or install ubuntu" it loads for a while then i get a brown screen with an error and the screen is seeing triple. it says something about the GNOME settings. its hard to read exactlt what its saying. i just need some help figuring this out. maybe some suggestions of a distribution for older comps.

---

### Post by DreadPirateRoby on 2007-03-28
I'm not familiar enough with linux yet to know exactly what your problem is, but if your having problems due to GNOME you could try Xubuntu instead. 
 
It should run a little faster on an older machine and you can always install the apps it's missing later.

---

### Post by deathbyswiftwind on 2007-03-28
Sounds like in windows when you set your refresh rate beyond the capacity how you would get those multiple screens all messy. If so then if you run

```

sudo dpkg-reconfigure xserver-xorg

```

and reset the gdm using the proper values it should fix that problem

---

### Post by mondoman89 on 2007-03-29
thx im going to try xubuntu. i used another monitor i have and the screen issue went away.

---

