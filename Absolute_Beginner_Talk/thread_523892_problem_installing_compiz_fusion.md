---
title: "problem installing compiz fusion"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by whiffy badger on 2007-08-12
I've been following this thread trying to get compiz fusion working on an intel laptop:

[http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion)

When I put "compiz --replace" into the command line I get this:

newton@Computer3:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:9608): Wnck-WARNING **: Unhandled action type (nil)
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


So can anyone tell me what's gone wrong with this compiz fusion install -  Thanks!

---

### Post by schorsch on 2007-08-12
Which graphic card are you using?

---

### Post by whiffy badger on 2007-08-12
I  have an intel 945 gm express chipset.  I did have Compiz fusion working before - it  worked using trevino's repository.  However, on seeing this new thread I decided to try to update.  Bad move!

---

### Post by schorsch on 2007-08-12
I am running beryl (not compiz-fusion!) on the desktop in my office with the same graphic card according to
[http://doc.gwos.org/index.php/BerylOnEdgy#Intel]("http://doc.gwos.org/index.php/BerylOnEdgy#Intel")
and it was running before I went into holiday one week ago. But I cannot check if it still runs today as I am ........ away from office :-)

---

### Post by E-rock on 2007-08-12
I was running Compiz-Fusion also, (not beryl) and I've been having the same problem ever since I tried updating.  I've tried at least 3 or 4 different methods of installation and even another repository I found, But I get the same error. I got it running once, but with only half of the options I used to have and without the cube working (even though that was one of the options that I *did* get), and although I tried to keep it figuring I could always fix it later, when I logged back in the next day and entered compiz --replace, It wouldn't work and gave me that same error again.

By the way I'm running a GeForce 6800 with the new drivers.

---

### Post by Niklas Schröder on 2007-08-12
i have a similar graphics card and following this tutorial...

[http://ubuntuforums.org/showthread.php?p=2895086](http://ubuntuforums.org/showthread.php?p=2895086)

gave perfect results.  :)

---

### Post by E-rock on 2007-08-12
Awesome, Thanks Niklas, I got compiz-fusion to start... but it didn't have windows borders, so I somehow thought it would be brilliant to try using emerald to give it window borders... and now neither one of them work, even after removing and re-installing them both. Is there something I'm not removing completely, or installing correctly (the same way that made them work fine last time), or does XServer just hate me?

---

### Post by Niklas Schröder on 2007-08-13
woops.  :p  forgot to tell you that.  ^_^;  use this.

```

compiz --replace -c emerald &

```

---

### Post by whiffy badger on 2007-08-13
Following this thread:

[http://ubuntuforums.org/showthread.p...=compiz+fusion](http://ubuntuforums.org/showthread.p...=compiz+fusion)

has knocked out what was a working  compiz fusion on my laptop.  I have tried the guides including the one above so to try to  reinstall compiz using trevino repositories but without success.  I can still access the compiz config settings manager but nothing works in it be it rotating cube desktops or anything else.

Unless anyone else have any ideas as I don't fancy reinstalling ubuntu again!

---

### Post by Arthur Archnix on 2007-08-13
I too had compiz working using Tevino's repos, then it partially worked with the new ones. I'd say leave the desktop effects alone for a week, then go back and try again. The thread where everything is broken links to ubuntu's official maintainer, so you'll get no better support than by paying attention to that thread. Amaroth I think it was. Anyway, they just transitioned, so give it a week and then try again.

---

### Post by Paul133 on 2007-08-14
Ah, so we should stick with Trev's repo's?

---

