---
title: "Xubuntu: Wireless Access Finder"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-11
Hi, I have used Net Stumbler in the past to secure my wireless
network now that I have xubuntu, I need a program
that will do the same thing. Thank you....  :KS

---

### Post by reckless2k2 on 2007-09-11
how would you use net stumbler to secure your network? net stumbler will show if you have an open network but you can tell that by logging into the wifi admin page. 

depending on what you are trying to do your answer is probably with kismet. you have to edit the kismet.conf for your wifi card though.

---

### Post by Orbital75 on 2007-09-11
Hi, Sorry I guess I should have went into more detail.
I use Net Stumbler to see how many access points are
around my house and where the strongest signals are
coming from.  This let me know where in the house to
place my Phones and Access Points to prevent interference.

Of course I use the standard MAC Address filtering, Disabling SSID Broadcast,
and WEP ( I have cards that don't support WPA ). I seem to get alot of interference
from houses with these Speed Boast Wireless Routers. Not sure what causes
the drop out but I like to place my Wireless things away from the strong signals.

Thank you for the Kismet recommendation.  How hard is it to set up?

---

### Post by reckless2k2 on 2007-09-11
kismet is definitely what you want and far more powerful than net stumbler. it only takes a tiny bit of know how in the kismet.conf file to specify your wifi card. 

sudo apt-get kismet

then check out the kismet site on the source spec. depending on your wifi card...plug it in and asave and fire it up done. it's run fro cli but VERY powerful. most penetration testing starts at kismet.

---

### Post by Maestro23 on 2007-09-11
Kismet site: [http://www.kismetwireless.net/](http://www.kismetwireless.net/)

---

### Post by Orbital75 on 2007-09-11
Hi...... Well, I downloaded Kismit with the Synaptic Packet Manager but there is no icon
in my menu.  I went to the kismit site and as you said you have to configure the
kismet.conf file.  Well, I have a slight problem.

Edit the config file (standardly in "/usr/local/etc/kismet.conf")

This path doesn't exist in my Xubuntu.

Do you know where that file is?

Also, I saw the list of Capture Sources.

Would you happen to know what source my Card uses.
Linksys WPC11  ( 802.11 B )


Thanks

---

### Post by Maestro23 on 2007-09-11
> **Orbital75 said:**
> Hi...... Well, I downloaded Kismit with the Synaptic Packet Manager but there is no icon
in my menu.  I went to the kismit site and as you said you have to configure the
kismet.conf file.  Well, I have a slight problem.

Edit the config file (standardly in "/usr/local/etc/kismet.conf")

This path doesn't exist in my Xubuntu.

Do you know where that file is?

Also, I saw the list of Capture Sources.

Would you happen to know what source my Card uses.
Linksys WPC11  ( 802.11 B )


Thanks

Open a terminal:

> locate kismet.conf

---

### Post by Orbital75 on 2007-09-11
Thanks......  I try that out...

Any idea what source to use?  :KS

---

### Post by reckless2k2 on 2007-09-11
sorry...the kismet.conf is in either /etc/kismet.conf or /etc/kismet/kismet.conf


can't remember which one..

also...you run kismet from cli

sudo kismet

---

### Post by Orbital75 on 2007-09-12
Thanks for the help. You were correct the kismet.conf was in 
the /etc/kismet/kismet.conf

There are a few things that I can't figure out to get it working.

1: * Set the user Kismet will drop privileges to by changing the "suiduser"
      configuration option.

Does this mean I change "suiduser" to my user name?


2. * Set the capture source by changing the "source" configuration option.
      FOR A LIST OF VALID CAPTURE SOURCES, SEE THE SECTION OF THIS README
      CALLED "CAPTURE SOURCES".  The capture source you should use depends

      on the operating system and driver that your wireless card uses.
      USE THE PROPER CAPTURE SOURCE.  

I can't find anyone that knows what source to use.
I believe its the Prism2

Linksys WPC11 ( 802.11 B )

I think this is the source I need

```

hostap         Prism/2             Linux       HostAP 0.4
                    http://hostap.epitest.fi/
                    Capture interface:  'wlanX'  
                    HostAP drivers drive the Prism/2 chipset in access point
                     mode, but also can drive the cards in client and monitor
                     modes.  The HostAP drivers seem to change how they go
                     into monitor mode fairly often, but this source should 
                     manage to get them going.

```

So I am thinking it would be set up like this.

**'source=type,interface,name[,channel]'.**

'source=hostap,wlanX,Prism2[,channel]'.

So do I need to put source code anywhere? or just type in names and fill on the blanks as I have done up above?
Also, see where it saids wlanX.  Should I put 0 there so it reads wlan0 ?

---

### Post by reckless2k2 on 2007-09-12
yeah you'll have to do a little checking on your chipset for the source info but you want to make it like this:

source = madwifi_g,ath0,ath_source


that's all you need. like mine was an atheros chipset. 

you have to find out what version wpc11 you have because some version are using prism and others broadcom. if you are suing broadcom you might have a few issues. supposedly bcm43xx works but i don't know what driver you are using or how you setup your wifi. ndiswrapper?

i used atheros because i was doing penetration testing and needed to inject and sniff at same time.

---

### Post by Orbital75 on 2007-09-12
Thanks, I'll give that a try.....
It really doesn't seem that hard but
since I'm a new Linux user I have to figure
things out.  

Not knowing the card drivers
or where to find this information is a little hard
as well.

Thanks again for your help, I doubt I could
have figured it out without you.  :)

---

### Post by Orbital75 on 2007-09-12
Got it up and running......

Got a quick question though.
What is this AutoMode.  It seems like
everything I try it states it can't preform action because
Automode won't alow it..... 

THis is very different from NetStumbler
I'm thnking I can't see most of the features
because it's in this AutoMode.

Any ideas how to get a better experience from it.
I've never used it before so I'm just playing around
with it.  So far all it does it count packets and show 12
other networks.  I'd like to see a Strength Meter of each
network it finds.

---

### Post by reckless2k2 on 2007-09-12
the features and or settings in kismet are pretty robust. off hand, i can't remember how to get it out of auto mode/scan. there is a help file right in the program though i think you access from just H or soemthing like that. that's how i learned how to use a lot of the features. i remember your specific situation but i can't remember the easy solution. i know there is a help file right in the program that told me the commands.

---

