---
title: "Installing wireless usb adapter: make command not found"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by newmster on 2006-08-24
Alright, I'm trying to install my D-link usb wireless adapter, the DWL-G122, and I am following this guide:
[here]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29")

I get to changing directories to ~/Module, but when I type in 'make' it says bash: make: command not found

Any help?

---

### Post by newmster on 2006-08-24
Now I get this message:
```
~/rt2570-cvs-2006082411/Module$ make
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

```

---

### Post by newmster on 2006-08-24
bump

---

### Post by christhemonkey on 2006-08-24
You need to have build-essential installed to compile anything from source.

```
sudo apt-get install build-essential 
```

---

### Post by newmster on 2006-08-24
thanks, but I still see the same error.

---

### Post by christhemonkey on 2006-08-24
Ok, you need your kernel headers as well;
```
sudo apt-get install linux-headers-'uname -r' 
```

---

### Post by newmster on 2006-08-24
what is 'uname-r'?

---

### Post by docshawnc on 2006-08-24
I'm working on a similar problem - different device.  Try this

sudo apt-get install linux-headers-2.6.15-26-386

assuming that your kernel is the 2.6.15-26.386 version.  The command 

uname -r tells you which one you're using

---

### Post by newmster on 2006-08-25
Thanks everyone.  It still doesn't work though.  I don't know, maybe I have the wrong driver, this is what it says:
```
dan@StevesComputer:/$ sudo ifup rausb0
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device rausb0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device rausb0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
rausb0: ERROR while getting interface flags: No such device
rausb0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up rausb0.
dan@StevesComputer:/$

```

again, i'm following this [howto]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29").  Maybe I edited the interface file wrong, I just add "iface rausb0 inet dhcp..." to the bottom right?

---

### Post by newmster on 2006-08-25
I also tried ndiswrapper, couldn't get that to work either.  I can install the windows driver, but it says hardware is not connected.

---

### Post by newmster on 2006-08-25
.

---

### Post by newmster on 2006-08-25
Alright, finally got the D Link DWL-G122 Rev. D to work.  I followed [this]("http://www.ubuntuforums.org/showthread.php?t=81461") guide.  After doing the steps in that guide, I had to restart, and then I used Wireless Assistant (i think i got that through Automatix), but of course had to use the command 'sudo wlassistant' to give the correct permission.  After this, I had to make it the default gateway in System->Administration->Networking, and then finally disable the regular network card inside the computer.  Now on to making the printer on the network working.

---

### Post by newmster on 2006-08-26
Alright, I have it all working, but when Ubuntu is booting up, when it says 'network interfaces', it hangs on that for at least 2 minutes, then finally says ok.  Anyone know what might be causing the delay?
Also, I'd like to have wlassistant (wireless assistant) start up when I log in, but it needs the 'sudo' command.  How do I go about doing that?

---

### Post by newmster on 2006-08-26
pretty please?

---

