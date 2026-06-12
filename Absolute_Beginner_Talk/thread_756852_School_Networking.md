---
title: "School Networking"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Slayze on 2008-04-16
Just installed Ubuntu 7.10, dual booting with Vista on a laptop recently. Tried to connect to my school's network while using Ubuntu and failed.
Guides on how to connect on other operating systems are given on their site [over here](http://www.nyp.edu.sg/cnc/wireless_get_connected.html), but being new to this, I got no idea on how to use them for Ubuntu.

Can anyone suggest a method? Hopefully, a simple one. Though anything hard is better than nothing.

---

### Post by Paqman on 2008-04-16
You might need to make friends with the network's proxies. If it's working in Windows go into IE > Tools > Internet Options > Connections > LAN Settings and take note of anything that's in the proxy settings. The put the same into Ubuntu's Firefox > Edit > Preferences > Advanced > Network > Settings > Manual Proxy Configuration.

---

### Post by Slayze on 2008-04-16
Alright, I'll try that.
Even though I can't connect to or even find the network at all, on Ubuntu, would it help?

---

### Post by smurphy_it on 2008-04-16
I know windows machines use the WORKGROUP option and all the computers need to be a member of the same workgroup.  With ubuntu, it uses samba, but one would assume it would also need the same workgroup.

If so, change your workgroup name to match that of the school's network.

System, Administraion, network

---

### Post by Paqman on 2008-04-16
> **Slayze said:**
> Alright, I'll try that.
Even though I can't connect to or even find the network at all, on Ubuntu, would it help?

Can you get a connection in Vista though? If so, does it connect automatically, or did you have to set it up?

---

### Post by Slayze on 2008-04-16
It works when I set it up using the guide I linked to in my first post. Doesn't connect automatically.
There's a username/password/login domain prompt as well.

---

### Post by ibgeorgeb on 2008-04-16
I'm a newbie to Ubuntu 6.10 also. I was having the same problems (username, password, etc) too. Our school network admin. advised me to get a windows laptop computer because Ubuntu was a strange system that didn't work with our district's system. I found an old linksys wireless router, plugged that puppy into the outlet, plugged in the power cord and powered it up. Lw and behold! I'm connected via wireless and I am right now wrting this from my classroom on my Ubuntu 6.10 Dapper computer that wasn't suppose to work with our school system. Don't understand how it works but it does. Just my thoughts....:confused:

---

### Post by Paqman on 2008-04-16
If you click on the wifi icon on the top right you should see the option at the bottom of the list of networks to set up a new wireless connection. You can use the details from the Windows/OS X guides regarding SSID, WEP, etc.

---

