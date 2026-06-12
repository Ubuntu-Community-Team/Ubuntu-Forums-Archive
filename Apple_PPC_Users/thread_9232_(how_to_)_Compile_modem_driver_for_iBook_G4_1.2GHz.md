---
title: "(how to ?) Compile modem driver for iBook G4 1.2GHz"
date: 2004-12-26
forum: Apple PPC Users
---

### Post by Laf on 2004-12-26
Hi all...

My Ubuntu installation has 24 hours and WOW, for a Linux my laptop is very well supported (including power management etc.).

Now i got two problems left :
[list]
[*]Getting the modem to work (very important :o) )
[*]Make "suspend" work (sleep ?) 
[/list]

Here is what i get if i search in the *dmesg* :

```
serial8250_init: nothing to do on PowerMac
pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
ttyS0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Serial port
ttyS1 at MMIO 0x80013000 (irq = 23) is a **Z85c30 ESCC** - Serial port
```

We see the name of the modem. But one strange thing : there is no mention about "modem".



I tried all which is writen in [an other thread](http://ubuntuforums.org/showthread.php?t=8349) but the problem is not resolved. In fact the modem say nothing.

Here is the output of **wvdial** :

```
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding
```

I also tried the configfile given in the thread mentionned highier and the problems are the same :o(.

Does anyone has an idea about what's wrong and/or where to find informations ?

---

### Post by trash on 2004-12-26
I did end up using pppconfig because it works well with the modem monitor. If you give that a try(assuming you are on dialup) enter your info and use 'CHAP' for authentication method and leave 'provider' as is. If it doesn't detect your modem edit the modem line to read '/dev/ttyS0'

---

### Post by Laf on 2004-12-26
Running **pppconfig** is the first thing i tried. As it wasn't ok i tried wvdial.

But i tried again (who know ?!).

Here is what **pon** does (when writing **ps f**) :

```
 5218 ttyS0    Ss+    0:00 /usr/sbin/pppd call provider
 5219 ttyS0    S+     0:00  \_ /usr/sbin/chat -v -f /etc/chatscripts/provider
```

Nothing happens, it's as if all would be waiting... for something that doesn't come...

As there is no output i tried the command line by hand :
```
 chat  -v -f /etc/chatscripts/provider
```

It shows me a **ATZ**... that's all. It stoppes after maybe one minute (timeout i think).

I think that the modem doesn't say "OK".

---

### Post by trash on 2004-12-26
just checked the properties of /dev/ttyS0...

check that the user/group is correct

group - dialout
and permission is 660

thats about all i can suggest

---

### Post by Laf on 2004-12-26
[QUOTE=trash]just checked the properties of /dev/ttyS0...

check that the user/group is correct

group - dialout
and permission is 660

thats about all i can suggest[/QUOTE]
 Hum...

```
$ ls -l /dev/ttyS*
crw-rw----    1 root     dialout    4,  64 2004-12-26 17:16 /dev/ttyS0
crw-rw----    1 root     dialout    4,  65 2004-12-26 17:16 /dev/ttyS1
```

:o(

---

### Post by michael_salcher on 2005-01-04
is anyone out there using their modem in their ibook? as far as i know, the only driver available is from [http://www.linuxant.com/](http://www.linuxant.com/) but costs US $ 15, or you can get a driver limited to 14.4 Kbits for free.

---

### Post by Laf on 2005-01-04
Look at old posts... some people are successfully using PowerMac Zilog driver...

It's like "Airport Extreme", some old "airport extreme" were working... but new ones doesn't work on Linux... it has the same name... but it is different !

---

### Post by tiiim on 2005-01-05
modems are closed source and you prob wont be one of the lucky ones to have the odd one that works.

airport extreme is off the cards.

as for sleep etc you have to download a new kernel with it enable this [link](http://ubuntuforums.org/showthread.php?t=5760)  will help you out...

---

### Post by chascon on 2005-01-06
[QUOTE=][/QUOTE]
 "Look at old posts... some people are successfully using PowerMac Zilog driver...
It's like "Airport Extreme", some old "airport extreme" were working... but new ones doesn't work on Linux... it has the same name... but it is different !"


You must be confusing "airport" with "airport extreme".  Airport did work with linux drivers but airport extreme (made by broadcom) does not.  If not I'd like to be proven wrong.

---

### Post by kris kincaid on 2005-01-25
laf,

I had the same problem with wvdial, but this line is the key:

"--> Warning: section [Dialer Defaults] does not exist in wvdial.conf"

Change the line in /etc/wvdial.conf that says "[Dialer PPOE]" (not sure on the PPOE part) to "[Dialer Defaults]"

Worked for me on an old G3 Lombard. 

Now if I could find a frontend to wvdial so my wife won't be afraid of it, I'll be a happy man!  :)

---

### Post by Ptero-4 on 2006-10-29
The problem here is that pmac_zilog isn't the modem, is the serial port (which is internal), in the G3 500MHz and earlier iBooks there was a brandless hardware modem attached to ttyS0, but now that port is empty and the modem is now a conexant softmodem.

---

