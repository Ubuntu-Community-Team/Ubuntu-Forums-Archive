---
title: "Where default application assignments for files types are saved?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by HuBaghdadi on 2008-02-24
Hi.
In Ubuntu, we can assign an application for each file type, for example:
Banshee for MP3, gedit for txt files and so on.
Under the hood, where those assignments are saved?
Thanks.

---

### Post by Mad_Gouki on 2008-02-24
I am not sure where those assignments are saved, but if you are looking to change the default program for opening a file type, you can right click on a file of that type, click properties (at the bottom), and click the "open with" tab.
there should be a few programs listed, if the one you want is there, click the little radio button by it, and then click close, now your program of choice will open that file type by default.
if your program of choice is not there, click add and check the list, if it is still not there, click the button by "use a custom command", you can browse for a program to use, or just type in the command (like: gedit).

hope this helps, if you still need to know which file actually contains the information, I will look into it for you :)

---

### Post by HuBaghdadi on 2008-02-24
Thank you, I know how to assign an application to a file type.
I'm just wondering where those assignments are saved...

---

### Post by Mad_Gouki on 2008-02-24
From what I can tell, ubuntu uses mime for that
the file you want may be one of these, but be careful editing them (back them up!), because I don't know what editing them could do
/usr/share/applications/defaults.list
/etc/mime.types
i think the applications/defaults.list is the one you want tho.

---

