---
title: "Can't join wep-protected network"
date: 2007-03-29
forum: Apple Intel Users
---

### Post by scorpio2002 on 2007-03-29
Hi there! I own a macbook core duo and installed ubuntu feisty 7.04. It correctly recognizes my wifi-card, and it can connect to unprotected networks. But when it comes to wep-protected networks, it isn't able to connect and goes on asking for a valid key even if I give it the correct key...

is it a known bug? is there a solution?

---

### Post by handaxe on 2007-03-29
Advice from chili555; try this tutorial:

[http://www.ubuntuforums.org/showthre...=172810&page=2]("http://ubuntuforums.org/:http://www.ubuntuforums.org/showthre...=172810&page=2")

HA

---

### Post by scorpio2002 on 2007-03-29
the link is broken and brings me back to the main forum page...

---

### Post by jsc1959 on 2007-03-29
I had to manually set my wep key like this

sudo su

iwconfig wlan0 key abcdef1234

and then restart the network by 

/etc/init.d/networking restart

then it works. Im using it now with wep.

---

### Post by handaxe on 2007-03-29
Corrected link is:

[http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

HA

---

### Post by pgroover on 2007-03-31
> **jsc1959 said:**
> I had to manually set my wep key like this

sudo su

iwconfig wlan0 key abcdef1234

and then restart the network by 

/etc/init.d/networking restart

then it works. Im using it now with wep.

Thanks a million for this one!  I was going nuts trying to figure out what was wrong with my connection and could find nothing.  Didn't even consider restarting networking, but I had done everything else under the book! :)

---

### Post by jsc1959 on 2007-03-31
did it work?

---

### Post by scorpio2002 on 2007-03-31
it worked just one time, never again. Now, if I use this method, I can connect, everything seems configured in the proper way, but it won't ping any ip (not local or external).

dunno. With other distros I never had this kind of problems. Something is broken in ubuntu. Hope they fix it before they release the stable one.

---

### Post by pgroover on 2007-04-01
I have to agree with the one shot bullet as it hasn't worked for me either since the first time.  I upgraded to Feisty this weekend and now I'm connectionless (at least through WEP that is) for now.

---

### Post by pgroover on 2007-04-01
Okay, I was finally able to join my wep network with the following commands placed into a script:

#!/bin/sh

sudo ifdown ath0
sudo iwconfig ath0 essid NETWORK_NAME key ENC_KEY ap AP_MAC_ADDRESS
sudo ifup ath0
sudo dhclient ath0

NetworkManager still shows no connection, but I know I'm up and running so I'll just ignore the visual clues for now and worry about it later.

As for madwifi, I have installed it, but strangely enough I wasn't able to install it until _after_ I got connected via my network.  IOW, using other networks I was unable to resolve the address but now everything works fine including updates I was unable to get earlier. :)

Edit: The connection does work but it does tend to be sporadic and sometimes requires being run a few times to re-establish after a reboot.  It's not a 54MB connection, but in the end I am connected so maybe it can work for others as well.  Nothing new in the script but for whatever reason, it works...

---

### Post by pgroover on 2007-04-02
Okay, everything is working perfectly well.  It turns out that my problem was me!  I had forgotten that in my haste to get things setup earlier that I had set up an "Open" connection versus "Shared".  I just thought about it a few minutes ago and corrected my router and now things are as they should be!

What lesson should be learned from this?  Simple, always check behind yourself otherwise you'll forever be chasing your own tail...

---

### Post by scorpio2002 on 2007-04-02
This is gonna drive me crazy :( Really hope someone will be able to fix this wep thing before the stable is released... it sucks -.-

---

