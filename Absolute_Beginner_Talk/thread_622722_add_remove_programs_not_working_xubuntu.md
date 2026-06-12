---
title: "add remove programs not working xubuntu"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by uzybear on 2007-11-25
just installed xubuntu gutsy on my ibm x30 laptop

when i try to install something through add/remove i get this:

The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. 



so i click "refresh" and it downloads some updates and then it gives me the same error message the next time i try to install

i'm thinking maybe it's something to do with my WiFi because there's sometimes a problem with the wifi on this laptop being recognized as ethernet LAN, but the wifi WORKS

so i'm thinking perhaps the add/remove program THINKS i don't have an internet connection when i really do, or something?


thoughts?

---

### Post by jken146 on 2007-11-25
Do you get any error messages when you type in a terminal ```
sudo apt-get update
```?

If not then you can use another method to install programs (e.g.  Synaptic, apt-get or aptitude).

---

### Post by jtvanlew on 2007-11-26
I was having this same problem.  It turned out the fix was pretty easy.

In the Add/Remove Applications window there is a Preferences button on the bottom left.

In that dialog was a window with the first tab being "Ubuntu Software" and a list of places where the software was Downloadable from the Internet

by default, all of these boxes were unchecked.  i checked them and hit close.  It ran through the update dialog again.

When i went to add or remove a program the window popped up again with the same error i had received before prompting me to reload.  this time when i clicked refresh it reloaded for real and i was able to add/remove everythign i wanted.

hope this works for you.

---

### Post by uzybear on 2007-11-26
fantastic; thank you so much; worked like a charm

i gotta admit it's a bit frustrating that linux is still like this, confusing for beginners, but i'm stoked that add/remove is working now, definitely wanted it

---

### Post by totlinuxnewbichik on 2008-06-08
Great trick!

What about for removing probrams? I can't seem to find a way to remove anything, or shut down anything with xfce xubuntu.

---

