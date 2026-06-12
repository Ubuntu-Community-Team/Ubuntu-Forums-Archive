---
title: "A few problems"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by CorryJm on 2008-02-10
First: I was creating folders inside of my music folder and then all of a sudden all of the icons disappeared and I had to force quit the window.  After this happened the desktop also seemed to stop functioning with all of the icons disappearing.

This is fixed with a restart, but then each time I try to access my Music folder the same thing happens.

this is all in my Home folder (which is showing as my desktop)

which is my second problem... my home folder is showing as my desktop!
I believe I accidentally dragged it on there, but can't seem to undo it.
Someone directed me towards a gconf-editor menu before, but it didn't seem to do the trick.

third problem: a lot of graphical glitches happen while I'm using anything.  A portion of a window may become discolored, or lines will randomly shoot across the screen or portions of a window will stay behind after closing or moving a window.
this is all easily fixed with click the "show desktop" button then bringing the window up again, but I'd like to know if there was some way to stop it.

thanks and sorry for the mass of problems and huge post =x

---

### Post by rainwalker on 2008-02-10
The issue with the folder messing up and having to force quit the window has happened to me before, and I haven't figured out what causes it or a definite way to fix it. What I did was drag the bad folder to my desktop, then make a new folder where that one used to be, then just copy everything from the old folder to the new one (command line), and then deleting the old folder.
To fix the thing with your home folder being your desktop, open a terminal and run "gconf-editor", then go to apps > nautilus > preferences and make sure the box for "desktop_is_home_dir" is not checked.

---

### Post by CorryJm on 2008-02-11
> **rainwalker said:**
> The issue with the folder messing up and having to force quit the window has happened to me before, and I haven't figured out what causes it or a definite way to fix it. What I did was drag the bad folder to my desktop, then make a new folder where that one used to be, then just copy everything from the old folder to the new one (command line), and then deleting the old folder.
To fix the thing with your home folder being your desktop, open a terminal and run "gconf-editor", then go to apps > nautilus > preferences and make sure the box for "desktop_is_home_dir" is not checked.

it isn't checked.
I had been directed to do this before, but then no reply after I responded that
the box was already unchecked.

is there possibly another cause?

PS: sorry about making 2 threads, I lost track of this one (beginner forums fill up pages fast) and wasn't even sure if I had posted it at all, so I made another.

---

### Post by MONODA on 2008-02-11
> it isn't checked.
I had been directed to do this before, but then no reply after I responded that
the box was already unchecked.
the check it, restart your computer then if it your home folder is still your desktoptop then go to the same place and uncheck it then restart. that may solve it.

---

### Post by CorryJm on 2008-02-13
still no results

checked the box, restarted, then unchecked it and restarted again

my home directory is still showing as my desktop!

sadness :(

is there any more info I could give that would help in discerning the problem?

---

### Post by MONODA on 2008-02-13
hhhmmm... try and log in as root see if your home is also your desktop then

---

### Post by CorryJm on 2008-02-13
> **MONODA said:**
> hhhmmm... try and log in as root see if your home is also your desktop then

sorry.
log into root?

---

### Post by MONODA on 2008-02-14
oh sry. Go System->administartor->login window. click security and make sure that "allow locacl system administrator login" is checked. Then log out. But dont login as your normal user name, login with the name "root" but with the same password for your account.

---

### Post by hyper_ch on 2008-02-14
next time use a descriptive thread title and not a generic "need help" one.

---

### Post by CorryJm on 2008-02-16
> **MONODA said:**
> oh sry. Go System->administartor->login window. click security and make sure that "allow locacl system administrator login" is checked. Then log out. But dont login as your normal user name, login with the name "root" but with the same password for your account.

I have the "allow local system administrator login" checked and tried to log into root using my password for my normal account, but got the error message that I had put either the login or password in wrong.
I tried several times to ensure I did it right, but always got the message.

and Hyper_ch, sure thing, next time i'll be more specific with my thread title.

---

