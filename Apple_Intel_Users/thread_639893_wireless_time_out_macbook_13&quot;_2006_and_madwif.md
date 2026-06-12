---
title: "wireless time out macbook 13&quot; 2006 and madwifi driver"
date: 2007-12-13
forum: Apple Intel Users
---

### Post by trevelyn on 2007-12-13
I wrote a shell script to control my wifi card myself, that goes like this:

> 
iwconfig ath0 essid "Waek-Net1" key DEADDEAD1337DEAD1337DEAD69 channel 11
dhclient ath0 

and it works great, i uninstalled network manager, and have been opening up a terminal and using this scrpit to attach the router, but.. I get an IP, then after about 5~10 minutes maybe, i lose the IP.  i disassociate and cant ping the router, i have to run my script again.  What sucks the most is that Pidgin doesnt tell me im offline, until i after have sent every messages and have been off for 5 minutes thinking im the only person alive on earth.

any ideas why it would die like that???

---

### Post by cyberdork33 on 2007-12-13
First, thanks for your AP info!

second, have you tried to compile the latest madwifi as there was a bug in the some of the older versions that caused a problem with disconnects.

---

### Post by trevelyn on 2007-12-13
AP info? lol
my routers password is password too! 

yeah i got madwifi r2717 is there a better option?

---

### Post by trevelyn on 2007-12-13
i went into my old directory for r2717 and did make uninstall and left, downloaded the newest version available from madwifi.org and untarred it, cd into it and make/make install it all went fine, but after reboot there was no wlan card at all. lolol
then i did the same uninstall process, and cd'd back to my r2717 directory and INSTEAD of patching the madwifi with the wesside-ng patch, this time i just did make/make install and I will wait this out and test it.  It did associate and grab an IP extremely fast i noticed just now.  I never saw it go that fast, before i would see the messge from DHCPNAK <..>

thanks,  - trev.

---

### Post by trevelyn on 2007-12-14
nope after testing i found that that did nothing.  


if i run a constant ping at google, on 3 different routers i get the same result.
at least %40 packet loss and the pings start and stop and tsrta and stop after every 10 seconds or so.  what a piece of crap.  does anyone have the newest madwifi drivers (that actually work) for the macbook 13" late 2006? I will keep searching and playing with the installs.

---

