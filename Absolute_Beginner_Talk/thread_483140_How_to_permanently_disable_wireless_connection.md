---
title: "How to permanently disable wireless connection?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by tico on 2007-06-24
I'd like to disable my wireless card permanently, since I can see my neighbors' wireless network everytime I start Ubuntu. How could I disable the wireless network card?

Thanks.

---

### Post by mattg89 on 2007-06-24
which interface is your card using? e.g. eth1, wlan0 etc.

If you're not sure type

iwconfig

in console and post the results.

---

### Post by tico on 2007-06-24
Here's the result:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID : off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power : off   
          Retry limit:7   RTS thr : off   Fragment thr : off
          Power Management : off
          Link Quality : 0  Signal level : 0  Noise level : 0
          Rx invalid nwid : 0  Rx invalid crypt :0   Rx invalid frag : 0
          Tx excessive retries : 0  Invalid misc : 0   Missed beacon:0

---

### Post by jimbob on 2007-06-24
Curious, why does it bother you that you can see your neighbor's AP as long as you don't try to connect to it or he can't connect to yours?  That's the way wireless is supposed to work. As long as yours is secure and locked down you are fully protected.

If you really want to you could take the cover off and remove your network card - that is a foolproof method.  If it is a laptop, most have switches that allow you to shut off the antenna which would accomplish the same thing.

Also you could enter *[COLOR="Blue"]sudo ifdown eth1[/COLOR]*
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Bachstelze on 2007-06-24
Just blacklist the ipw2100 module. It won't be loaded at startup, thus the system won't "see" any wireless interface and you'll be happy :)

---

### Post by tico on 2007-06-24
> **HymnToLife said:**
> Just blacklist the ipw2100 module. It won't be loaded at startup, thus the system won't "see" any wireless interface and you'll be happy :)

Ok. And how can I blacklist it? I'm a Linux newbie.

---

### Post by Funk Phenomena on 2007-06-24
I chose "Manually configure" whatever when I selected the wireless options.  That disabled the wireless since I didn't manually configure anything.

Otherwise, yeah, just pull the card.

---

### Post by tico on 2007-06-24
> **Funk Phenomena said:**
> Otherwise, yeah, just pull the card.

Can't do this: it's a laptop…

---

### Post by kevdog on 2007-06-24
Edit the following

gksu gedit /etc/modprobe.d/blacklist

Add the following line:
blacklist ipw2100

Save file.

Reboot.

---

### Post by tico on 2007-06-25
> **kevdog said:**
> Edit the following

gksu gedit /etc/modprobe.d/blacklist

Add the following line:
blacklist ipw2100

Save file.

Reboot.

It worked. Thanks.

---

### Post by ghandi69_ on 2007-06-25
Just be thankful that your wireless works!

---

### Post by jimbob on 2007-06-25
> Just be thankful that your wireless works!

+1

How true.  Usually around these forums it is quite the opposite ..
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

