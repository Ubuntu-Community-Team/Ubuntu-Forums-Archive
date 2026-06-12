---
title: "[SOLVED] Minicom 2.3 on Ubuntu 7.10"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by aelric on 2008-04-10
I'm new to the whole Ubuntu experience, i've just installed ver 7.10 on a laptop with a serial connection and need to access a switch via a console cable to do some configs. 

I did some looking around and everyone says this app called minicom is the thing to use in lieu of windows hyperterminal. So i download the tar ball, but can't seem to get the freakin thing installed. 

when i follow the minicom readme instructions and try compiling it i get a error: C compiler cannot create executables.

can anyone help me or tell me if there is an alternative package/app i can use to get into my switch 

p.s. telnet and ssh are not an option as these have not been configured on the switch yet i need direct console access via a serial connection

:confused:

---

### Post by brian_p on 2008-04-10
> **aelric said:**
> I'm new to the whole Ubuntu experience, i've just installed ver 7.10 on a laptop with a serial connection and need to access a switch via a console cable to do some configs. 

I did some looking around and everyone says this app called minicom is the thing to use in lieu of windows hyperterminal. So i download the tar ball, but can't seem to get the freakin thing installed. 

when i follow the minicom readme instructions and try compiling it i get a error: C compiler cannot create executables.

can anyone help me or tell me if there is an alternative package/app i can use to get into my switch 

p.s. telnet and ssh are not an option as these have not been configured on the switch yet i need direct console access via a serial connection

:confused:

You do not need to compile minicom. It is available as a package in Ubuntu.

---

### Post by aelric on 2008-04-10
Hi Brian 

thaks actually just figured it out.. reason i was trying to compile was that i could get the package via package manager and the sudo  apt-get was returning a no such package error (seems in my ubuntu infancy i forgot to tell the package manager it is allowed to go out to the internet an search sources ... duhhhh!!!) 

anyways long story short.. minicom installed configured and working... thanks

no i just need to work out how mark this thread as SOLVED

---

