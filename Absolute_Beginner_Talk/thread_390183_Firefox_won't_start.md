---
title: "Firefox won't start"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by andycyca on 2007-03-21
Hi everyone!

This morning I was checking mi mail as usual and shut down the computer 'cause I had school. I came back half an hour ago and I can't start Firefox now (I'm using Galeon). Whenever I try to start it a message window pops saying:

Firefox is already running but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

Of course, I don't know how to stop processes in Xubuntu, so I restarted the whole sys. But it keeps appearing and now I can't use FF!!! Help anyone?

---

### Post by doobit on 2007-03-21
> **andycyca said:**
> Hi everyone!

This morning I was checking mi mail as usual and shut down the computer 'cause I had school. I came back half an hour ago and I can't start Firefox now (I'm using Galeon). Whenever I try to start it a message window pops saying:

Firefox is already running but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

Of course, I don't know how to stop processes in Xubuntu, so I restarted the whole sys. But it keeps appearing and now I can't use FF!!! Help anyone?

you can stop a process a couple of different ways. One way is to open a terminal and type ```
top
```
That shows a list of running processes. type q to stop top. There is a number by each process that you can use to kill the process. Type```
 sudo kill <the number>
```
Another way is just to type ```
sudo killall firefox
```
Probably you don't need to kill it though. Try opening a terminal and type firefox. It may open but give an error in the terminal that can give you a better idea of what's going on.

---

### Post by arochester on 2007-03-21
Try > killall -9 firefox-bin

---

### Post by raul_ on 2007-03-21
Another way to find the process is 

```


ps aux | grep <string to find>


```

in your case

```

ps aux | grep firefox

```

and then

```
 kill -9 <PID> 
```

---

### Post by andycyca on 2007-03-21
Yay! can you see the red/blue icon there?

**Thanks** doobit... bas thing is that I couldn't find firefox there. 
**Thanks** arochester! It worked!!!
**Thanks** raul_  even tough I didn't even try your method.

[img]http://img221.imageshack.us/img221/2259/biggrinzy0.gif[/img] see why I love Ubuntu?

---

