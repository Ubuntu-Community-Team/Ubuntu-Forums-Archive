---
title: "error 40"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by goatbaby on 2006-05-10
ok i have searched and searched but can't figure this one out. after log in i get a 10 second error that says : error while loading shared libraries: LIBESD.SO.0 cannot open shared object file error 40.
 
i was trying to fix my sound and when i restarted i got this message. 
any ideas on how to fix this?

thanks

---

### Post by 1337hacker on 2006-05-10
can you give more of the error message?

---

### Post by Monster_user on 2006-05-10
[QUOTE=goatbaby] : error while loading shared libraries: LIBESD.SO.0 cannot open shared object file error 40.[/QUOTE]
LibESD...

ESD, or the eSound daemon is a Linux sound manager, mostly used by Gnome, or Ubuntu.
What did you do to try to get your sound to work?

My recomendation would be to run "Synaptic", and then reinstall any ESD packages you find.

I do not recall where Synaptic is in the Breezy Badger applications menu.

You can press "Alt-F2" to bring up a Run dialog box. Then type

> gksu synaptic

It will ask you for your password. Then click the "Reload" button, to check for updates online.

Then you should click "Edit -> Search", and do a search for "esd".

Click on the "check box" on the left of every package that comes up, and select "Mark for Reinstallation". Then click Apply.

---

### Post by goatbaby on 2006-05-12
ok here is the error message
your session only lasted longer than 10 seconds. if you have not logged out yourself this could mean that there is some installation problem or that you could be out of disk space. try logging on with one of the failsafe sessions to see if you can fix this problem. 

details 
etc gdm presession default: registering your session with wtmp and umtp
etc gdm presession default: running:  usr bin x11 sessreg -a -w var log run utmp -x "var -h "" -l ":0" "adam"
etc gdm presession default: beginning session setup...
x session manager error while loading shared libraries: libesd.so.0 cannot open shared object file error 40

i cannot log in to get to synaptic, tried with failsafe terminal and rejected my password and locked up. 

i was trying to get sound to work, using this method [http://www.ubuntuforums.org/showthread.php?t=8882](http://www.ubuntuforums.org/showthread.php?t=8882) .

thanks for the help

---

