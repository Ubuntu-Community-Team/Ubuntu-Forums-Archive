---
title: "Changing default order at startup"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Stephen47 on 2006-11-30
I have read the Ubuntu documentation on this.I type in the commands as shown but nothing happens, it just goes to the next line and it satrts:"steve@steve-laptop:/$
What does this mean.
When I open terminal it opens like this:
steve@steve- laptop~$
perhaps I need a tutorial on terminal or I may end up that way. Thanks for any help

---

### Post by alican timur on 2006-11-30
you have to modify the grub listing.

---

### Post by kerry_s on 2006-11-30
When you get the terminal, type so it looks like this->

steve@steve- laptop~$ sudo gedit /boot/grub/menu.lst

Scroll down till you see->

default		0

change to->

default		saved

This will make it boot the last OS used.

---

### Post by Stephen47 on 2006-11-30
> **alican timur said:**
> you have to modify the grub listing.

What does that mean and how do I do it? Remember this is the Absolute Beginner Talk forum.

---

### Post by Stephen47 on 2006-11-30
> **kerry_s said:**
> When you get the terminal, type so it looks like this->

steve@steve- laptop~$ sudo gedit /boot/grub/menu.lst

Scroll down till you see->

default		0

change to->

default		saved

This will make it boot the last OS used.

Isn't that redundant? If I am at the terminal then I am in Ubuntu which is the last OS used so won't that make it default to Ubuntu?

---

### Post by sailor2001 on 2006-11-30
assuming you are dual booting......The first boot choice is ubuntu (0) follwed by ubuntu safe mode (1) and memtest (2) and the windoz safe (3) and then windoze (4) but check on that in your boot up.........then if you want windoze default, in terminal sudo gedit /boot/grub/menu.lst and change the default (0) to the proper number

---

### Post by Tomosaur on 2006-11-30
If you're having difficulty figuring out grub via the command line, check the link in my sig :)

---

### Post by alican timur on 2006-12-03
I meant to explain it but i couldn't remember the command :) i'm sorry. 
press alt + f2 and type in "sudo gedit /boot/grub/menu.lst"

you'll see the list of operation systems installed in your pc, as you see them in the selection list you see when you're booting up your computer. modify the list as you like, moving your desired default choice to the top. that's it :)

---

### Post by steve.horsley on 2006-12-03
My preference if someone wants windows to be the default is to move the windows stanza from below the automagic section to above it. That way, windows becomes the top entry in the list and also the default entry.

---

