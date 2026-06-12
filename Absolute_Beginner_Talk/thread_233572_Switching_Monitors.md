---
title: "Switching Monitors"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Magiclamp on 2006-08-10
Hey guys, the main monitor I am using keeps flickering out and whatnot, (old monitor) and when I try plugging in other monitors, the screen just remains black. Any suggestions? Does this happen to everyone? 

Is there a way to just switch monitors easily?

---

### Post by xpod on 2006-08-10
I seem to be able to plug any of our monitors in to any of our systems..
Ubunto/xp.Kbunto Or even the xbunto cd if i stick it in.
Ive had them all here there and everywhere and i aint yet had any problems along those lines....My probs are mainly "user" issues as apose to hardware issues mind you...lol.

have you turned things off prior to plugging new monitor in??Mabey if you just switched over without rebooting...i suppose you would have eh??

Im sorry im not more help but im new too.All my stuff just seems to "work" and its ALL over 5 years old which is ancient in pc terms i believe.

Someone should be able to HELP you....good luck


PS....Ive just brought an old hulk of a ibm monitor down from upstairs that even has specific wires on it for its own sys(sound & a usb lead??)I slung the old ibm sys itself as it was REALLY old

We use it on the m.e pc my young un`s play with and even it works ok with ubunto AND kbutno....No sound obviously as it has it`s own weird wire that none of our pc`s have socket for as well as some green usb connecter comming from it..BUT works fine on both linux

---

### Post by aeiah on 2006-08-10
like xpod asked, let us know whether you are switching your computer off before connecting the monitor. i know that some monitors, with windows as well as linux, dont get recognised as being pressent when you plug them in whilst the pc is running, especially when your pc is expecting your original monitor

---

### Post by djsroknrol on 2006-08-10
You might try this in a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

with the new monitor plugged in...should straighten things out...

---

