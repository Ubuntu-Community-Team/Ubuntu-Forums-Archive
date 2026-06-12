---
title: "[SOLVED] network manager refresh?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by myddewji13 on 2008-02-12
Hi,

I have to restart my computer everytime i go from work to school/library/home in order to view networks available....i was wondering if:
a)If theres any way to make network manager 'refresh'? (commands?)
b)if there isnt what other alternatives do i have?
c)in case of b...what do you recommend and if i screw up/dont like it how do i go back to my original config..

thanks for your help....i noe its a pretty simple q and there are posts in the forums abt it...

---

### Post by Ferri on 2008-02-12
You can tell the network manager to disconnect the network and then connect again. Also, from the command line:
```
sudo ifdown eth0
sudo ifup eth0
```
will have the same effect, provided your network interface is eth0 (change it as appropiate). If you are in a DHCP network it will refresh your IP and the other settings.

---

### Post by stchman on 2008-02-12
> **myddewji13 said:**
> Hi,

I have to restart my computer everytime i go from work to school/library/home in order to view networks available....i was wondering if:
a)If theres any way to make network manager 'refresh'? (commands?)
b)if there isnt what other alternatives do i have?
c)in case of b...what do you recommend and if i screw up/dont like it how do i go back to my original config..

thanks for your help....i noe its a pretty simple q and there are posts in the forums abt it...

Try this:

```
sudo /etc/init.d/networking restart
```

---

### Post by myddewji13 on 2008-02-12
none of the above solutions worked!!!! help!! i ususally put my comp into suspend or hibernate but whenever i go sumwhere i gotta restart....which sorta defeats the purpose of suspend/hibernate....so please help!!!

---

### Post by myddewji13 on 2008-02-13
ok for so i finally figured it out:...this line in terminal works:


```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

YAY!!!! no more computer  restart from hibernate/sleep!!!

---

