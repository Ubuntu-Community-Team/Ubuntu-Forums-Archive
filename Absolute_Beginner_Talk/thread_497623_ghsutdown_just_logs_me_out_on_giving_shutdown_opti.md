---
title: "ghsutdown just logs me out on giving shutdown option..... please help"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2007-07-10
hello guys

i have ubuntu feisty. i want to use gshutdown to shutdown my computer at defined time in night. but gshutdown only logs me out instead of shutting down.

i read in another thread its the problem because with ubuntu feisty, there is something different used during boot up than previous version, this is why gshutdown is not able to shutdown.

is there any way around this....

i don't wish to use terminal method of shutting down at defined times. (feels uncomfortable)..

may be any other software than gshutdown (and kshutdown since it will require me to install kde libs which i don't want).... 

please help as i really need it. ( leave torrents on download in night.)

---

### Post by AlexenderReez on 2007-07-10
my ghsutdown give me that error too....hm....but i used to set gnome power manager to replace its tasks....

---

### Post by cyneuron on 2007-07-10
will be good if you could explain a bit further.....

---

### Post by AlexenderReez on 2007-07-10
hm....i'm using alpha version..so i don't really care about problem with software...sometimes dependency give error so if i got any problem with particular software , i just ignore it...and use alternative way...that is how my system...but in this case , we can see that gshutdown give error not because of dependency but its system itself...so open gshutdown ---> preferences ----> then set auto command---> use command that can shutdown using terminal as well as others....good luck

for shutdown
> sudo shutdown -h

for restart

> sudo shutdown -r

or 

> sudo reboot

---

### Post by yoramdavid on 2007-11-07
I am having the same problem in ubuntu7.10, cannot shutdown, it just logs me off.
Any help?

---

### Post by gtr225 on 2008-03-12
Run it as root by either typing ```
sudo gshutdown
``` in the terminal or pressing alt+F2 and running ```
gksu gshutdown
```under preferences, use custom commands and change the "Turn of computer" command to poweroff and the "Restart computer" command to reboot. Now it should work fine. To make a quick shortcut to run it as root just add a shortcut to the panel for gshutdown, right click it and in properties change the command from /usr/bin/gshutdown to gksu gshutdown.

---

