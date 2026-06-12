---
title: "Startup scripts..."
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by ecto on 2005-12-20
Hello I was wondering if it is possible to create a xinitrc script that allows me to startup x that starts different programs on different apps running on different desktops IE Firefox running on desktop 1, 4 terminals running on desktop 2, xmms on desktop 3 etc.

---

### Post by Sutekh on 2005-12-20
Look for something called Devil's Pie.  I haven't used it, but that's what it does.

[Gnome - HOWTO: Automating Gnome with Devil's Pie]("http://ubuntuforums.org/showthread.php?t=75749&highlight=devils+pie")
Looks quite complex..

---

### Post by Gandalf on 2005-12-20
Doing this is easy,
First follow [this guide](http://ubuntuforums.org/showthread.php?t=75749) to get devilspie up and running, then

System -> Preferences -> Sessions -> Startup Programs

click on add, add devilspie with 30 as priority, then start adding startup programs after 60 as priority

---

### Post by ecto on 2005-12-20
thank you but the problem is im using opebox...

---

### Post by Gandalf on 2005-12-20
in that case i am not sure, sorry i don't use other than gnome

---

### Post by Sutekh on 2005-12-20
Why is openbox a problem?  Are you using openbox with or without gnome?

Edit: I just read you howto for openbox without gnome, okay, sorry I don't know what you can do.  Like Gandalf I haven't used other than gnome.

---

### Post by patrick295767 on 2005-12-21
Since I am using fvwm with some stuffs of gnome (gnome-panel...), I would say this would be easier with fvwm 'cos it's very free & easy to customize the startup ... 
  
In .fvwm/.fvwm2rc  :
>         then, there is a startup line ... + I exec exec program_name .... 

Good courage !

Pat'

---

