---
title: "How do i send the command window into the background once an app is launched.."
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-10-04
I set up a launch icon on my desktop, now when i click on it and it calls the program it is instructed to call, i want the console window to be automatically hiden.. Is there a special command like in the launch icons command i could say "programA -hide"

and it would call programA but hide the console?

---

### Post by john.nicholls on 2006-10-05
Instead of using the launch icon, you could press Alt-F2 to launch a Run menu. Then when you select and execute the command, the Run window will close.

John

---

### Post by james_san on 2006-10-05
Also when you are editing the launch icon, I believe there is an option called "run command in terminal". You want to untick this (Unlike windows, most linux programs have console output for debugging and stuff, so it can't automatically detect whether to show it in a console).

---

### Post by ashokpappu on 2006-10-05
some little tip from shell.  when u run command from shell like bash all u need to do is to put & at the end of command.  say for example if u want to run kcalc u just type at the shell kcalc&.  that will run the shell in the back ground.

---

