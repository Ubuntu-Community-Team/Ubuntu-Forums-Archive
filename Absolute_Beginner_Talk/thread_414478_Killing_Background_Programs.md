---
title: "Killing Background Programs"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by drs305 on 2007-04-19
SOLVED:  I am familiar with xkill and using the gui skull and crossbones to terminate a program. Lately I have had mplayer start in background and I don't know the command to kill it. What terminal command do I use and also how do I get mplayer to start with a gui interface? I think the programs are currently launching with the command 'mplayer'.

By the way, my upgrade from Edgy 6.10 to Feisty went flawlessly this afternoon. Not one problem!

Thanks Team Ubuntu!

---

### Post by ~SkyBlue~ on 2007-04-19
There is a unix command to show all running process, try this:

Assuming your username is 'joe'
```
$ ps -u joe
  PID TTY          TIME CMD
 4014 ?        00:00:00 x-session-manag
 4071 ?        00:00:00 ssh-agent
 4074 ?        00:00:00 dbus-launch
 4078 ?        00:00:00 dbus-daemon
 4094 ?        00:00:00 gconfd-2
 4122 ?        00:00:00 gnome-keyring-d
 4125 ?        00:00:01 gnome-settings-
 4266 ?        00:00:00 sh

```

It shows running process under user 'joe'. If for example you want to kill a process (say dbus-daemon), then just type its PID (process ID)

```
$ kill 4078
```

Hope this helps :KS

---

### Post by drs305 on 2007-04-19
thanks skyblue, that did it. 

still looking for a way to start mplayer with an interface. I'm using mplayer with mediaconnectivity firefox plugin.  when I open a link with mplayer (/usr/bin/mplayer) it produces the sound but no gui interface for me to change settings or stop the program.

---

### Post by dugas on 2007-04-19
gmplayer for mplayer gui, or use many of the kick a**( front ends for it (kaffeine for example). 
p.s = if you want to kill mplayer, then you can issue the command
```
killall mplayer
```
or for any program
```
killall programName
```

---

### Post by drs305 on 2007-04-19
Now all my questions are answered. Thank you.

---

