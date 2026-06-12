---
title: "graphical sudo"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by dsbw on 2007-08-19
I know about gksudo and still have a question:

I want to copy files from a network drive over to the /var/ folder, but I don't get prompted for a password, I get denied.

I can manage this any number of other ways, I'm sure, but am curious as to whether there is a way, from the GUI, to do things like this (file management) without dropping to a command line. Although the CLI is more efficient in most cases, in some cases the GUI is better (but obviously not if you have to drop back to the CLI to start up a GUI app).

Tx.

---

### Post by Hobo Joe on 2007-08-19
If you want to transfer the files with Nautilus, but you don't have the permission, you need t ALT+F2, and type: 
```

gksudo nautilus

```

That will give you a browser with full root rights.

---

### Post by Falcorian on 2007-08-19
> **dsbw said:**
> I know about gksudo and still have a question:

I want to copy files from a network drive over to the /var/ folder, but I don't get prompted for a password, I get denied.

I can manage this any number of other ways, I'm sure, but am curious as to whether there is a way, from the GUI, to do things like this (file management) without dropping to a command line. Although the CLI is more efficient in most cases, in some cases the GUI is better (but obviously not if you have to drop back to the CLI to start up a GUI app).

Tx.

You could try opening Nautilus with gksudo. That should give you a root gui.

---

### Post by dsbw on 2007-08-19
'preciate the help, guys.

I get "Gtk-WARNING **: cannot open display:"

It's sorta not the point though. 'cause if I go to a command line, I can sudo cp them anyway, right? I'm just talking about a situation where I happen to have the source folder open in one window and the destination folder open in the other and wanna do a drag/drop. Sometime Ubuntu asks, other times it just denies. Is there any way to force it to ask?

---

