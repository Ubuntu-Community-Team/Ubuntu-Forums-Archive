---
title: "Need to access menu items"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by KauLad on 2008-02-14
Absolute new user here.

I need to access menu items (synaptic package manager) on the System menu. But it's not there.

Read two books on Ubuntu but they just gloss over the subject "Go to System->Administration->Synaptic" But !!! it is not there!

If someone could just point out some help pages or just how to term the search method, I would really appreciate it.

---

### Post by jan quark on 2008-02-14
open the terminal

I hope it is there

system > accessories > terminal

and type 
```
gksudo synaptic
```
and enter
you should see synaptic now

or get an error message, post the error

you can also add synaptic to the menu via the main menu
system>  preferences > main menu

---

### Post by PeterJS on 2008-02-14
How much is missing? The entire system menu, or just synaptic?

---

### Post by dhruva023 on 2008-02-14
go to : System > Preferences > Main manu,
and see if its checked there.

---

### Post by KauLad on 2008-02-14
Trying to use terminal -> gksudo synaptic
I get Gtk-WARNING **: cannot open display.


Trying to access Preferences: Menu
It is not there. There is Menus & Toolbars but it doesn't help

---

### Post by jan quark on 2008-02-14
what version of ubuntu do you use?

did the installation worked fine?

---

### Post by KauLad on 2008-02-14
Ubuntu 6.06 LTS
The install went just great!; it found my net, contacted the support site, downloaded
all the package updates and installed them. But, when I went to install OpenSSHD, I
got truncated menus.

---

### Post by jan quark on 2008-02-14
well

perhaps just remove OpenSSHD and we will see if that chages something

---

### Post by KauLad on 2008-02-14
Sorry, I misspoke. I started to install and could not find Synaptic.
That's what started this mess! Maybe I shouldn't have looked for it.

Thank you for your help. I suspect I need to dump this OS and try 
again.

---

