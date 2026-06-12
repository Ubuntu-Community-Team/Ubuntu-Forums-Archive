---
title: "Xubuntu Menu bars"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by gustasonfrever on 2008-03-08
I just installed Xubuntu last night and when I started up in the morning (today) my top/bottom menu bars disappeared. How can I get them back?

---

### Post by JeffoOfMetal on 2008-03-08
if you can manage to open the terminal, type in xfce-panel.

good luck!

---

### Post by gustasonfrever on 2008-03-08
Is there a short cut availible to open a terminal window?
I tried hitting alt-f2 and then typing the xfce-panel in that 'run program' window but it says 'Failed to execute child process "xfce-panel" (no such file or directory)

---

### Post by julian67 on 2008-03-08
you don't need the terminal, just Alt+F2 and enter the command in the dialog box

---

### Post by gustasonfrever on 2008-03-08
Thats what I did and I got this message 

'Failed to execute child process "xfce-panel" (no such file or directory)

---

### Post by alan34 on 2008-03-08
Need a terminal if you can get one then

cd ~

cd .config/xfce4

mv panel ~

(this means you can put it back)

then restart

Done it yesterday for a friend who had lost his

---

### Post by julian67 on 2008-03-08
> **gustasonfrever said:**
> Thats what I did and I got this message 

'Failed to execute child process "xfce-panel" (no such file or directory)

the command is not xfce-panel, it's xfce4-panel

---

### Post by gustasonfrever on 2008-03-08
That was it, thanks

---

### Post by gustasonfrever on 2008-03-08
I just tried shutting down by hitting the button in the top right corner, but instead of bringing up a menu with options to shut down, sleep, or logout it brings up 'Exit XFCE Panel' window 
How do I shutdown?

---

### Post by julian67 on 2008-03-08
try Alt+F4

---

