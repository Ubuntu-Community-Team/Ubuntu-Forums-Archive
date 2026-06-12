---
title: "How to get Terminal when panels are missing"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by muddler on 2008-02-01
Is there a way to use terminal without using panels. Mine are missing. My screen is blank.

---

### Post by gazj on 2008-02-01
press alt+f2

then type

gnome-terminal

then press enter

---

### Post by PinkFloyd102489 on 2008-02-01
If you wish to launch a new panel, enter gnome-panel in the Alt+F2 prompt.

---

### Post by muddler on 2008-02-01
Thanks, I got the Terminal. I thought I was smart enough to take it from there but I was mistaken. Using gnome-panel was not successful. 
Once I get to terminal, what do I do to get my panels back?

---

### Post by jipke on 2008-02-02
As far as I know, it is impossible to remove the last panel. So there should always be at least 1 remaining on the desktop. Is the gnome-panel process running? Yes? Try to restart it by killall gnome-panel. If not, what output do you get when trying to start it by entering gnome-panel in a terminal?

---

### Post by muddler on 2008-02-02
After entering "gnome-panel" I get no response. The screen does not change.

---

### Post by Ardrias on 2008-02-02
I've had the same problem. Delete your .gnome configs and restart X, should solve it.

---

### Post by bumanie on 2008-02-02
What type of video card are you using?

---

### Post by Kevbert on 2008-02-02
To restart Xserver try pressing Alt-Ctrl-Backspace.  This also works if your desktop locks up, but you may loose information from any opened documents.

---

### Post by muddler on 2008-02-02
Problem solved! I have no idea what happened. I used alt+ F2, entered gnome-panel and received the Error Message: Failed to execute child process "/home/park/.gnome/application-info/user.applications" (Permission denied)  However, the panels reappeared. Thanks to each of you for your help.

---

