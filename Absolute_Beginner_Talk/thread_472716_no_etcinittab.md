---
title: "no /etc/inittab?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-13
I keep on reading about /etc/inittab, but there doesn't seem to be such a file on my system.

Is there something wrong with my install? It seems like a pretty important file from what I'm reading?

> 
The kernel, once it is loaded, finds init in sbin and executes it.

When init starts, it becomes the parent or grandparent of all of the processes that start up automatically on your Linux system. The first thing init does, is reading its initialization file, /etc/inittab. This instructs init to read an initial configuration script for the environment, which sets the path, starts swapping, checks the file systems, and so on. Basically, this step takes care of everything that your system needs to have done at system initialization: setting the clock, initializing serial ports and so forth.


> 
But there are other possibilities as well [...] Ultimately, your system documentation will explain the details about the higher level aspects of init.


> 
The discussion of run levels, scripts and configurations in this guide tries to be as general as possible. Lots of variations exist.


- where can I look for further info if it's Ubuntu not conforming to the guide I'm currently reading, which is [here]("http://tldp.org/LDP/intro-linux/html/sect_04_02.html")?

---

### Post by moore.bryan on 2007-06-13
*[this ]("http://ubuntuforums.org/showthread.php?t=292507")might help you...*

---

### Post by ecs_pf5 on 2007-06-13
it does, very much so. Thanks :p

---

### Post by moore.bryan on 2007-06-13
*no problem... just post if there's anything else.*

---

### Post by alanhoyle on 2007-06-28
I'm trying to install an automated remote backup program on my machine and one of the last steps in the instructions is to do the following:

> To install the client scheduler, add the following line to the /etc/inittab file: 
>         ad:2345:respawn:/usr/bin/backup-program >/dev/null 2>&1
>
> Then run the following command from the /etc directory: 
>       telinit q

In order to make this work, can I create the /etc/inittab so it ONLY contains that one "ad:2345:respawn:..." line, or will I basically have to recreate the entire Upstart configuration in there?  

Alternatively, can anyone tell me how to write an Upstart script to replace that line?

Thanks, alan

---

### Post by alanhoyle on 2007-06-29
I figured it out using one of the /etc/event.d/ttyX files as a model and running the start program.

---

