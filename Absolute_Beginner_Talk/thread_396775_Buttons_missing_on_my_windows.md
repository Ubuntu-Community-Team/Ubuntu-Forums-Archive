---
title: "Buttons missing on my windows"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by ronald_stall on 2007-03-29
Sometimes when I login to my Edgy desktop the buttons in the top right corner that minimize, maximize, and close my windows do not appear and you cannot resize or move the windows. Any idea why this may happen and a fix to it?

---

### Post by dbbolton on 2007-03-29
which window manager are you using ?

---

### Post by ronald_stall on 2007-03-29
Using Gnome, GL Desktop, Compiz, does that answer what you need?

---

### Post by dbbolton on 2007-03-29
ok. at the login screen, in the lower left corner, click options, select session, and choose Failsafe Gnome. do you still have missing buttons in the failsafe session ?

---

### Post by jem7v on 2007-03-29
It might be happening because you're using Compiz and it's not perfect.  I think I had that issue for a little while when I was still using it.  One obvious solution is to stop using Compiz, but that's sort of lame.

---

### Post by seshomaru samma on 2007-03-30
It's a compiz problem 
I had compiz before and experienced a similar problem
I solved it by changing the theme , if I'm not mistaken

---

### Post by jem7v on 2007-03-30
Now that seshomaru samma left that message, that's ringing a bell for me.  That's right - some Metacity themes (aka Window Border) just don't work with Compiz.  Go to System>Preferences>Theme and just switch that to something else, I guess... (You can switch specifically just window borders if you click the Theme Details button.)

---

### Post by ernstblaauw on 2007-03-30
My Window Manager never starts. I had Beryl, but I uninstalled it. How can I enable a Window Manager automatically?

---

### Post by seshomaru samma on 2007-03-30
> **ernstblaauw said:**
> My Window Manager never starts. I had Beryl, but I uninstalled it. How can I enable a Window Manager automatically?

What do you mean?
If you uninstall Beryl should be left with metacity

---

### Post by mech7 on 2007-03-30
I had the same thing on feisty yesterday.. somebody told me to enter metacity --reinstall and it worked :)

---

### Post by anaconda on 2007-03-30
> **ronald_stall said:**
> Sometimes when I login to my Edgy desktop the buttons in the top right corner that minimize, maximize, and close my windows do not appear and you cannot resize or move the windows. Any idea why this may happen and a fix to it?

quick and dirty "fix"
you can move the window with Alt and left mouse button
and if you press Alt and right mousebutton you can minimise, maximize, resize or close the window..

---

### Post by ernstblaauw on 2007-03-30
> **seshomaru samma said:**
> What do you mean?
If you uninstall Beryl should be left with metacity
> **mech7 said:**
> I had the same thing on feisty yesterday.. somebody told me to enter metacity --reinstall and it worked :)
I had Beryl installed on Edgy and updated to the Feisty beta. Ubuntu automatically uninstalled/disabled Beryl and now no Window Manager is started in Feisty. I will try metacity --reinstall.
Thanks for all your help!

---

### Post by ernstblaauw on 2007-03-30
> **mech7 said:**
> I had the same thing on feisty yesterday.. somebody told me to enter metacity --reinstall and it worked :)
I tried it, but metacity does not recognize the option --reinstall. Do you know for sure it was that option?

---

### Post by dbbolton on 2007-03-30
metacity --replace

---

