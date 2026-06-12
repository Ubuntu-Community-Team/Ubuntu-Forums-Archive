---
title: "cursor theme switches back and forth for one user"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-12-27
this is annoying and I can't seem to find a solution. When hovering over a application window the proper theme is shown, but when hovered over the desktop it reverts back to the old theme instantly. so unless I have a window maximized I can actually watch the cursor theme switch back and forth as I move it in and out of the application window. It works fine for all other users on the computer, and I have tried several different themes with the same result. Any ideas?

---

### Post by gezzabob on 2008-01-14
I have had this problem and it is a tad annoying.  Is it still happening or has this been resolved.

If not just to stop it annoying the hell out of you try this.  Its not a complete fix or explination but at least it may help.

Open a terminal as normal and copy and paste this in 

sudo update-alternatives --config x-cursor-theme

(put in your password)

and select a theme I would recommend using 1, it is /usr/share/icons/DMZ-White/cursor.theme. on mine.

and then either reboot or press Ctrl + Alt + Backspace to restart the xserver (ps save any work first as it will close all open programs etc).

Again its not the be all and end all of the problem but if it works (it did for me) it will probably be helpful.

There is a several treads on here somewhere ref to this problem have a look around and you may come across a better description and fix of the problem.

---

