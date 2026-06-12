---
title: "Installing with apt-get: where do they go?"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by jms830 on 2006-03-01
I do not understand how things are installed in ubuntu.  I windows, you install the program and a GUI allows you to select where you want the program installed to (for instance C:\program files) and then whether you want shortcuts in your start menu or on the desktop.  When I use apt-get install, I have no idea where the program goes or how to run it once its installed. For instance, I just typed "sudo apt-get install winesetuptk". Now how the heck do I run the program? I went to the home folder via "cd ~" and typed winesetuptk, but it cannot find it.

---

### Post by aysiu on 2006-03-01
Wine is a special case because it's not an application unto itself. It's a helper application that lets you run .exe files.

A normal graphical application (that launches by itself) usually has a menu icon created for it and can be launched by a simple typing of the command, too (Alt-F2 and then ```
nameofprogram
```)

Just to satisfy your curiosity, though, most programs executables live in /usr/bin

---

### Post by PsychoTrauma on 2006-03-01
They are usually installed to /usr/bin/ and you can start the application by hitting alt-f2 then typing the name of the program.

edit:aysiu beat me to the answer.

Also once you know the name of the executable you can use a menu editor to add it to your menu list.

---

### Post by chimera on 2006-03-01
just type

```

whereis applicationname

```

that should tell you where it's installed.

---

