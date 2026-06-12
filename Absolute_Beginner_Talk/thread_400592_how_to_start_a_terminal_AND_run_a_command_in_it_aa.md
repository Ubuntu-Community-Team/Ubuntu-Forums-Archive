---
title: "how to start a terminal AND run a command in it?? aaargh  oh nd probs with amarok"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by CC_machine on 2007-04-03
ok so i've been experimenting with Linux, especially the Xubuntu 7.04 beta, lovin' it so far :D

a small thing: what command can i run to start a terminal AND run a command in it? i want to bind this to a key in beryl so i can do "xmmsctrl title" which wil tell me what song is playing in xmms(media player.) this working fine in a terminal which i have already open...

i know the command to start an xfce terminal is xfterm4... but binding xfterm4 xmmsctrl title to a key in beryl just starts a terminal and does nothing :(

btw: i've tried the manpage on xfterm4, nothing about how to do this.

Thx in advance, CC


--------

about amaroK: It always freezes when generating my library and when the "install mp3 codec?" popup dialog pops up: i can do nothing! xmms is fine for me really, but i want to fix this :(

---

### Post by bruenig on 2007-04-03
There is a way to do it, but doing so will only run that one command, and then the terminal will be useless. I am on 6.10, but for that it would be
```
xfce4-terminal -H -e "xmmsctrl title"
```
Not sure if xfterm4 is the exact same thing, but would probably be similar.

---

### Post by CC_machine on 2007-04-04
xfce-terminal -H -e "xmmsctrl title"
looked at some manpages and found that this should work:
xfce4-terminal -H -e "xmmsctrl title"

you were right about the terminal being unusable, but the command still doesnt happen :(

---

### Post by bruenig on 2007-04-04
Yeah I meant xfce4, try other commands like do it with the "ls /home" command or something and see if that works. If it does, then perhaps you should analyze that command you are trying.

---

