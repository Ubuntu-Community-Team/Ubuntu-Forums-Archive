---
title: "need help with choosing OS"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by p3ngu1n on 2007-07-20
ok i have ubuntu x86 right now and i dont think its good for my system. heres my specs:

motherboard: amd socket A support BROKEN usb and sound pluggin
prosessor: AMD 1ghz peice of crap socket A
ram: 512mb
hard drive: 300gig
graphics: NVIDIA GeForce 6200 1/4gig mem

ive been thinking about xubuntu because my prosessor is melting right now. and also theres all of those different versions of ubuntu for different prosessors! what should i pick!? if i do go with xubuntu, would i be able to play half-life? maybe play half-life BETTER? your thoughts please.

---

### Post by por100pre1 on 2007-07-20
I think you can give Ubuntu a try first. I haven't tried Half-Life on Linux but I think shouldn't be a big deal... (I assume you are talking about HF1, HF2 is too much for your pc anyway...)

---

### Post by p3ngu1n on 2007-07-20
yah i have ubuntu. and like i said, its melting my cpu. i dont realy know what those other things than x86 are, but maybe they'll be better? or xfce? im not going back to windows. NEVER!!!!!! lol but i do need something good on my cpu

---

### Post by Rocket2DMn on 2007-07-20
You have to have x86, that is the processor architecture.  Xfce is the desktop environment for Xubuntu, it uses fewer resources than Gnome.  It should be perfect on your computer.
If your CPU is burning up, you may want to make sure the fans and air pathways are cleared of dust.  Maybe you need some thermal paste for your processor.

---

### Post by p3ngu1n on 2007-07-20
you know what, thermal paste is a good idea! come to think of it, i think i forgot to put it in last fan switch! i think ill do xubuntu. but will half-life work? (in steam)

---

### Post by Rocket2DMn on 2007-07-20
You won't know until you try.  I imagine it will run a little slow, though.  1 GHz isn't a whole lot of speed for an FPS running under wine.  I play counter-strike at 2ghz, and I'm able to get a good framerate when I turn off Beryl, but it's still not quite the same as windows.

---

### Post by p3ngu1n on 2007-07-20
well, knowing i hate windows with a passion, ill be fine :D i love the fact that linux never locks up! lol but is there a way to turn ubuntu into xubuntu without totaly reloading the OS?

---

### Post by Rocket2DMn on 2007-07-20
More or less, you can get Xfce like so:
```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```
Sounds like you have plenty of HD space so no need to uninstall other environments.
Then restart X and select Xfce as your environment at the login screen.

---

### Post by p3ngu1n on 2007-07-20
ok so i can switch between gnome and xfce?!?!?! thats wonderfull! will all of my gnome things be saved in my xfce? (hopefully)

---

### Post by FleetAdmiral74 on 2007-07-20
Fluxbuntu uses an even lighter enviorment then Xubuntu, but you might not need that depending on how Xu goes.

---

### Post by AlexenderReez on 2007-07-20
> **Rocket2DMn said:**
> More or less, you can get Xfce like so:
```
sudo apt-get update
sudo **apt-get** install xubuntu-desktop
```
Sounds like you have plenty of HD space so no need to uninstall other environments.
Then restart X and select Xfce as your environment at the login screen.

why people keep suggesting to use apt-get for this kind of installation ...please use

> sudo aptitude install xubuntu-desktop

you can easily remove this environment (all software that you have install for it) if you don't like it with 

> sudo aptitude remove xubuntu-desktop

but you can't do this will apt-get command:)

---

### Post by testube_babies on 2007-07-20
> **AlexenderReez said:**
> why people keep suggesting to use apt-get for this kind of installation ...please use



you can easily remove this environment (all software that you have install for it) if you don't like it with 



but you can't do this will apt-get command:)

Ummm...yes you can; ever since Edgy Eft you can use apt-get autoremove and it has the same effect (ie removing unused dependencies).

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by AlexenderReez on 2007-07-20
> **testube_babies said:**
> Ummm...yes you can; ever since Edgy Eft you can use apt-get autoremove and it has the same effect (ie removing unused dependencies).

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

autoremove will remove all that had been mark as unused dependencies ,,,if user use extra repo,most probably this autoremove will broken....it is better

> sudo aptitude install xubuntu-desktop
> sudo aptitude remove xubuntu-desktop


it is even easier:)

---

### Post by p3ngu1n on 2007-07-20
xubuntu works great! but anything that will help it would be great! what is the apt-get for fluxbuntu? ill get that too

---

### Post by testube_babies on 2007-07-21
> **AlexenderReez said:**
> autoremove will remove all that had been mark as unused dependencies ,,,if user use extra repo,most probably this autoremove will broken

...good to know!

---

