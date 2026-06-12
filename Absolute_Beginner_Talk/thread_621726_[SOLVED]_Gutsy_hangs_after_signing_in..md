---
title: "[SOLVED] Gutsy hangs after signing in."
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Motorhead Kaze on 2007-11-24
Hi, ever since I "Upgraded" to Gutsy startup takes twice as long.  The startup process once I type in my name and i.d. is slow.  Today in fact the process stopped at the beige screen.  Ctrl+alt+bksp, and the 2nd and 3rd tries I got to my desktop image, but no system bars at the top or bottom, just the file icons I had on the desktop.

I shut off the PC, and restarted.  On the second attempt I got back to my usual Gutsy.  This isn't the first time Gutsy has hung up on the beige screen (the one before the "Human" screen) but the first time it's been THIS obnoxious.

I've also been having trips with installing Emerald and it killing my Compiz too, if that's any relevance.  Feisty was just fine man... what a drag.

---

### Post by n_i_c_k on 2007-11-24
Things you could try for investigation,

a) Create a file ~/.gnomerc containing
[INDENT]```
exec > gnome.log 2>&1
```[/INDENT]

Log out of gnome, log back in, see what appears in gnome.log.

[Is there an easier way to get at gnome's chit-chat?]

b) Add another user, using /usr/sbin/adduser or the like, and log in as that user.

---

### Post by Motorhead Kaze on 2007-11-29
Hey hey, that could be useful in the future too.
Once I have that file made, how do I put that text in it?  Are you saying open a terminal from that file/window and add that command?  Thanks for that too!

---

### Post by n_i_c_k on 2007-12-04
> **Motorhead Kaze said:**
> Once I have that file made, how do I put that text in it?
With a text editor.  Perhaps I don't understand your question.

> Are you saying open a terminal from that file/window and add that command?
Sorry, I don't understand that question.

---

### Post by Motorhead Kaze on 2007-12-23
Hi! I disappeared for a couple weeks, dang.  Sorry.  In the interim, I just went ahead and installed Gutsy again.  Not just because of the hanging, but Open Office and Gimp would just crash in the middle of use, and I'd lose whatever I'd been working on.  That was shite, so I just reloaded.

BUT!  I still wanted to try out the advice I got above, to learn something new.  I just opened a text editor, typed 
> exec > gnome.log 2>&1  in it, then saved it as the name  ~/.gnomerc .  I restarted Gnome and there was the gnome log, with this in it:

Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/kaze-desktop:/tmp/.ICE-unix/16300
** Message: Not starting remote desktop server
Initializing gnome-mount extension
Fontconfig error: "~/.fonts.conf", line 2: no element found
Fontconfig error: "~/.fonts.conf", line 2: no element found
Fontconfig error: "~/.fonts.conf", line 2: no element found
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.7

Fontconfig error: "~/.fonts.conf", line 2: no element found
  PID TTY          TIME CMD
Fontconfig error: "~/.fonts.conf", line 2: no element found
Fontconfig error: "~/.fonts.conf", line 2: no element found
Fontconfig error: "~/.fonts.conf", line 2: no element found
Fontconfig error: "~/.fonts.conf", line 2: no element found
Fontconfig error: "~/.fonts.conf", line 2: no element found
Fontconfig error: "~/.fonts.conf", line 2: no element found
Fontconfig error: "~/.fonts.conf", line 2: no element found

Does this have any meaning that I should be understanding?

****
Update:  Well, I guess this should be chalked up to "Just a dirty install of Gutsy".  Don't know why, but after installing fresh yesterday, with a complete reformat, Gutsy behaves nicely.

If at first you don't succeed...wipe the disc and reinstall.

---

