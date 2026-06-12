---
title: "run command form terminal[without tying it up]"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by ninocass on 2006-03-15
Is is possible to execute a command from the terminal witout tying it up?

for example if i run XMMS from the terminal xmms starts but the terminal is tied to that process until it ends.  is there anyway around this?

Thanks

Nino

---

### Post by oakz on 2006-03-15
add "&" to the end of the command to run it in the background.

$ xmms &

if you want the application keep running even after the terminal is closed, execute the program with nohup:

$ nohup xmms &

---

### Post by stuporglue on 2006-03-15
Also, if you've already tied up the temrinal with a command, ctrl+z will freeze the program, typing "bg" will then send it to the background. You can bring stuff back to the front again by running "fg", and view all backgrounded processes by running "jobs". If you have multiple backgrounded jobs, you can use "fg #" where # is the number of the job as listed when you run "jobs". 

I'm sure that's not very clear, but if you play with it a bit, it'll make sense.

---

### Post by 5-HT on 2006-03-15
[quote=oakz]if you want the application keep running even after the terminal is closed, execute the program with nohup:

$ nohup xmms &[/quote] 
Just to add something that can save a little typing in some instances (comes in handy if you're lazy like me :p)...

If you're running the command in the background from a non-login shell (i.e. terminal emulators in X or just a subshell), I don't think you need to call it with 'nohup' for it for it to remain running after you exit the shell.

---

