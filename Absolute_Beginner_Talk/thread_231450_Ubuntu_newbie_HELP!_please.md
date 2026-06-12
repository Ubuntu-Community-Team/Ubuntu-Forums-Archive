---
title: "Ubuntu newbie HELP! please"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by scoobydoo518 on 2006-08-07
I have installed 6.06 AMD64 version from live CD but:

What is the password for root? Can't install anything. I read root account is disabled and use "sudo passwd root" but when I try to put in a new password it replies "try again".

Where is Natuilus? or a file manager?

How do I add mp3,mpeg,avi support? I saw a posting and "saved" it to the live CD. Forgot it was only in memory.  :(


So far I'm very impressed

Thanks

---

### Post by Bunto0 on 2006-08-07
Hey ScoobyDoo, welcome to Ubuntu. I'm a newbie too and I actually installed my first plugin last night (woohoo, right?). You don't need a root password. I'm not sure if what I'm saying is the absolute most correct answer but I hope I am pointing you in the right direction. OThers can chime in too, since I'm probably doing it a harder way, but!

When you want to install something from the command-line, all you need to do is type sudo before your command.

so like if you want to copy something from your desktop to the system portion, all you need to do is: "sudo cp <location of file you want to copy> <location of file you want placed>." That's just for copying. So you just type sudo before any command that needs root priveledges and that would be in the command-line. I have also read something about something called Synaptic PRogram Manager that lets you install programs without you having to look for all the dependencies, etc. but I really don't know what how Synaptic works or what all the other stuff means. 

As for the mpeg, avi support, you need to install the proprietary software for it, kinda like my plugin install for firefox. I installed the JAva Runtime Environment last night so I could play some Yahoo! games.

---

### Post by scoobydoo518 on 2006-08-07
Actually trying to use add/remove applications. It wants a password. 

Thanks

---

### Post by Kobalt on 2006-08-07
Bunto0 explained well the sudo thing. 
You were asked for a root password during your installation : that's the one Add/Remove is asking you, the one you need to launch Synaptic (the package manager).
You can browse files with nautilus directly from the shortcut section, or you can press Alt+F2 and type nautilus if you want to use the wierd way... 
And if you want to install codecs, softwares and other stuff, check this adress out : [https://help.ubuntu.com/]("https://help.ubuntu.com/").

Cheers ! :rolleyes:

---

### Post by pdub on 2006-08-07
Check out this excellent how-to for Dapper.

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Follow these instructions and you will have a very functional Ubuntu system.

You may want to avoid the **Automatix** section, it messed up my system.

---

### Post by Bunto0 on 2006-08-07
ah i c. Well if that is the case, it depends on what you did when you were installing ubuntu. If you only have one user, the password would be the password you use to login into your account. ubuntu doesn't have root, it has super-users. try using the same password that you use when you login...

---

### Post by scoobydoo518 on 2006-08-07
It works! Thank you. :p

---

