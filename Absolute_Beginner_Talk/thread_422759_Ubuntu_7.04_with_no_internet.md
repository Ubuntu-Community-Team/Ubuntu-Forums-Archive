---
title: "Ubuntu 7.04 with no internet?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by zionykl on 2007-04-25
Dear Ubuntu experts,

I have installed my Ubuntu 7.04 Desktop Edition successfully and everything looks great except that I have problem connecting to my Wireless Router using my Compex WLU54G adapter. I provided my passphrase for the WEP and I can see that it said Network Connection to "Name of my Wireless connection" 87%, however, my Firefox cannot connect to any internet sites.

This adapter is working fine on my Vista which is now a dual boot machine.

I really would like to try out Ubuntu but if it is without internet connection, there's a lot of thing I cannot do with it.

Please help.

---

### Post by xboxbman on 2007-04-25
> **zionykl said:**
> Dear Ubuntu experts,

I have installed my Ubuntu 7.04 Desktop Edition successfully and everything looks great except that I have problem connecting to my Wireless Router using my Compex WLU54G adapter. I provided my passphrase for the WEP and I can see that it said Network Connection to "Name of my Wireless connection" 87%, however, my Firefox cannot connect to any internet sites.

This adapter is working fine on my Vista which is now a dual boot machine.

I really would like to try out Ubuntu but if it is without internet connection, there's a lot of thing I cannot do with it.

Please help.

i find network manager to be a piece of crap.  try wifi-radar.  Just ```
sudo apt-get install wifi-radar
```

I've never had a problem with wifi-radar, but had tons of problems with network manager

---

### Post by kinson on 2007-04-26
You might wanna post the output of this terminal command here:
```

iwconfig

```

(I'm not the expert, but that output might help one of the experts see something :p )

I don't know whether it affects you or not. But on my router, if my WEP key is "abc123", in Ubuntu, when I input "abc123", I make sure I select it under "HEXADECIMAL"...I don't know why I its not ASCII.

Btw, from firefox, can you access your router? (e.g. 192.168.1.1)

*wink

---

### Post by eiapoce on 2007-04-26
> **xboxbman said:**
> i find network manager to be a piece of crap.  try wifi-radar.  Just ```
sudo apt-get install wifi-radar
```

I've never had a problem with wifi-radar, but had tons of problems with network manager

Sorry, I just tried this wifi-radar... it wirtes "connected" but ip information is wrong, does not let me edit the fields and can't disconnect. Its not working either...

Enrico

---

### Post by zionykl on 2007-04-26
Hey,

It is now working!! I am replying this message on my Ubuntu now, yay!

I did not know what I have done, when I did a iwconfig, this is what I have got:
```

lo        no wireless extensions.
eth0      no wireless extensions.
rausb1    RT2500USB WLAN  ESSID:"Ezekkiel"  Nickname:""
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:09:5B:D8:CC:18   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=84/100  Signal level:-58 dBm  Noise level:-202 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

And when I was checking the Ubuntu's user manual in Firefox, because I wanted to try out  the wifi-radar, I have got this instead:

```
E: Couldn't find package wifi-radar
```

So when I clicked on an external link in the user manual, tada... Here I am connected to the internet!!

Thanks, Experts! ;)

---

### Post by kinson on 2007-04-26
Not sure whether you need the Universe or Multiverse repositories to be enabled to find that, but I can find it in mine.

Anyways, if it ain't broke, don't fix it :p

Glad to hear you've got it up and running ! :) Enjoy the experience :)

Cheers,
Kinson

---

