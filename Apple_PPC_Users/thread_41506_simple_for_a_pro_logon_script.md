---
title: "simple for a pro: logon script"
date: 2005-06-13
forum: Apple PPC Users
---

### Post by Kurbycar32 on 2005-06-13
all i want to do is set up ubuntu (ppc) to run the rdesktop -f (ip address) command on startup.  i also want to do the auto login but i already found [this](http://www.ubuntuforums.org/showthread.php?t=31310)

---

### Post by Xerampelinae on 2005-06-13
Well if you're just logging in from the console this should work:

Create the file .xinitrc and add whatever commands you want to run, one per line. (prepend the last one with exec to save some memory)

Then in your .bash_login put the command "startx" ... should work, although I haven't tested it.

---

### Post by Kurbycar32 on 2005-06-13
where should the .xinitrc file go?  and would simply entering startx execute the .xinitrc file? or is there more to it?

---

### Post by Xerampelinae on 2005-06-13
It goes in your home directory....   ~/.xinitrc

startx reads .xinitrc.. you could for example put in "exec gnome-session" and gnome would pop up when you type startx.

---

### Post by Kurbycar32 on 2005-06-13
it didnt work, no errors or anything, just nothing.  being from a windows enviroment i tried wrapping the rdesktop command in quotes (like this "rdesktop -f 192.168.0.1")  and i still got nothing.

---

### Post by desdinova on 2005-06-13
If you're using GDM - logging in graphically - then use Preferences - Sessions - you can set a program to run at startup there

---

### Post by Kurbycar32 on 2005-06-13
hey that was exactly what i wanted.  thank you.  i set it up to run in order 100 (i figured that would be last) and to run as a regular item and it does exactly what i need.  thanks alot!

---

### Post by Xerampelinae on 2005-06-13
[QUOTE=Kurbycar32]hey that was exactly what i wanted.  thank you.  i set it up to run in order 100 (i figured that would be last) and to run as a regular item and it does exactly what i need.  thanks alot![/QUOTE]
 Oops.  Guess you weren't logging in from the console after all... my original assumption..

---

### Post by desdinova on 2005-06-13
[QUOTE=Kurbycar32]hey that was exactly what i wanted. thank you. i set it up to run in order 100 (i figured that would be last) and to run as a regular item and it does exactly what i need. thanks alot![/QUOTE]

You're welcome ;-)

---

### Post by Kurbycar32 on 2005-06-14
[QUOTE=Xerampelinae]Oops.  Guess you weren't logging in from the console after all... my original assumption..[/QUOTE]

i plan on doing it from the console after i get everything else working, so later il need your instructions too.  thanks!

---

