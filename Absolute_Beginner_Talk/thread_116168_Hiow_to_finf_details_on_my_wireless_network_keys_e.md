---
title: "Hiow to finf details on my wireless network keys etc?"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by andrewsco on 2006-01-12
Hi.

How can I find out information on my wireless network? From a tutorial I need to find out this information and I'm not sure how to do it. If it requires the internet,  can only do this through windows, as I have no internet on Ubuntu (yet!)

> 

# Enter your essid here
wireless-essid XXXXXXXXXXXX

# Enter your WEP key using colons for 128bit WEP
wireless-key XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XX

# Enter your MAC address for your Wireless Access Point using colons
wireless-ap XX:XX:XX:XX:XX:XX

There are no passwords or security keys on it - and it is called 'default' 

Thanks
Andrew

---

### Post by AndyCooll on 2006-01-12
So your wireless network is open to the world?

In which case it may be easiest for you to use your Windows pc to set up the security features for your wireless network.

You usually set up the the wireless-essid (the name of your wireless network)and wireless key on the access point itself. In my case I open up Firefox and type 192.168.2.1 into the address bar, after putting my password in it logs me onto the router/access point. It is here I can set the wireless network security (i.e. the WEP key). You might need to read the manual for further details.
It is also here where you can usually find details about the access points MAC address.

:cool:

---

### Post by andrewsco on 2006-01-12
Can I just apologise for my appauling spelling in the title... I only just noticed it.

Yes it is open to the world! I thought it would be easier that way to connect through linux? At the moment I would rather have an insecure connection that works than a secure one that doesn't - although ideally both. Anyway where I live is in a rural ish area, old people live next door - there is not as much need for security really.

Thanks
Andrew

---

