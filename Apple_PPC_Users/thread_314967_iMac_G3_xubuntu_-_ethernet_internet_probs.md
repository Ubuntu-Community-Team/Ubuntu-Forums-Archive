---
title: "iMac G3 xubuntu - ethernet internet probs"
date: 2006-12-08
forum: Apple PPC Users
---

### Post by samden on 2006-12-08
I have just successfully installed Xubuntu 6.06 on my iMac G3, now I need to get the internet working. I have an ethernet connection to my work network, but don't have permission to access the network as such. I can access the internet through the network, through a proxy server. I have done this using my iBook G4 running OSX - all I do is type in the name of the proxy server and off we go. What do I do with Xubuntu?

I have tried entering the proxy server into Firefox, no go.

I have ensured that the ethernet connection is activated in networking and the modem is deactivated.

Not sure where to go from here. Thankyou.

Edit:
I have also tried downloading the repository indexes through the software manager - this could not be contacted either due to network problems. So the problem is not just with Firefox.

---

### Post by samden on 2006-12-11
OK, now this is odd. I have installed the Gnome dictionary utility. Now I find that it actually works. This is odd, as the dictionary looks up definitions online (I know this for a fact as it doesn't work when the ethernet cable is unplugged).

So the dictionary can access the net. But neither Firefox or the package manager can. Why could this be? How might I be able to fix it?

Thankyou.

---

### Post by stream303 on 2006-12-11
I wrote a little howto that might be of interest if you find you can ping, but can't surf (resolve dns).  Maybe something here can help:

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

btw, I have been experimenting with OpenDNS and find that it works pretty well.

---

### Post by samden on 2006-12-12
What I have tried now:

Editing /etc/resolv.conf

Editing /etc/dhcp3/dhclient.conf

Disabling IPV6

Still no internet. But I can download email through Thunderbird, I can ping websites, and when I put the 'network monitor' icon in my top bar it fluctuates saying I have incoming network traffic, even when I have no applications open.

So the computer is on the internet. But it won't let me look at websites or download updates and software.

Very, very frustrating. I am at a loss as to what to do.

Edit:
I have run through the troubleshooting procedure on [http://doc.gwos.org/index.php/Wired_Ethernet_Troubleshooting](http://doc.gwos.org/index.php/Wired_Ethernet_Troubleshooting). Everything here works - I can ping [www.google.ie](www.google.ie) by both name and number for example. So the problem definitely has something do do with my end.

Edit:
I have now tried all three options on [http://doc.gwos.org/index.php/Router_DNS_Problems](http://doc.gwos.org/index.php/Router_DNS_Problems) with no luck either.

---

### Post by samden on 2006-12-13
I just installed dillo in case it was a problem with Firefox, as I have had problems with a version of Firefox in OSX before. However Dillo is unable to connect to webpages either - just gives the message 
"ERROR: unable to connect to remote host"
So Firefox is certainly not the problem. I'm rather stuck.

---

### Post by samden on 2006-12-14
I have decided to continue this thread in the networking section of the forum, as I may get more response there. Feel free to post a response here, but for the latest on my situation visit

[http://www.ubuntuforums.org/showthread.php?t=317996](http://www.ubuntuforums.org/showthread.php?t=317996)

Thankyou. 8)

---

