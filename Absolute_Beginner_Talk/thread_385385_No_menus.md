---
title: "No menus"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by gacostac on 2007-03-15
Hi
I was installing some programs using automatix2. When the installation finished automatix told me that it wasn't able to installed them. After that my computer froze and I had to restart it. 
When it came back up, i had no top or bottom menus. I restarted a couple of times to see if it fixed itself, but it didn't work.
I would really appreciate if someone could give me a step by step solution, since i am completely new to ubuntu and linux
Thanks
Gabe

---

### Post by annda on 2007-03-15
if you use gnome, try hitting Alt+F2 and typing gnome-panel

hope this helps and you can configure your panels and save the configuration.

---

### Post by gacostac on 2007-03-15
nothing happens when i hit alt f2.....

---

### Post by drs305 on 2007-03-15
How about:

killall gnome-panel

---

### Post by annda on 2007-03-15
this is very strange - ALT+F2 should bring up a window where you can enter commands...

is your desktop still intact (icons etc.)? does right-clicking your mouse on the desktop give you a context menu? if so, create a launcher with gnome-panel as the command and click on it.

---

### Post by gacostac on 2007-03-15
where do i have to input that? Nothing happens when i hit alt+F2. when i hit alt+F4 i get something like a terminal. should i put it there? how do i get out of it once i am done?
Thanks a lot

---

### Post by gacostac on 2007-03-15
yes, the desktop is intact with icons and everything. I will try right clicking and doing what you said.

---

### Post by gacostac on 2007-03-15
wow!!! that worked!! thanks a lot. Any ideas on what is the problem? should i check something in my computer to see what happened and make sure it doesn't happen again?
Thanks a lot

---

### Post by annda on 2007-03-15
i'm glad that it worked out. i have absolutely no idea what happened to you but definitely some gnome configuration went wrong at some point...

make sure you still have your panels after logging out and back in, and even after reboot.

for safety reasons, you can always back up your home directory. if something goes wrong again, just restore the old (working) files, especially everything that starts with "." - those are all hidden configuration files.

---

