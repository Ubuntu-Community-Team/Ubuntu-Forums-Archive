---
title: "Process management -- viewing a process"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Monsieur le Comte on 2007-01-18
I'm not sure if I used the correct title, but heregoes:

I was ssh'd into my ubuntu box at home, running motion to monitor living area.  However, my connection dropped and I had to reconnect. 

Is there any way to pick back up the motion process and view it again like before my connection dropped?  Jobs and fg are of no help there.

I could always kill the motion process and restart it, but is there a cleaner way of picking it back up?

---

### Post by weresheep on 2007-01-18
Hello,

I've not used motion but it sounds like 'screen' is what you are looking for. screen is a program that allows you to detach the currently running program(s) from the shell (leaving them running) and then reattach at a later point.

See [this thread]("http://www.ubuntuforums.org/showthread.php?t=314229") for more details.

-weresheep

---

### Post by seuaniu on 2007-01-18
I don't know of a way that you can "reattach" to any random process, but there is hope :)

```


user@host$ man screen


```

Screen will save your butt every time.  Screen makes a "virtual" terminal that you can detach and reattach at will.  If your connection drops, just re-connect, and screen will be waiting for you to re-attach and continue working.  I use it every single time I log into a server.

---

### Post by Fundi on 2007-01-18
Yeah screen is what you would need. To install just type:

sudo apt-get install screen

Then to use run the command 'screen'. It will look just like the regular terminal. If your conection drops you then just type screen -ls and then screen -r of the session you want to reconnect too.

---

### Post by punx45 on 2007-01-18
yes, if you just ssh in and get disconnected, any running processes get killed. in some instances this is probably a good thing.

but for cases where you specifically want to SSH in, start something, log out with it still running, and come back to it at a later time, screen is exactly what you want.

today I am using screen to carry on a command line invoked torrent download remotely through SSH.   its also good for doing things that would break if you got disconnected accidentally (compiling, etc.)

---

