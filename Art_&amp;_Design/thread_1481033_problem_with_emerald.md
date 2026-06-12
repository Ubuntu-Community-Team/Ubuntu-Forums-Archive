---
title: "problem with emerald"
date: 2010-05-12
forum: Art &amp; Design
---

### Post by Steo_Walsh on 2010-05-12
sorry if this is in the wrong place but i'm new to the forums and relatively new to ubuntu. anyway i'm having troubling make emerald set my default theme. i can import the theme then when i go into a terminal and put in 'emerald --replace' the theme changes to the theme i want. the problem is when i go to close the terminal i get a message saying the a process is still running in the terminal, so if i want my theme i have to keep the terminal open, if i kill the terminal then i lose my theme. any help would be greatly appreciated

---

### Post by texpat on 2010-05-12
Hi,

a quick fix for your problem would be to send the process to the background. Your command would look like this:
```
emerald --replace &
```
You will continue to have a prompt from which you can keep working in the terminal.

Ultimately, you will probably want to run emerald at startup so you don't have to do this every time you turn your computer on. I'm afraid I don't know how to do that off the top of my head, but if you search these forums you should find an answer since this must be quite a common thing.

Good luck!

Oh, by the way: emerald is not a 'theme', its a desktop manager (I think that's the word for it). Themes are the styles of window borders, buttons, icons, and so on that emerald uses. You can change those in System-Preferences-Appearance.

---

### Post by Steo_Walsh on 2010-05-12
this stopped the message asking me whether to kill the process or not but still when i close the terminal my theme that i had chosen in emerald just goes, any more ideas?

---

### Post by texpat on 2010-05-12
OK, so I found this article:[http://seogadget.co.uk/how-to-run-emerald-at-startup/]("http://seogadget.co.uk/how-to-run-emerald-at-startup/"). See if it helps.

---

### Post by texpat on 2010-05-12
Another thing I found was [here]("http://http://ubuntuforums.org/showthread.php?t=789956")

Go to System-Startup Applications

Click the 'ADD' button and in 'command' write 'emerald --replace'

This should run emerald at startup.

---

### Post by Steo_Walsh on 2010-05-12
not quite sure how i did but i think i got it working, thanks for your help, greatly appreciated :)

---

### Post by texpat on 2010-05-12
My pleasure :)

Please mark the thread SOLVED, then.

---

