---
title: "Lost Right-click menu in Xubuntu"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Brendantb on 2007-02-05
Hi, 

Another small problem: I have just noticed that the right click menu, with create launcher, etc, is missing. Could I have unclicked it in some settings menu?

---

### Post by john.nicholls on 2007-02-05
The usual reason is that xfdesktop has stopped running. Just use alt-F2 to get a terminal and type in xfdesktop.

---

### Post by Brendantb on 2007-02-05
Hi, thanks for replying. 

The xfdesktop command did reinstate the right click menu, but only so long as that terminal window remained open. 

I think the problem was that the "Let Xfce manage the desktop" option in settings, desktop settings had become unchecked. I checked it, and logged in and out, and it seems to be working normally now.

---

### Post by Brendantb on 2007-02-07
I don't know if this is a bug or just my system: 

When I check hide panel, I lose the right click menu on the desktop. In settings, desktop, the check in "allow Xfce to manage the desktop" is missing, though it was previously checked. 

I'm using Xubuntu with the Xfce 4.4 beta2 (4.3.99.1)

---

### Post by john.nicholls on 2007-02-08
> The xfdesktop command did reinstate the right click menu, but only so long as that terminal window remained open.
This will happen if you use an ordinary terminal, but not if you use alt-f2 to access the run command.

> the check in "allow Xfce to manage the desktop" is missing, though it was previously checked.
I've struck this before. Make sure you have selected the save the session option. Sometimes it just seems to take a few tries to get this setting to stick.

John

---

