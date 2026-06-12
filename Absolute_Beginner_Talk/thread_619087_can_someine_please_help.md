---
title: "can someine please help"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by moondoggy17 on 2007-11-21
trying to use emerald themer but none off my themes are working
does anyone know why

---

### Post by jordanmthomas on 2007-11-21
Is emerald running?
```
 ps -A | grep emerald
```

---

### Post by moondoggy17 on 2007-11-21
> **jordanmthomas said:**
> Is emerald running?
```
 ps -A | grep emerald
```

when i run that cod i get this

```
 moon@newtype:~$ ps -A | grep emerald
13735 ?        00:00:03 emerald-theme-m
moon@newtype:~$ 
```

---

### Post by daimaru on 2007-11-21
if you mean that there are no themes listed, I had to install the emerald theme package from feisty because there was no gutsy one at the time in installed. dont know if there is a gutsy theme package yet.
you can find the feisty emerald theme package on ubuntu.com

---

### Post by moondoggy17 on 2007-11-21
> **daimaru said:**
> if you mean that there are no themes listed, I had to install the emerald theme package from feisty because there was no gutsy one at the time in installed. dont know if there is a gutsy theme package yet.
you can find the feisty emerald theme package on ubuntu.com

i have plenty of themes it is just that none of them show up

---

### Post by jordanmthomas on 2007-11-21
OK, emerald is not running.
You need to do this:
```
killall gtk-window-decorator  #your window borders will go away
emerald --replace &
exit
```

To make this permanent, you'll want to install the advanced compiz options:
```
sudo apt-get install compizconfig-settings-manager
```
Then, run ccsm
Go to the window decoration plugin and change the "Command" line to this:
```
emerald --replace
```

---

### Post by moondoggy17 on 2007-11-21
that did it thank you very much:)

---

### Post by moondoggy17 on 2007-11-21
i talk to soon now when i close emerald themer my title bar disappers
:confused:

---

### Post by jordanmthomas on 2007-11-21
did you close the terminal with the button or with exit like I said?
Open a new terminal, type this (exactly)
```
emerald --replace &
exit
```

also, if you went through the steps I gave to make it permanent, logging out and then back in will fix things up for you as well.

---

### Post by moondoggy17 on 2007-11-21
thank you it works now

---

### Post by moondoggy17 on 2007-11-21
now can someone tell how to get the cube sky dome feature to work

---

### Post by jordanmthomas on 2007-11-21
Install the compiz advanced settings manager (I described this process earlier in the thread)

Then, run ccsm and go to the Desktop Cube plugin, and then to the Appearance tab,
Here, you will see a list of file to use for the Skydome (at the bottom)
Be sure to check the box that says 'Skydome' or it won't be activated.

---

### Post by moondoggy17 on 2007-11-21
i used to beable to get to the sky dome feature but i had to format my hard drive when one of my famliy members got on my computer and downloaded a virus that my virus software could not delete:(

---

### Post by jordanmthomas on 2007-11-21
Does it not work after doing what I suggested?

---

### Post by moondoggy17 on 2007-11-21
yes but i was thinking of another way to do it but i cant remember how to do it like before or find the app that i used, with it you could be inside the cube or set a pic for the surroundings of the cube

---

### Post by jordanmthomas on 2007-11-21
Odds are the program you used to use no longer works with compiz and has been abandoned.

You can still be inside the cube.  In ccsm, go to the desktop cube plugin and then the behavior tab.

---

### Post by moondoggy17 on 2007-11-21
so you cant set a pic for the outside surroundings any more?

---

### Post by jordanmthomas on 2007-11-21
[quote=jordanmthomas]run ccsm and go to the Desktop Cube plugin, and then to the Appearance tab,
Here, you will see a list of file to use for the Skydome (at the bottom)
Be sure to check the box that says 'Skydome' or it won't be activated.
[/quote]
This isn't what you wanted?

---

### Post by moondoggy17 on 2007-11-21
yes but i'm not the only user on this computer

---

### Post by jordanmthomas on 2007-11-21
How is this relevant?  Just repeat the process for each user.

---

### Post by moondoggy17 on 2007-11-21
ok my girl and i use this computer i like the sky dome feature she like being able to put her amine pic around the cube and i'm trying to get that pic back up for her, see:)

---

### Post by moondoggy17 on 2007-11-21
never mind i over looked it
:lolflag:
sorry about that

---

### Post by moondoggy17 on 2007-11-21
i can't change screen resolution:(

---

