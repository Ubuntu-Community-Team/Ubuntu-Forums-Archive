---
title: "Where and how can i put DNS addresses?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by lalek on 2007-10-25
well, I'm trying to go through System -> Administration -> Network but everytime i enter the DNS addresses given by my ISP provider and close the window,when i open it again the address is back to the default value (192.168.1.1)

I'm have just few days experience with linux so I have no idea if even this is the right thing to do or is there some other procedure for this.

---

### Post by ronald.higgins on 2007-10-25
You can add it in your resolv.conf located in your /etc/ directory.

nameserver IPADDRESSHERE

But normally ISP's assign DNS Automatically.... ???

---

### Post by mikeyphi on 2007-10-25
> **lalek said:**
> well, I'm trying to go through System -> Administration -> Network but everytime i enter the DNS addresses given by my ISP provider and close the window,when i open it again the address is back to the default value (192.168.1.1)

I'm have just few days experience with linux so I have no idea if even this is the right thing to do or is there some other procedure for this.

Are you doing this? In Network - select connections, highlight required network - select properties; select static ip address, enter all settings. select OK, select Close.

---

### Post by lalek on 2007-10-25
well i have the constant problem of not having connection present.or to explain better, the connection is present but only skype recognizes it. nothing else does.or they do but only briefly (10-20secs) and then stop. anyway, anyway,if i somehow succeed in starting some bigger file download (i did this just for test) the connection doesn't drop on the download, but it does on firefox for example. i have no idea what's happening but i'm willing to try anything. 

if you have any suggestion , go ahead please. if you need any file or output just gimme the command and i'll copy it here. 

it's been 3 days now i can't get this thing to work and i'm getting a bit frustrated.

---

### Post by stfury on 2007-10-25
shore.

search for opendns on google. go to the website - they supply a free dns which u can use if u want to - wen u click to setup they have a set of instructions on how to change that 
/etc/dhcp3/something.conf file just go to the opendns u will find instructions there 

i had same problem as u - alternatively if u working from a router try change settings in your router aswell man.

cheers,
stfury

---

### Post by lalek on 2007-10-25
> **mikeyphi said:**
> Are you doing this? In Network - select connections, highlight required network - select properties; select static ip address, enter all settings. select OK, select Close.

hmm static ip? i don't think i have static ip. In windows the setting was "Obtain ip automaticly". So here i went with Automatic configuration (DHCP). If i select static ip then i have no idea what to enter in the fields below :( is that the problem? lol i'll feel so stupid if it is!

---

### Post by mikeyphi on 2007-10-25
> **lalek said:**
> well, I'm trying to go through System -> Administration -> Network but everytime i enter the DNS addresses given by my ISP provider and close the window,when i open it again the address is back to the default value (192.168.1.1)

I'm have just few days experience with linux so I have no idea if even this is the right thing to do or is there some other procedure for this.

OK - so now I'm confused!!!!
If you have DNS address from ISP you can't be using automatic DCHP.
What sort of Internet connection do you have?  Router/modem/wireless?


192.168.1.1 looks like a Gateway address - in which case it should be entered under Network -DNS tab/DNS Servers

---

### Post by lalek on 2007-10-25
ADSL Modem connection i guess 

when i enter the 192.168.1.1 address in firefox after i log in this is what i'm getting.

Status Information
System Uptime 	28 hour(s) 44 minute(s)
DSL Status 	Connected
DSL Speed 	256 Kbps Upstream,
	2048 Kbps Downstream
LAN IP Address 	192.168.1.1
Ethernet 	Connected
DHCP Server 	Running
Software Version 	V1.00B02T02.EU.20040614

---

### Post by arrrghhh on 2007-10-25
192.168.x.x is a local address and you are behind a router of some kind.

i use openDNS, and the dns addresses are in my router so every machine benefits from openDNS.  if you just want to put them into your own computer, after you make the changes to the dns address is there a green check button at the top, right?  i know my settings don't take effect until I hit that green check button.

---

### Post by stfury on 2007-10-25
ok wel the problem is ur machine resets the dns to its default one after a period of inactivity and stuff like that. to stop it doing that u have to follow the instructions on the opendns website

---

### Post by lalek on 2007-10-25
yup! Thank you all!!! 

I followed the instructions on OpenDNS website and it works like charm,both with their DNS addresses as well with the ones provided by my ISP.

Anyway,I'll go with your advice and stick to the openDNS addresses.

Thanks again for your help!

---

