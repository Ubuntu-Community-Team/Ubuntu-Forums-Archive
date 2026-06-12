---
title: "Can I turn off user passwords?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by jeramiahx on 2007-08-28
[COLOR="Blue"]**[LEFT][SIZE="1"][FONT="Comic Sans MS"]I understand the security issues of turning off user passwords but I don't feel their is any treat on my end. I have searched and searched through the forums to find out the answer but I can not figure out how to disable the user passwords. I share my computer with 3 people and as soon as I get off somebody else gets on and having to type in passwords everytime gets annoying. HOW TO DISABLE THE USER PASSWORDS? Can somebody please help a newb?[/FONT][/SIZE][/LEFT]**[/COLOR]:KS

---

### Post by aysiu on 2007-08-28
Try this:
[HowTo: Create a Passwordless / Guest Login (Simple Method)](http://ubuntuforums.org/showthread.php?t=513820&highlight=passwordless)

---

### Post by jeramiahx on 2007-08-28
For some reason when I transfer between users it ask me for my password twice. Your method worked on the first password but not the second one......... how do I disable the second one?

---

### Post by jeramiahx on 2007-08-28
I switch users and when i log back onto another user it ask me for my password on the log on screen and then it has a screen pop up and it ask me again......... I have disables everything and I can't figure it out..

---

### Post by dwhitney67 on 2007-08-28
> **jeramiahx said:**
> [COLOR="Blue"]**[LEFT][SIZE="5"][FONT="Comic Sans MS"]I understand the security issues of turning off user passwords but I don't feel their is any treat on my end. I have searched and searched through the forums to find out the answer but I can not figure out how to disable the user passwords. I share my computer with 3 people and as soon as I get off somebody else gets on and having to type in passwords everytime gets annoying. HOW TO DISABLE THE USER PASSWORDS? Can somebody please help a newb?[/FONT][/SIZE][/LEFT]**[/COLOR]:KS

Ugh, what an ugly and unpleasant font!

If you want 2 or more persons to share a computer and not have to login, then don't logoff or enable the password-protection when the screen saver kicks in.

---

### Post by jeramiahx on 2007-08-29
Everybody has their own user account and I want to keep it that way. I have also tried this:



Press alt + F2. Type in gconf editor. then go to apps --> gnome-power-manager. Search for lock_on_blank_screen and uncheck it.

if you like the command line, you can do it by
Code:

> gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings false

No luck there either..........

---

### Post by dwhitney67 on 2007-08-29
See if this works:

Add the following statement to the **/etc/gdm/gdm.conf-custom** file:

[FONT="Courier New"]PasswordRequired=false[/FONT]

This option should be placed directly following the [security] line since it pertains to that section.

Btw, this option is currently commented out in gdm.conf, the sister file of gdm.conf-custom.  According to the instructions, one should not edit gdm.conf.  To edit the gdm.conf-custom file you must have root-privileges (i.e. use sudo when editing).

P.S.  Let me (and the rest of the forum) know if this works or not!

---

### Post by jeramiahx on 2007-08-29
no beans.............................................

---

### Post by marco123 on 2007-08-29
If you don't care about security just use a really simple password like "lll".

---

### Post by dwhitney67 on 2007-08-29
> **jeramiahx said:**
> no beans.............................................

I think I found what you need.  Here is the [link]("http://ubuntuforums.org/archive/index.php/t-12777.html") to the post.  Look at the entry one up from the last.

---

### Post by jeramiahx on 2007-08-29
dwhitney67- works great but after a user logs back in the screen goes to black and a small screen asking for a password pops up and it won't let me bypass that one.

aysiu- your way works too but I'm still having problems with the small log in screen. It won't let me bypass it. the only difference between yours and dwhitney67 is that your way you have to press enter after clicking the name....

---

### Post by jeramiahx on 2007-08-29
So when someone switches to another user it goes to the lock out screen and it will not let me bypass it. I still have to type in a password. I have tried to bypass the lock screen through :

gconf-editor 
gnome-power-manager

but it still comes up..................................

I can't turn it off........

---

### Post by dwhitney67 on 2007-08-30
The instructions I provided to you apply to the GDM login screen, not the password protected screen that is displayed when you switch users.  I do not know enough about Gnome to help you there.

Btw, have you considered logging OFF before you leave the workstation so that the next person can login.  In other words, don't use the "switch user" feature.

Also, would it not be possible to access the system from another computer using SSH?

---

