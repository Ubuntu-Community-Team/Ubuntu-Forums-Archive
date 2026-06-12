---
title: "Opening files/folders as &quot;root&quot; in Nautilus"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-11-21
Just wondering if anyone has come up with a way to do this yet. It is still a "to do" item in the 7.10 How To. I tried the Fiesty method for my Gutsy install and still no go. In fiesty if you right click a file you get a "Scripts" option with "Open as root" in the dropdown menu. Any ideas ??

---

### Post by carlosjuero on 2007-11-21
Well, one way to do this is to open terminal and then type ```
gksudo nautilus
```, this will prompt for your SU password in a graphical dialog and then launch an instance of nautilus (you can also create a script to do it most likely and just run the script).

It isn't exactly what you want, but its an option - I am sure someone else will be along with a fix that does exactly what you need though :)

---

### Post by bluepowder7 on 2007-11-21
Alt-F2, and then type in "gksudo nautilus" and hit the ok button.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

scroll to the "Making system-wide changes graphically" section

---

### Post by jerrynewt on 2007-11-21
Duh - right in front of me !! Thanks guys, been at the desk here for tooooo long today. I just created a launcher for root file browser, and set the properties of the launcher to gksudo nautilus and booyaa ! Thanks again for the wake-up.

---

### Post by AndyCooll on 2007-11-21
There's a Nautilus addon in the repos called nautilus-gksu. It adds an "Open as adminstrator" option to the right click context menu.

:cool:

---

