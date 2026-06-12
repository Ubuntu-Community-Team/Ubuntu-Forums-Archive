---
title: "WIFI Problems... HELP...!!! Please..."
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2007-02-05
Ok, here it goes...

I used to use ubuntu on my laptop (this system) and when i first started using it, it took me ages to get the wireless working.. :(

i finally did it by looking through about 6 different tutorials, and messing wih settings...

i have re-installed ubuntu from scratch and have come across the same proble, but this time, 7 tutorials and how-to's later, still no wireless, 

the last tutorial was a step by step guide to ndiswrapper, but after all of this, i cannot get wlan0 to show up on 'iwconfig'

all i see is 'lo' 'eth0' and 'sit0'

i did also see 'eth1' untill i comented it out of one of the files (cant even remember which one i edited thatmany)

ohh, and also... ME = Ubuntu n00b.. (so go easy :) )

Pleas help me guys.... (and gals)

S2k

---

### Post by shoot2kill on 2007-02-05
Small Bump... :( Still Not Working...

---

### Post by BrendanM on 2007-02-05
You're going to have to give some more specific information before people can help you. What kind of computer is it? What kind of wireless card is it? Which tutorials did you try following? What did you do to make it work before?

---

### Post by shoot2kill on 2007-02-06
Computer - Compaq Presario R3000

Wireless Card - Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)

Tutorials Followed So Far - [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)
                                     - Another Bcmxx Tutorial (simmilar to above)
                                     - 3 or 4 Different NdisWrapper How-To's (dont know URL, Sorry)

Work Before - Followed Lots Of Tutorials, And after giving up onit and using Ethernet, i started to install other aps... unplugged the thernet and WIFI was working.. so havnt got a clue how i did it.. :D

---

### Post by shoot2kill on 2007-02-07
OK, i have just upgraded to Edgy, And still not working (i wasnt really expecting to beany change but someone said edgy is better for doin this stuff)

But, BUMP   :D:D:D

---

### Post by shoot2kill on 2007-02-07
anyone ???

---

### Post by darrenm on 2007-02-07
No experience with that exact one but if the bcm43xx module supports that card I would try the bcm43xx-fwcutter + module route rather than using ndiswrapper.

Also once you can actually see the wifi light on then I found connection-manager very useful. [http://www.ubuntuforums.org/showthread.php?t=299462&highlight=connection+manager](http://www.ubuntuforums.org/showthread.php?t=299462&highlight=connection+manager)

---

### Post by rtmie on 2007-02-07
I think on Ubuntu the wireless lan adapter will normally show up as eth1 (assuming you also have a wired ethernet nic), so I'd be nervous about your statement that that you commented eth1 out of somewhere.

You could start at basics like trying lspci -v in a terminal and searching your output to see if your wireless card shows and then try typing dmesg in and see if there is any indication that there was an attempt to load a driver, or type lsmod to see if you can see if a driver is loaded.

Rob

---

### Post by shoot2kill on 2007-02-08
lspci -v
```

02:02.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 12f3
        Flags: bus master, fast devsel, latency 64, IRQ 201
        Memory at d0204000 (32-bit, non-prefetchable) [size=8K]

```
Like i say, i am new to linux.. dunno if this is shwing good or bad. :(


dmesg
the only things i could find that are/may relate to the WIFI card are
```

[17179603.624000] bcm43xx driver
[.....]
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[17179604.872000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[.....]
[17179610.268000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179610.300000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179610.300000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179610.328000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179610.328000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179610.328000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179610.360000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179610.360000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179610.360000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179610.384000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179610.384000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179610.384000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179610.408000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179610.408000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179610.408000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed

```

of which all seem to be errors of some sort. anyone know what these mean ???

thx for help so far...

---

### Post by darrenm on 2007-02-08
I think if you are using ndsiwrapper you need to blacklist the bcm43xx open-source driver.

```
sudo gedit /etc/modprobe.d/blacklist
``` then put bcm43xx on the final line by itself and reboot.

---

### Post by shoot2kill on 2007-02-08
this is what i did when looking through thr NDISWRAPPER tutorials... but ndiswrapper didnt recognise my wireless device, so i took bcm off the blacklist cos it did recognise my device, but now it cant see any device

---

### Post by darrenm on 2007-02-08
Ah right, so blacklist ndiswrapper instead. Same process but put ndsiwrapper in there instead.

---

### Post by shoot2kill on 2007-02-09
Still No Joy.... I Really Need This Fixing...

---

### Post by darrenm on 2007-02-10
Have you done what I suggested above? What happens after you put blacklist ndiswrapper in /etc/modprobe.d/blacklist?

---

### Post by shoot2kill on 2007-02-10
nothing noticeble..

when i first tried it with bcmxx it kinda worked.. it could see the different netrworks, but could not connect, no matter wht i did (even disabling encryption)

so i decided to use ndiswrapper and no luck there either. so i added ndiswrapper to blacklist and nothing, ithe wireless just dont wanna work....

---

### Post by CongoJim on 2007-02-10
I had trouble with mine too. Tried this link [http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper)
and it didn't work UNTIL I cleaned up a synaptic problem. I had downloaded sun-jdk docs and an install program. Everytime that I ran Synaptic it would tell me the files were not where they needed to be and I'd have to tell synaptic to continue without the files. Not an option when running the auto installer from the link above. After I moved the files then ran the programs all was well. Any chance you have something like that and have you tried the link above?

---

