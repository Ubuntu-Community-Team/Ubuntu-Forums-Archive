---
title: "Killing Unwanted Users"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by HeyGabe on 2007-12-26
This is probably not a beginner question, but I really want to know and I figured one of the helpful folks around these parts could, well, help. 

How Do I rid myself of unwanted logins?

```
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
name              127.0.0.1:1      13:28    4days  3:02m  0.35s x-session-manag
name     tty9     :0               17:39    0.00s  1:10m  0.31s x-session-manag
name     pts/0    :0.0             17:48    3:22m  0.17s  0.17s bash
name     pts/1    :0.0             17:53    0.00s  0.14s  0.01s w
```

Where "name" is my login, by the way.
I understand that tty9 is the login to the computer of which I'm currently using as I sit in front of the machine. .
And I understand  that pts/1 is the Gnome Termanal and pts/0 is probably the Tilda window sitting around in the background that I forgot that I had up when I went and opened the gnome terminal.
I also understand that the one from 127.0.0.1:1 is the login from my VNC over SSH tunnel from work earlier today.

But now that I'm home, how do I kill that logon?

---

### Post by blueridgedog on 2007-12-26
I would do a ps aux, find the process ID and then issue a kill -9 XXXXX where XXXXX is the process ID.

You could make it easier by greping for what you want:

ps aux | grep pts/1

---

### Post by thenailedone on 2007-12-26
...The easiest way to kill users is to hire someone to do it... a professional would be best as their will be less chance of you getting implicated... I would suggest however first discussing your issues with the users before taking drastic measures...

Sorry for this OT... but when I saw the title that was the first thing that popped into my mind...

---

### Post by Casual Fan on 2007-12-26
> **thenailedone said:**
> ...The easiest way to kill users is to hire someone to do it... a professional would be best as their will be less chance of you getting implicated... I would suggest however first discussing your issues with the users before taking drastic measures...

Sorry for this OT... but when I saw the title that was the first thing that popped into my mind...

:lolflag: Right there with you. I know a few unwanted users I'd like to kill...:twisted:

---

### Post by HeyGabe on 2007-12-30
> **blueridgedog said:**
> I would do a ps aux, find the process ID and then issue a kill -9 XXXXX where XXXXX is the process ID.

You could make it easier by greping for what you want:

ps aux | grep pts/1


Yeah. But I want to kill the user that I don't know what process he's on.

---

### Post by bindatype on 2007-12-30
Use the command
```

last

```
You can cross-reference the info you get with the output of
```

ps aux

```

I recommend you use 
```

ps faux

```
because it will show you what processes that user has spawned.

---

