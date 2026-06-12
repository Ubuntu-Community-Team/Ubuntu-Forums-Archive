---
title: "Tty???"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by belikralj on 2007-03-21
How can I run something from tty1 in tty7? I know that the ps command has the option -t and that the kill command can also kill processes from other tty's (I forgot how though). Can someone tell me the options or commands for running commands in other tty's? For example how could I from shell 1 (tty1) run firefox in X (tty7)?

---

### Post by v8YKxgHe on 2007-03-21
I can't help with you're problem, though I'm wondering what the benefit of doing that would be? I would have thought it would be easier to just launch them from tty7?

Also, what does TTY stand for? I've never known what it means!

---

### Post by belikralj on 2007-03-21
I don't know either, could be text terminal.... or anything really. But the point is I'm trying to halp someone who can't really start things from X that easily but once started can use them. I'm not sure if it will help but I thought it might, here's the thread rather than me trying to retell the situation [http://ubuntuforums.org/showthread.php?t=390061](http://ubuntuforums.org/showthread.php?t=390061)

---

### Post by mcduck on 2007-03-21
> **AlexC_ said:**
> 
Also, what does TTY stand for? I've never known what it means!
It's short for teletypewriter.

---

### Post by jordanmthomas on 2007-03-21
[COLOR="Silver"]This would maybe work:
```
[COLOR="Silver"]export DISPLAY=127.0.0.1:0
xterm -e /usr/bin/firefox[/COLOR]
```
It should start a terminal on your first X server and run firefox from the xterm.
It's not great for normal usage but it may help you get your troubles sorted.[/COLOR]

Scratch that, this is all you need to do:
```
export DISPLAY=127.0.0.1:0
firefox & #the & is for in case you want to still use the tty

```

---

### Post by belikralj on 2007-03-22
it said it couldn't start the display. I'll have a better look at that command you gave me in a minute, but thanx it seems it might work :)

---

### Post by jordanmthomas on 2007-03-22
Let me make sure I understand the problem first.
The person you are helping has X running, but cannot start programs?

Or is X not running?

---

### Post by mcduck on 2007-03-22
I just realized that you are trying to start firefox in a tty. You can't do that, it's a graphical program and needs X to run.

---

### Post by belikralj on 2007-04-01
> **jordanmthomas said:**
> Let me make sure I understand the problem first.
The person you are helping has X running, but cannot start programs?

Or is X not running?

[http://www.ubuntuforums.org/showthread.php?t=390061](http://www.ubuntuforums.org/showthread.php?t=390061)
heres the thread

---

