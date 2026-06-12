---
title: "Window won't minimize/resize/exit"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by PleaseEnjoyThis on 2007-04-26
When any of my windows are maximized they can't be minimized resized or exited out of from the top right hand corner.  Instead I have to right click their tab at the bottom of the screen and choose what to do.  But if the window isn't maximized it works fine.  This is extremely odd to me, anyone have any ideas?

---

### Post by PleaseEnjoyThis on 2007-04-26
So I guess it went away on its own.  I keep having all these temporary glitches.  Driving me nuts!

---

### Post by dpar on 2007-04-26
Do you have desktop effects turned on?? I've heard that will do it.

---

### Post by csf111 on 2007-04-26
...curious as to:

a) What Windows Manager you are using?

b) What graphics card you are using?

---

### Post by trishacupra on 2007-04-26
I've noticed the same thing with my new installation of Feisty. Using Gnome and an ATI card. The Desktop Effects were definitely playing up something chronic. Haven't had the problem since I installed the ATI restricted drivers (yesterday).

I also can't use Desktop Effects at all now. Probably the graphics card's fault.

---

### Post by PleaseEnjoyThis on 2007-04-26
I currently have no desktop effects turned on.

Graphics card: GeForce 7900 GT/GTO

It is weird I'll get these little glitches and they will go away.  I assume its from messing with stuff from [http://art.gnome.org](http://art.gnome.org).  

Right now everything is running smooothly.  : D

---

### Post by csf111 on 2007-04-27
Are you using the linux-restricted-modules?

(These include nVidia modules for your 7900....)

---

### Post by PleaseEnjoyThis on 2007-04-27
This is possible.  I thought i read that mine were fine as they are.  What should I do?

---

### Post by csf111 on 2007-04-27
</Response in context of Absolute Beginner/n>

If indeed you think you have them, go to:
 
System -> Administration -> Restricted Drivers Manager

and verify the nVidia drivers are present and selected.

(If you don't see a Restricted Drivers Manager menu item;
select System -> Preferences -> Main Menu 
When that opens up, toward the bottom on the 
Left Hand Side column labeled Menu is 
System -> Preferences -> Administration
Ensure the Restricted Drivers Manger is selected (checked)
on the Right Hand Side column, select Close and (after logout)
you will see it in your System -> Administration menu

---

### Post by trishacupra on 2007-04-27
Maybe it's this bug?

[http://bugzilla.gnome.org/show_bug.cgi?id=433253](http://bugzilla.gnome.org/show_bug.cgi?id=433253)

---

### Post by csf111 on 2007-04-28
Good find!

(BUT as we never heard back from PleaseEnjoyThis.....)

---

