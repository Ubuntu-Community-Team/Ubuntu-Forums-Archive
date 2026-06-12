---
title: "Help on Some commands to mess with Ubuntu?"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by deadly_paddooo on 2006-01-03
Hi!

I dun't have to say my status, it's on the profile (newbie)!

I have been messing with Ubuntu, so I wanna know wat does these do

Ctrl-Alt-F8, brings me onto booting messages, How do I get out! I pressed Ctrl-Alt-Del (system rebooted)

Ctrl-Alt-Esc, i think it brings me into original shell, i typed exit and was back in GUI after some rebooting time. So in that mode how do I turn off PC, just switch it off?
Also how do we shutdown from terminal (command) i tried "logout" did not worked.

Next I tried ```
 sudo shutdown -aH 
``` and messed me up!

Also it would be great for links of keyboard shortcuts in Ubuntu!

---------------------------------
I use mice w/ my left hand

Thanks

---

### Post by Luke on 2006-01-03
to shutdown:

```
sudo shutdown -h now
```

---

### Post by deadly_paddooo on 2006-01-03
[QUOTE=Luke]to shutdown:

```
sudo shutdown -h now
```[/QUOTE]

Oh yeah forgot the now!, does nothing halts the machine down, back to root i think.

---

### Post by estel on 2006-01-03
Or "now" can be replaced by a number which represents the number of minutes until shutdown. Or the time. Or number of seconds.

Type *man shutdown*

---

### Post by estel on 2006-01-03
Ctrl+Alt+F8 changes you to the 8th "terminal".
Ctrl+Alt+F7 changes you back to the GUI.

---

### Post by MartinJ on 2006-01-03
I've used the 'sudo poweroff' command before.  What's the difference between that and shutdown?

---

### Post by carlosqueso on 2006-01-03
[QUOTE=deadly_paddooo]Ctrl-Alt-F8, brings me onto booting messages, How do I get out![/QUOTE]

Ctrl-Alt-F7 should bring you back into the graphical mode.

[QUOTE=deadly_paddooo]Ctrl-Alt-Esc, i think it brings me into original shell, i typed exit and was back in GUI after some rebooting time. So in that mode how do I turn off PC, just switch it off?
Also how do we shutdown from terminal (command) i tried "logout" did not worked.[/QUOTE]

You have a couple of choices in a shell:  ```
sudo init 0
``` should work (change the 0 to 6 for a reboot) or ```
sudo halt
``` and there are a couple more that I don't know.  


[QUOTE=deadly_paddooo]Also it would be great for links of keyboard shortcuts in Ubuntu![QUOTE]

[http://www.gnome.org/learn/intro/2.2/](http://www.gnome.org/learn/intro/2.2/) is a good place to start....I had found a list of keyboard shortcuts somewhere, but can't find it now....

EDIT: I type too slow....lol

---

### Post by carlosqueso on 2006-01-03
HA! found the hotkey reference! Here it is: [http://www.gnome.org/learn/users-guide/2.10/ch01s02.html#shortcuts-global](http://www.gnome.org/learn/users-guide/2.10/ch01s02.html#shortcuts-global)

---

### Post by Omnios on 2006-01-03
shutdown -r now =reboot

shutdown: invalid option -- -
Usage:    shutdown [-akrhHPfnc] [-t secs] time [warning message]
                  -a:      use /etc/shutdown.allow
                  -k:      don't really shutdown, only warn.
                  -r:      reboot after shutdown.
                  -h:      halt after shutdown.
                  -P:      halt action is to turn off power.
                  -H:      halt action is to just halt.
                  -f:      do a 'fast' reboot (skip fsck).
                  -F:      Force fsck on reboot.
                  -n:      do not go through "init" but go down real fast.
                  -c:      cancel a running shutdown.
                  -t secs: delay between warning and kill signal.
                  ** the "time" argument is mandatory! (try "now") **
[/CODE]

---

### Post by Suger on 2006-01-03
```
shutdown -r now
```
not
```
shutdown -r now=reboot
```

shutdwon -r now means reboot

---

