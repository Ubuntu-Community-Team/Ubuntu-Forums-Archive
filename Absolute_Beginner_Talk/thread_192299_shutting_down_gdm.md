---
title: "shutting down gdm"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by mfleming on 2006-06-08
I'm not an absolute beginner but it seems like this should be a simple question (despite the fact that I don't know the answer). I have a computer that will mostly be used in character mode, ie without X. However, occasionally I want to be able to start up gdm to do something. I have configured the computer to boot into character mode, and can start up gdm simply by typing "gdm" as root. However, I don't know how to stop gdm to return to character mode. I can make this happen with CTRL-ALT-BACKSPACE, but it seems like there should be something more elegant. There is apparently supposed to be a gdm-stop command, but it does not exist on my system.

Thanks in advance,

Matthew Fleming

---

### Post by echo $USER on 2006-06-08
try ctrl-alt-F1 to enter text mode
ctrl-alt-F7 to bring up the GUI

---

### Post by muep on 2006-06-08
To start GDM:

sudo /etc/init.d/gdm start

To stop GDM:

sudo /etc/init.d/gdm stop

To restart GDM (x reconfigure or something):

sudo /etc/init.d/gdm restart

---

### Post by christhemonkey on 2006-06-08
At a terminal type:
```
sudo /etc/init.d/gdm stop
```
To stop it.
Replace stop with a start to start it up again.

---

### Post by linear on 2006-06-08
[quote=christhemonkey]At a terminal type:
```
sudo /etc/init.d/gdm stop
``` To stop it.
Replace stop with a start to start it up again.[/quote]
For at least some, this doesn't work in Dapper. See [this thread]("http://www.ubuntuforums.org/showthread.php?t=189734").

---

