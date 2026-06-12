---
title: "FLUXBOX: lid close"
date: 2007-12-16
forum: Apple Intel Users
---

### Post by kestaz on 2007-12-16
Hi all !

I have such problem: recently i migrated to fluxbox from gnome. But then i close lid apple logo still shows  light. Any solutions to solve this problem ? 

And one thing. I want use  vga-out. Then i close lid i want see just my desktop monitor, not macbook internal display



cheers, kestaz

---

### Post by cknight on 2007-12-16
Well I can help solve your lid problem, but not the monitor switching problem (though I too am looking for a solution to this. The lid closure actually has a key event associated with it.  This means you can associate actions in your keys file for lid-closure events.  Give this a try:
```
None 214		:Exec xset dpms force off

```

Where 214 is the key number of your lid closure.  You can find your key number by running 'xev' on the command line, closing and opening your lid and then looking at the output.  For more info on key bindings, check out this link which has a more detailed explanation on using 'xev':  [http://ubuntuforums.org/showthread.php?t=617812]("http://ubuntuforums.org/showthread.php?t=617812")

Note that the above key binding will turn the monitor off when you close AND open your lid.  Thus after opening it, jiggle the mouse or press a key to reactivate it.

As for switching monitors, I think your solution will lie in either modifications to your xorg.conf file or using xrandr to swap screens.  Good luck!

---

