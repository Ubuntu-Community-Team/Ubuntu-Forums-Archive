---
title: "issues wth permission"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Robert98374 on 2007-05-02
Hello all,
Heres the issue. I am trying to install some skins for the Media player XMMS but when i try to move the skin files over it states 

Error while copying to "/usr/share/xmms/Skins".
You do not have permissions to write to this folder.
what can i do to fix that?

---

### Post by qpieus on 2007-05-02
Add sudo to the front of whatever copy/move command you used. The directory you are copying to is owned by root, so you need to use sudo.

---

### Post by Robert98374 on 2007-05-02
I dont know how to move stuff with the terminal so i am doing it with the file browser

---

### Post by Vajra Vrtti on 2007-05-02
Open and type
> sudo nautilus
This will open Nautilus with root access, so be **_VERY CAREFUL_**! Copy the files you need and close it.

---

### Post by Robert98374 on 2007-05-02
Thanks that will help alot!
Is there anyway of making a icon on the desktop so that i can just double click that instead of getting in the terminal?

---

### Post by bobplano on 2007-05-02
i suggest ```
gksudo nautilus
``` why?
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
and its just good practice

---

### Post by Vajra Vrtti on 2007-05-02
I use 2 Nautilus scripts to do that. One is to open Nautilus in root mode and the other to gedit a file as root. You access them with the mouse right button (option **Scripts**). I'm sending them in the attached file. Put them in **~/.gnome2/nautilus-scripts** (in Nautilus, use *View->Show Hidden Files* to see this directory).

---

### Post by Robert98374 on 2007-05-03
Alright will try that one out thanks :-)

---

