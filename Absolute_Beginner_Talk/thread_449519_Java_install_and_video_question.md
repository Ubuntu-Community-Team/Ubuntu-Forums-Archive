---
title: "Java install and video question"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Neenjah on 2007-05-20
First off After Installed my video driver everything works great now, BUT I cant change my resolution back to 1024/768 and It drives me crazy living so small.. any tips?

Secondly java gets to this point:

[IMG]http://i1.tinypic.com/6ceq0xc.png[/IMG]

How do I click okay.. or accept the EULA?

---

### Post by Happy_Man on 2007-05-20
Press enter..... 

and after you configure all that... type
```
sudo dpkg-reconfigure xserver-xorg
```

into the terminal, and accept all the defaults. When you get to the screen that has all the resolutions on it, scroll and select with spacebar any ones you want. Then press enter. Then, press ctrl-alt-backspace.

---

### Post by Neenjah on 2007-05-20
Thanks for the tip on the java 

but on the resolution screen

[IMG]http://i2.tinypic.com/6fynurb.png[/IMG]

800/600 is the only option

---

### Post by Neenjah on 2007-05-20
After I type sudo dpkg-reconfigure xserver-xorg

it brings me to another screen I cant accept the EULA on for Configuring xserver-xorg

---

### Post by solomarv on 2007-05-20
> How do I click okay.. or accept the EULA?

Press "TAB" to navigate to the "OK" button, then press "Enter". If "TAB" does not work, try the keys "<-" and "->".

---

### Post by Happy_Man on 2007-05-20
What? Are you sure?

---

