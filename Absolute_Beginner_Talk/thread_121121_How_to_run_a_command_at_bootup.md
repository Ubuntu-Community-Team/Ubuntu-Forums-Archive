---
title: "How to run a command at bootup?"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by madu on 2006-01-24
Hello guys..

There was a similar post in this but the answer was not given exactly..
Can somebody tell me how to run a command(program) at start up..?

i want to run "gkrellm" at start up..?
I put gkrllem at the end of the /etc/init.d/bootmisc.sh file, but it didnt work..
Can somebody tell me how to do this?

Thanks a lot guys...!

---

### Post by dpm on 2006-01-24
I don't know what you mean exactly by "at startup", but if you want to start a program every time the GNOME session starts, go to System>Preferences>Sessions.

There you can choose the "Startup programs" tab and specify which programs to execute when your session starts and in which order (from 0 to 200, I think).

For example, in your case you could specify gkrellm as the command to execute and leave the order as the default 50 (a program with order 0 will be executed first than one with order 1, and so on).

Cheers.

---

### Post by Titus A Duxass on 2006-01-24
From the Command Line enter - sudo update-rc.d bootmisc.sh defaults.

This puts the mandatory links in the various rc files.

It should give a report of various rc levels.

Hope it helps, I was the original poster.

Titus.

---

### Post by Delkster on 2006-01-24
[QUOTE=madu]i want to run "gkrellm" at start up..?
I put gkrllem at the end of the /etc/init.d/bootmisc.sh file, but it didnt work..
Can somebody tell me how to do this?[/QUOTE]

That would cause the command to be executed at the very startup of the system, before login and even before the graphical subsystem starts. Gkrellm is a graphical application so that wouldn't work.

Generally you only want to put background services and other such non-interactive things in the initialization scripts in /etc/init.d. Applications, such as gkrellm, should probably be launched when Gnome (or whichever desktop environment you use) is started, just like desp instructed.

---

### Post by madu on 2006-01-24
Thanks guys..
I used the session manager and it worked..
Thanks for the help..!

---

