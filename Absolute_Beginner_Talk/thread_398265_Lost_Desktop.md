---
title: "Lost Desktop"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by pimmy on 2007-03-31
I'm a complete newbie so please bear with me. I was having sound quality issues after installing Real Player 10 and in the process of trying to solve these, using instructions from a thread somewhere (I've forgotten where) I lost my Desktop. When I log on to Ubuntu 6.06 now I get straight to the Terminal which asks me to log in and then waits for me to enter a command. What command do I enter to get my Desktop back?

---

### Post by taurus on 2007-03-31
Try

```
startx
```
and post the error message if there is one.

---

### Post by r4ik on 2007-03-31
try,

[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

Good luck !

---

### Post by pimmy on 2007-03-31
Taurus. I tried the "startx" command and I my computer screen looked like wire mesh with vertical stripes and just locked up.

---

### Post by Majorix on 2007-03-31
Try configuring X first:

```
sudo dpkg-reconfigure xserver-xorg
```

You have to type in the correct values for refresh rates for the monitor, that is important. You can find them in the product description of your monitor.

Good luck!

---

### Post by johnny4north on 2007-03-31
ubuntu 6.06 .. pimmy we need more info.. sys info; cpu,videocard and mem.  try startx, when error happens write down and post here to read. if you cant read it, then depress Esc key once. wait afew seconds, then depress the Enter key. read it. post the error here..got 2 go check on u later.  thanks Ubuntu
OOp, i think the majorix is correct...:)

---

