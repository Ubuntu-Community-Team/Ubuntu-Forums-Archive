---
title: "[SOLVED] Has my wireless router just been hacked/attacked???"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by suomalainen on 2008-01-16
Hello Ubunteros:

I have a Linksys wi-fi wireless router model  WRTP54G. I received this router when I subscribed to Vonage fot telephone service.

30 minutes ago I was using my PC and browsing the web when I took notice that my PC was logging onto the wireless network called "linksys".... I tried to figure out where my network called "mountain" went and could not find it!

I logged into the router and discovered that the SSID changed from "Mountain" to "Linksys". All security settings were set to factory default and anyone passing by could log onto my network.

Before making changes to my router, I booted up my laptop with Win XP and confirmed "mountain" had changed to "linksys".

I immeadiately changed my user name and password. for the router. I also created a new SSID and WEP encryption.


The question I have on mind now is as to whether or not my router had been hacked/attacked??? Or is it possible that for what ever reason the router simply reset itself?

Any insight would be much appreciated.

Thank you!

---

### Post by Cypher on 2008-01-16
It is most likely that the firmware on the router reset itself to the default state. It might be wise to see if the firmware on there is the latest, and if not, to upgrade..

---

### Post by tennvolsmb on 2008-01-16
If someone were to hack you I would definitely say they would do more than just reset to factory they would change the password and everything. I would say you router encountered some kind of problem and simply reset its self. It can take sometimes months to hack a Wi-Fi with a WEP encryption unless you have the right computers hardware and software. I would think just re make everything and you should be fine!

---

### Post by suomalainen on 2008-01-16
Cypher,

Thanks for the feedback. If this is a reset issue, is it something that happens from time to time? This router has been up and running for about 3 years now.

Not sure if you know how to answer my next question but if I was hacked or attacked are their sights that I could look for?

Thanks again!

---

### Post by tennvolsmb on 2008-01-16
Routers most definitely can do that after a while. I have the exact same type of router on my house computer and I know on more than 1 occasion it has happened to me. I would think you are safe just resetting everything to the way it was before.

---

### Post by suomalainen on 2008-01-16
tennvolsmb, I think you said it all. If someone were to wreck havoc I guess they would have done a little more..... But I wonder if this is a sign that a new router may be needed down the road?

---

### Post by jrusso2 on 2008-01-16
My Linksys seem to last about three years.  Make sure you don't use the default paswords.

---

### Post by Cypher on 2008-01-16
Technically no the router should never reset back to factory defaults. If it was overloaded for some reason, it might reset, but it should retain all of your configuration and not revert to the fully open state it had. Having said that, and the fact that router is 3 years old, you've probably not been upgrading it, so who knows what might be wrong with that firmware or what new exploit has become available on the 'Net.

Now if indeed someone managed to reset your router to it's default state, they could login and see all the DHCP'ed IP addresses given out and then in turn figure out what the IP addresses of any and all machines in your local network. From there, it depends on what OS those machines are running, if Linux, they could try to connect to it but it would be hard to get much farther without your username/password and it's hard to randomly guess at what the username might be..

Having noticed this issue with the router, you might want to change your passwords just to be on the safe side and just poke around to see if there is anything strange..

---

### Post by suomalainen on 2008-01-16
Yea... I think everyone knows admin admin by now...... Or was that guest and password?........

---

### Post by stchman on 2008-01-16
> **suomalainen said:**
> Hello Ubunteros:

I have a Linksys wi-fi wireless router model  WRTP54G. I received this router when I subscribed to Vonage fot telephone service.

30 minutes ago I was using my PC and browsing the web when I took notice that my PC was logging onto the wireless network called "linksys".... I tried to figure out where my network called "mountain" went and could not find it!

I logged into the router and discovered that the SSID changed from "Mountain" to "Linksys". All security settings were set to factory default and anyone passing by could log onto my network.

Before making changes to my router, I booted up my laptop with Win XP and confirmed "mountain" had changed to "linksys".

I immeadiately changed my user name and password. for the router. I also created a new SSID and WEP encryption.


The question I have on mind now is as to whether or not my router had been hacked/attacked??? Or is it possible that for what ever reason the router simply reset itself?

Any insight would be much appreciated.

Thank you!

My advice, WEP is practically worthless.  I recommend WPA or WPA2 and make sure and use strong passphrase of at least 35 characters.

---

### Post by suomalainen on 2008-01-16
Does anyone know the procedure for up dating the firmware on the WRTP54G?

Thansk

---

### Post by julian67 on 2008-01-16
This is true. WEP can be broken in minutes. If you have 2 wireless adapters and some freely available tools you can break a WEP protected network in less than 30 minutes. Use WPA,  and strong password on your router's admin. Disable remote management so you must have a wired connection to make changes to the router.

---

### Post by gsub on 2008-01-16
I have one of those routers myself, and it seems to come with a option where you can specify "Only these MAC addresses are allowed to connect". Wouldn't that be the most secure?

---

### Post by suomalainen on 2008-01-16
Thanks so far for all the help and advice. It looks like I need to make some changes? Below I listed what I found from my router. Is this the right setttings I want? If not what do I need to look for?


 Security Mode: 	WPA Pre-Shared key  	  	 
 WPA Algorithms: 	TKIP  	  	 
 WPA Shared  Key: 	  	ENTER #% DIGITS HERE  	 
 Group Key  Renewal: 	3600  seconds

---

### Post by ronmarley1 on 2008-01-17
> **suomalainen said:**
> Does anyone know the procedure for up dating the firmware on the WRTP54G?

Thansk

I updated mine using the instructions on the Linksys site: [http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1169671597629&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=9762937314B360&displaypage=nodata](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1169671597629&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=9762937314B360&displaypage=nodata)

Also, newer models of this router have a Reset button (mine does not).  Maybe you bumped that?  Does the reset button reset to factory defaults?  Sorry, just guessing here.

---

