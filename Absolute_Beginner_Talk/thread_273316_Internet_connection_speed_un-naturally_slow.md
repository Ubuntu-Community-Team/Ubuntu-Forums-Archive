---
title: "Internet connection speed un-naturally slow"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by fedupwithwin on 2006-10-07
My internet connection is running very slow since I installed Ubuntu.  I have a high speed connection, a new cat5 cable to my router, I checked all my connections and I have two other windoze machines on the same router that have good connection speed.  The weird thing is that the connection will pause for a while and then run like crazy.  Even bringing up the main google search page can take a while.  I was wondering if maybe I need to update some files?  It's just that every time I try to perform the automatic updates I get all kinds of download fail messages.  

Please help - this is getting aggravating. :confused:

---

### Post by wieman01 on 2006-10-07
Disabling IPV6 both globally and in Firefox will - most likely - resolve your problem. Check out some posts in this forum...

---

### Post by JayTee on 2006-10-07
If you're using a router that's plugged into a cable modem, try plugging your computer running Ubuntu directly into that to bypass the router. If you've setup your network config for DHCP then you'll probably need to reboot to reset your IP configuration or maybe someone else can add to this thread what the command line equivalent of Windows "IPCONFIG /RENEW" is. If your connection issues don't remain when connected directly to the cable/dsl modem then there is a problem between the router and your Ubuntu computer. Since your Windoze comps are running ok the router is probably fine and the Ubuntu configuration needs tweaking. Sometimes IPv6 is enabled and that can slow some sytems up. I had to turn off IPv6 in Firefox because it was slowing it down. If you've installed a firewall on you Ubuntu box try turning it off or tweaking it's config.

---

### Post by fedupwithwin on 2006-10-07
Forgot to mention - I'm running firefox V1.5.0.5.

Also, whenever I go to "System" "Network Settings" and select the "general" tab, My host name is shown but the domain name is blank. Even if I type something in for the domain name it will not retain it when I check again later.  Am I supposed to have a domain name for a home system?  I work with computers all the time and do a lot of machine control programming, I'm just not real familiar with internet jargon.

---

### Post by wieman01 on 2006-10-07
> **fedupwithwin said:**
> Forgot to mention - I'm running firefox V1.5.0.5.

Also, whenever I go to "System" "Network Settings" and select the "general" tab, My host name is shown but the domain name is blank. Even if I type something in for the domain name it will not retain it when I check again later.  Am I supposed to have a domain name for a home system?  I work with computers all the time and do a lot of machine control programming, I'm just not real familiar with internet jargon.
Try to disable **"ipv6"**. Your problem sound strangely familiar and the forum is full of such posts. This will increase the performance tremendously. I have experienced & done the same thing.

---

### Post by JayTee on 2006-10-07
You don't need a domain name in your config. I don't have one in mine. If you are using Firefox type about:config in the address line and hit enter. Navigate down the list to find the entry network.dns.disableIPv6 and change the boolean flag to "true" from the default which is false.

---

### Post by fedupwithwin on 2006-10-07
OH YEA!!!  I'm feeling MUCH better now.  I search the forum for "Disable IPV6" and got the whole deal.  I would not know enough to search for this particular text combination otherwise.  Seams as if some of the purists have beat this dead horse flat in the past.  Anyway, thanks - in a huge way - you saved me a lot of sweat.

---

### Post by wieman01 on 2006-10-07
> **fedupwithwin said:**
> OH YEA!!!  I'm feeling MUCH better now.  I search the forum for "Disable IPV6" and got the whole deal.  I would not know enough to search for this particular text combination otherwise.  Seams as if some of the purists have beat this dead horse flat in the past.  Anyway, thanks - in a huge way - you saved me a lot of sweat.
Glad it helped. Let us know if we can be of assistance with other wireless topics (file sharing, tuning, WPA1/2, etc.). :-)

---

### Post by fedupwithwin on 2006-10-08
After diabling IPV6, I performed all the updates requested by the update manager and my internet connection starting bogging down again.  It seems as if the IPV6 issue is rearing it's ugly head again.  When I originally disabled it, I used the technique of creating the "bad_list" file in the "/ect/modprobe.d" directory with the "alias net-pf-10 off" command so updates would not effect this setting.  I aslo disabled IPV6 in firfox via the "About:config" setting.  One thing I noticed is that when I bring up the network settings and click on the "Hosts" tab, six out of eight of the host names have an "IP6" prefix on the "aliases" entry.  Is this relevant to IPV6?  If so, how do I disable it?  

Thanks in advance - The Manic Mechanic

---

### Post by wieman01 on 2006-10-08
> **fedupwithwin said:**
> One thing I noticed is that when I bring up the network settings and click on the "Hosts" tab, six out of eight of the host names have an "IP6" prefix on the "aliases" entry.  Is this relevant to IPV6?  If so, how do I disable it?
I remember you can delete them using the Gnome applet. Yes, they relate to "ipv6", so you need them by no means.

---

