---
title: "Composite Manager Faliure"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by HdK on 2006-09-02
When I start my KDE session I get an error that says Composite Manager Failure-Kdialog Composite extension not found
You must use XOrg &#8805; 6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your X config file:
Section "Extensions"
Option "Composite" "Enable"
EndSection

How do I fix this

---

### Post by lilchris173 on 2006-09-02
Hey its a very long process. 
Step 1: Look at the error message.
Step 2: Do what the error messages says.
Step 3: YOUR DONE!! lol!!

In a more detailed agenda... sudo nano /etc/X11/xorg.conf go to the veryyyyyyyy bottom and type this:
Section "Extensions"
Option "Composite" "Enable"
EndSection

Then press ctrl x then press enter enter. Now alt ctrl backspace (restarts X session so if you have a program running... let it finish). Now you should be good. If your not e-mail me at [email]lilchris173@yahoo.com[/email]. Unlike in windows errors will actually tell you stuff. I told you how to do that just from looking at your post and only your post. I wish you good luck.

---

