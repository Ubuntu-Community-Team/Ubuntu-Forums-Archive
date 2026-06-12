---
title: "ubuntu 60% slower than xp ?????"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by ac45 on 2006-10-05
:( 
Hi,
I've used Ubuntu for 2 months.
I've just discovered, my adsl connexion is very slow (+/- 350 Kb) and even fall down to 154 kb sometimes.
With the same PC and same modem, my adsl connexion has been totaly stable (around 650 Kb).
Why ?
And how could I check / change parameters ?

Modem used : speedtouch 330.

Thank's a lot for your help

---

### Post by FuzZy2006 on 2006-10-05
I'm using the same modem but the speed difference between ubuntu and xp is +10 kBps for ubuntu ;). It works a lil' better 4 me.

---

### Post by haxer on 2006-10-05
i get an normally 250kb/s ín xp with my broadband 2mbits and in ubuntu i get an 280 sometimes 300 or 350 :)

---

### Post by Pjotr123 on 2006-10-05
Is your ADSL modem hooked up to your PC by a USB cable or by a normal network cable? USB cable connections for internet modems, have been known to cause several problems.

Greeting, Pjotr.

---

### Post by Ueland on 2006-10-05
It`s quaranteed not Ubuntu`s fault, but it could be that you are using the wrong drivers or have the network card configured wrong. 

Just a little hint.

---

### Post by LookTJ on 2006-10-05
try this...

open terminal

```
gksudo gedit /etc/modprobe.d/aliases
```

then look for

```
alias net-pf-11 ipv6
```

then save it and reboot the computer

hope that helps

---

### Post by jaboua on 2006-10-05
And, just in case: you do know the difference between kBps and kbps?

---

### Post by LookTJ on 2006-10-05
> **jaboua said:**
> And, just in case: you do know the difference between kBps and kbps?

People are lazy...to correct their mistakes

KiloBytes/second = KB/s

Kilobits/second = Kb/s

---

### Post by JGuru on 2006-10-05
**If you want FireFox browser to zoom like a F1 car, You need to do these tweaks!!!**
 
 Type **about:config** in the URL field, press Enter key.
 To change numeric value, select it , right-click, 'Modify', Enter the new
  value in the dialog that appears. To change boolean values (true/false),
  You must select 'Toggle'.

  In the **Filter** textfield, type **network.dns** (Press Enter)
  Change **network.dns.disableIPv6 -> true** 
  Now type **network.http** in the 'Filter' field

  Change these values of the following items:

  **network.http.max-persistent-connections-per-proxy -> 8**
  **network.http.max-persistent-connections-per-server -> 8**
  **network.http.pipelining -> true**
  **network.http.pipelining.maxrequests -> 24**
  **network.http.proxy.pipelining -> true**
  **network.http.redirection-limit -> 8**
  **network.http.request.max-start-delay -> 0**

   Restart the FireFox browser for the changes to apply. And see the speed
  difference!!!!

---

### Post by LookTJ on 2006-10-05
sorry Jguru, my post disables ipv6 globally

---

### Post by xyz on 2006-10-05
You can try Switffox as well...Some people have reported lots of "swiftness!"

---

