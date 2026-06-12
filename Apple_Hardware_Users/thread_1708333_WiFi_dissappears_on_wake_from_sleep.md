---
title: "WiFi dissappears on wake from sleep"
date: 2011-03-16
forum: Apple Hardware Users
---

### Post by wweeks on 2011-03-16
When I put my iBook G3/600 to sleep and wake it again it loses its WiFi connection and can't even detect WiFi Connections. I can still connect via the "Connect to Hidden Network" function but that is rather annoying. Restarting always makes it detect WiFi again. Any help would be very much appreciated.

---

### Post by linuxopjemac on 2011-03-16
you probably have an airport classic, right? If so zou might want to do the following:

Make a hook in /etc/pm/sleep.d and /etc/pm/power.d as root. In /etc/pm/sleep.d created 20_wireless with the following into it:

```
#!/bin/sh  
rmmod -f airport
rmmod -f orinico
```

chmod +x this file to make it executable

Do a similar thing in /etc/pm/power.d/10_wireless:
```

#!/bin/sh  
modprobe orinoco
modprobe airport
```

---

### Post by wweeks on 2011-03-16
Yes, classic.
 I tried the first set of command and it worked till I tried to remove "orinico". It says
```
Error: Removing 'orinico': No such file or directory 
```
I don't understand what you mean by chmod+x either?
 Also, it says that /etc/pm/power.d/10_wireless doesn't exist either. Any ideas?

---

### Post by linuxopjemac on 2011-03-16
typo
```
orinoco
```

---

### Post by rsavage on 2011-03-17
How have you got wifi working at all? What steps have you taken?

I'm not at my my ibook at the moment (because it currently needs some resoldering to bring it back to life) so i can't check this, but I think if you are using wpa encryption it should work with suspend.

---

### Post by wweeks on 2011-03-17
Yea it's working fine except it stops detecting Wifi after sleep. It can still connect though. 
I still haven't got a chance to run through the corrected steps linuxopjemac gave me. 
I believe the home network I'm on is WPA-2. Personal

---

### Post by wweeks on 2011-03-17
I'm sorry I still don't understand what you mean by chmod+x. I ran chmod --help and I still couldn't understand how to make it work. I'm kinda new to Linux, mind explaining it?

---

### Post by linuxopjemac on 2011-03-17
you created the file called /etc/pm/sleep.d created 20_wireless To make it executable do:
```
sudo chmod +x /etc/pm/sleep.d/20_wireless
```
You also have to do this to the other file.

---

### Post by wweeks on 2011-03-17
It works now. Thanks you guys!

---

### Post by BitSar on 2011-04-17
This due to a configuration flag being set to False in the .state file.

Here is the fix
```

sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

```

Your network connectivity will re-establish in about 60seconds - or restart if required. 

```

sudo shutdown -r +1

```
There +1 gives the kernel 1 minute to unload everything a stop it cleanly before a restart signal is given.

Hope this helps,
BitSar

---

