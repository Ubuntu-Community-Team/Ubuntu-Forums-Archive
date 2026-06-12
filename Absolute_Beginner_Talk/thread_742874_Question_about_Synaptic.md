---
title: "Question about Synaptic"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by iSplicer on 2008-04-02
Hey all!

I just installed visualboyadvance from synaptic (visualbotadvance-gtk also installed visualboyadvance) all seemed to go fine, but the application is nowhere to be found (not in applications)! Can someone please help?

Thanks

---

### Post by taavikko on 2008-04-02
Not every program has a menu item.

You can always start programs in the command line
propably
```
visualboyadvance-gtk
```
does the trick.

And you can edit menus to include every command you like
```
alacarte
```
and add new launcher

---

### Post by mikeserv on 2008-04-02
Look in /usr/bin

And, for the hell of it, try typing "visualboyadvance" at the terminal prompt.

-Mike

---

### Post by iSplicer on 2008-04-02
Thanks for the reply, guys, but I got this problem:

```
isplicer@PEGASUS-III:~$ visualboyadvance-gtk
bash: visualboyadvance-gtk: command not found
isplicer@PEGASUS-III:~$ 

```

anyone?

---

### Post by mikeserv on 2008-04-02
Did you try it without the gtk?  Did you look in /usr/bin?

The filename might not be visualboyadvance exactly (though it is good practice to list installs that way).

-Mike

---

### Post by iSplicer on 2008-04-02
its in /usr/bin, although the command "vba" works.

I will try that and post here if there are any problems, thanks to all that helped!

---

### Post by mikeserv on 2008-04-02
There's a link in /usr/bin called "vba."  Run it from the command line.

-Mike

---

### Post by mikeserv on 2008-04-02
Oh, and I found the gui for it, too.  Man, those developers suck at listing their programs.  The gui is "gvba."  Just create a launcher for it, and stick it in games or something.  You can edit the menu by right clicking on the menu and selecting "Edit Menus."

-Mike

---

### Post by iSplicer on 2008-04-04
> **mikeserv said:**
> Oh, and I found the gui for it, too.  Man, those developers suck at listing their programs.  The gui is "gvba."  Just create a launcher for it, and stick it in games or something.  You can edit the menu by right clicking on the menu and selecting "Edit Menus."

-Mike

Thankyou for that my friend, thanks to you!

---

