---
title: "how to restart - command help"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by SVDtiger on 2006-12-04
AI told me "well its time you learn command line then" and i have been putting it off. Ubuntu now says its time for me to learn atleast some use of terminal :)

i must have clicked suspend/hibernate i guess because when i boot system today it asks for my user and pass and not comming to the gui side of things like my magnified desktop i need badly

i remember my password and user of course and enough DOS to be dangerous. so can someone please give this blind swine the proper
directory to be in and the command to restart?  

much thanks as always for all you do and best regards, John

---

### Post by Otaconda on 2006-12-04
sudo shutdown -r now

sudo to run as root, shutdown in the command (which you should be able to run from anywhere), -r tells it to restart, now tell it to begin immediately :)

---

### Post by Tomosaur on 2006-12-04
To reboot your system immediately, type:
```

sudo shutdown -r now

```

shutdown is the command
-r is the paramater (restart)
'now' is when to do it. This can be altered for a specific time or just a matter of minutes or whatever. If you're running a server, the shutdown command will send a message to all clients, telling them what's going on etc. You can specify your own message. You may wish to try 'man shutdown' at the command line for more info.

(damn, beat me to it :P)

---

### Post by an.echte.trilingue on 2006-12-04
well, that depends on the version of ubuntu.

up until edgy, it was "sudo init 6" but they changed things and init does not exist any more (AFAIK).

Try "sudo reboot".

take care

-mat

---

### Post by pay on 2006-12-04
startx should start the x-server

---

### Post by SVDtiger on 2006-12-04
im up and running again thanks to the very best community on the net 
:mrgreen: its wonderful to have clever friends 

bright blessings and sincere thanks. john

---

### Post by bodhi.zazen on 2006-12-04
Restart what?

X:```
Ctrl-Alt-Backspace
sudo /etc/init.d/gdm restart
```

System:```
sudo shutdown -h now
sudo init 0 #Shutdown
sudo reboot
sudo init 6 #Reboot
```

---

