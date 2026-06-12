---
title: "splash screen"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by amtnbiker16 on 2007-10-02
okay, so i downloaded this splach screen off of somewhere, probably the gnome website, and the readme file told me to do this...

Open the Terminal from your Accessories menu and type  

sudo nautilus  

into it and press Enter, type in your password and press enter again to open the Root Browser (that's the entire extent of CLI for this procedure - the rest is very Windowsian). Then navigate through the following folders  

File System > usr > share > pixmaps > splash  


the problem is that it wont let me write to that file because i dont have permissions or something, but it wont let me authenticate.

whats the matter with it?

---

### Post by Perfect Storm on 2007-10-02
Check point 6 in my guide: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by Gremlinzzz on 2007-10-02
try gksudo nautilus

---

### Post by dca on 2007-10-02
Is it a splash screen or a bootsplash screen?  The splash screen is what you see after you login to your system.  The bootsplash is what you see prior when it's loading/starting all services...

---

### Post by amtnbiker16 on 2007-10-02
i dont think that the (login) splash screen was designed to run under the splash screen manager, but i was also wondering how come i was being denied access to my own files

---

