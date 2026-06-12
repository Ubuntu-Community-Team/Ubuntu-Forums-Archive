---
title: "Resolution problem help please"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by CharlieChadson on 2005-06-27
I am completely new to linux.  I have been trying to change the screen resolution to something other than 640x480.  I have seen some stuff on trying "sudo gedit /ect/X11/xorg.conf" in the terminal but all i get is a message that says:

(gedit:8054): GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Can someone please help me with this problem so that everything on the screen won't be so huge.  Thank you very much.

---

### Post by mtron on 2005-06-27
it's "sudo gedit /**etc**/X11/xorg.conf" not ect..

also if you don't like the command line, type "sudo gedit" and then open the file from within gedit.

---

### Post by rockmusic88 on 2005-06-27
you mean **sudo gedit /etc/X11/xorg.conf** not **sudo gedit /ect/X11/xorg.conf**.

and the error message seems to be a standard error messege that has nothing to do with the misspelling becasue i get the same error message on my system and all works fine.

But if you want to do thigns the easy way you could always go to system>prefrences>Screen Resolution.

---

### Post by CharlieChadson on 2005-06-27
Oops, it was just me typing it wrong.  I got it all fixed now.  Thanks for all your help

---

### Post by mtron on 2005-06-28
[QUOTE=rockmusic88] the error message seems to be a standard error messege that has nothing to do with the misspelling [/QUOTE]

No, it's not a standard error, i don't get it.

cheers 
mtron

---

