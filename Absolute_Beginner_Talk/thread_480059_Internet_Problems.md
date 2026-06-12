---
title: "Internet Problems"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Messiah1095 on 2007-06-21
Hey all. Long time Windows user, first time Linux user.

I'm currently having a problem getting my internet to work through our work proxy here. At home it works fine through the direct connection to my router. I've put in the correct proxy and authentication details under the Network Proxy settings but neither Firefox or Add/Remove Programs will connect to the net. 

Is there a setting somewhere I've missed?

---

### Post by p_quarles on 2007-06-21
What kind of connection are you using? Ethernet? Wireless?

---

### Post by Messiah1095 on 2007-06-21
Ethernet at the moment, using DHCP which has picked up all of the right settings.. Can't seem to connect up to wireless at work.

---

### Post by p_quarles on 2007-06-21
Shot in the dark: Have you tried connecting to your work network WITHOUT the proxy settings? 

My only other idea is to go to Places >> Network and then enable roaming.

---

### Post by Messiah1095 on 2007-06-21
I've tried not putting proxy settings in and also enabling roaming, no go.

We have two proxy servers here, one is a Windows Server 2000 based proxy and the other is a modified Linux proxy. Can't seem to get a connection on either.

---

### Post by p_quarles on 2007-06-21
It sounds like you're using a laptop, so you might look up the compatibility of your wireless card ([https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)). If your card isn't supported natively in Ubuntu, you can still use NDISwrapper to install the Windows driver. 

Don't know what else to tell you.

---

### Post by Messiah1095 on 2007-06-21
My wireless works fine on my home connection, for some reason it just doesn't accept the password that I'm giving it for the wireless system at work.. Using an IBM Thinkpad R52 by the way.

Edit: Just got wireless to work, used 64 bit instead of 128. Which is weird cause the key is meant to be 128 :Z

And yeah, I'm not sure what else to do about this proxy stuff. Basically ran out of ideas.

---

