---
title: "not recognising ethernet card"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2006-10-23
Hello there 

Well of months of experimenting I found a combo I liked , So I decided to dual boot my desktop 

Ubuntu worked well it dual booted just fine , except it coulnt pick up ,my ethernet ( I assume thats what it is~)

The system is a AMD duron1100 mhz with 750 ram with a wirelees router,

from the phone jack into the ADSL modem into a router then lan cable to the desktop and this laptop ( XFCe /kde )

when I try to connect all I get ( in networking) is modem not configured 

and the the gateway /activate is grayed out ..

Its seems not to be recognising my card 

can anyone steer me in the right direction

kind regards Stephen

---

### Post by po0f on 2006-10-23
basilwatson,

Post the output of:
```
$ ifconfig | grep "inet addr"
$ lspci | grep Ethernet
```

---

### Post by basilwatson on 2006-10-24
Hello the result so far

 inet addr ; 127.0.0.1    mask 255.0.0.0

 0000:00:09.0 Ethernet controller: VIA Technologies, inc VT86c100a (Rhine) (rev 21)

hope that makes sense!!!:confused: 

Stephen  :confused:

---

### Post by po0f on 2006-10-24
basilwatson,

I do not recognize that ethernet controller (never owned a Via board).  Maybe try:
```
$ lsmod | grep via-rhine
```

This command lists all the modules currently loaded by the kernel and checks to see if the via-rhine (which I think is the driver for your NIC) modules is loaded.

---

### Post by basilwatson on 2006-10-24
thanks will try that after work ..just rushing out the door ,,Late as usual!

Ill post back this evening with a progress report !! 


Stephen

---

