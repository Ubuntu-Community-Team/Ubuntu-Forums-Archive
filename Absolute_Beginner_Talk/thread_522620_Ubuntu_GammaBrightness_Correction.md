---
title: "Ubuntu Gamma/Brightness Correction"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by speaker219 on 2007-08-10
Can anyone help me with this?
on windows, i have a utility to change gamma/brightness/contrast values, etc.
i want to do this on ubuntu. any help would be appreciated.
 i know of xgamma but i need something that can also control brightness (i know about the Fn+ combo, but this isn't what i'm talking about, its a brightness control utility that does something not hardware related [i think])

on windows, i have the following (see screenshot)

is there a ubuntu equivalent?

---

### Post by speaker219 on 2007-08-10
Please help guys.

---

### Post by speaker219 on 2007-08-12
I FIXED IT!!! ;) Pardon me, i'm very excited ;)

Anyway, here's how i fixed it. I was googling and found this program:
[http://www.softpedia.com/get/Tweak/Video-Tweak/Gamma-Panel.shtml](http://www.softpedia.com/get/Tweak/Video-Tweak/Gamma-Panel.shtml)

It was a windows app, so last resort i figured, hey, i might as well sudo apt-get wine and try this out.

To my surprise, IT WORKED! I was able to control brightness, contrast, AND GAMMA!

GO WINE! (AND THE GUY THAT WROTE THE PROGRAM)
Hope this helps anybody with the same problem

---

### Post by rosegarden78 on 2008-01-19
Try typing the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

