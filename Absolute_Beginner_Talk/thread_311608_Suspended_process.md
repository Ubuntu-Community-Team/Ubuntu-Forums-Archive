---
title: "Suspended process?"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by humphry on 2006-12-03
Hello,

This is really a noob question... 

I can run python, and I can suspend python by hitting ctl-Z, and by using ps I can see that python is in fact suspended.  How do I get back to a suspended process?  It should NOT be required to kill -9 it each time........

(I know I can close it with Ctl-D, but there are times that I want to simply suspend it and then get back to it)

---

### Post by steve.horsley on 2006-12-03
You can use the command **fg** to bring it back into the ForeGround, which is what I think you're asking for. Alternatively, you can use the command **bg** which places the task in the BackGround. In this case, the command keeps running and can print output to you, but you can continue to enter other shell commands or launch other processes.

For your intertest, if you launch a program from the command line with an ampersand '&' on the end of the line, the process is launched into the background. e.g. 
**python myprog.py &**
but it still gets killed if you exit the shell that you launched it from. If you also use nohup (No Hang-up) you can launch a process that will not be killed when the parent shell exits, and you have in effect launched a unix service, called a daemon, e.g.
**nohup python myserviceprog.py &**

Hope This Helps

---

### Post by keyboardashtray on 2007-10-07
Ahh Thank you! You just saved my game of Nethack! fg for the win! :) :) :)

---

### Post by keyboardashtray on 2007-10-07
...and then I got killed by a jaguar not a minute later.

---

