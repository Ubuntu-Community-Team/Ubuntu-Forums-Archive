---
title: "how to turn off the pointer locating with the ctrl-key?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by eidam655 on 2007-11-13
hi,

i have ubuntu gutsy. when i press ctrl, the OS plays an animation which shows my cursor's location. i want to turn this off.

however, even if i found some tutorials, they all navigate me to system->preferences->mouse, where should be a Pointer tab. but, maybe because i am on notebook, i have the touchpad tab there .

so, is there any console command to turn the poinetr-showing off?

thx in advance

---

### Post by FuturePilot on 2007-11-13
Press Alt+F2 and type in
```
gconf-editor
```
Navigate to desktop>gnome>peripherals>mouse. Uncheck the box that says locate_pointer.

---

### Post by eidam655 on 2007-11-13
thx :)

wish all problems could be solved this simply :D

---

### Post by FuturePilot on 2007-11-13
You're welcome :D

---

### Post by rax_m on 2007-11-13
Or maybe even easier is.. System-> Preferences -> Mouse Preferences 

And under the pointers tab uncheck the box :)

---

### Post by eidam655 on 2007-11-14
> **rax_m said:**
> Or maybe even easier is.. System-> Preferences -> Mouse Preferences 

And under the pointers tab uncheck the box :)

yeah, tahnks for actually reading my first post... :roll: ;)

---

### Post by rax_m on 2007-11-16
> **eidam655 said:**
> yeah, tahnks for actually reading my first post... :roll: ;)

LOL .. sorry .

I'm on a notebook too, but I do get the pointers tab. I'm on Feisty.. which version are you on?

---

### Post by eidam655 on 2007-11-25
Gutsy :) maybe that's the problem :)

---

