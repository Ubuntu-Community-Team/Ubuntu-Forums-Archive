---
title: "Internet access"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by SergeantSunshine on 2005-11-30
I've installed Ubuntu on the same machine as Windows.  Windows can get to the internet, Ubuntu can't.  

I am using a D-Link ADSL router which issues DHCP IP addresses on the LAN.  

Ubuntu is getting an IP address, but still can't access the internet through the browser.  

I can use the browser to get to the config screen of the router by specifying the IP address.

I was wondering if something is up with DNS, but can't see anywhere to configure (any of) the internet settings.

I'd appreciate some help.

---

### Post by basketcase on 2005-11-30
System -> Administration -> Networking -> DNS Tab -> See if you can add your DNS servers there.

---

### Post by SergeantSunshine on 2005-11-30
OK.  Unfortunately, I don't actually know which DNS servers I use for Windows since I use DHCP for these.  Can't Ubuntu do the same?

---

### Post by ex` on 2005-11-30
[QUOTE=SergeantSunshine]OK.  Unfortunately, I don't actually know which DNS servers I use for Windows since I use DHCP for these.  Can't Ubuntu do the same?[/QUOTE]
Try specifying your router's IP address as primary DNS server. That ought to do the trick.

The problem seems to be that DNS servers aren't sent by the DHCP server on your router, or that Ubuntu doesn't query for them.
You can either specify a DNS server manually (easy fix), or edit your dhclient.conf so that is queries for them. (sudo nano /etc/dhcp3/dhclient.conf and add request domain-name-servers to it, but if I recall correctly there were some problems with this (in an earlier package), so I'm not too sure if this will solve it).

---

### Post by basketcase on 2005-11-30
And if you're not sure of your ISP's DNS numbers, while in XP, go to Start -> Run and type cmd press enter.  At the prompt, type ipconfig /all and you should get your DNS addresses.  Take those, and put them in the linux box.  

The above suggestions sounds like the best way to do it.

---

### Post by SergeantSunshine on 2005-11-30
OK.  Thanks for all the help.  It's still not working though.

I've checked in the DNS config and the router address (192.168.1.1) is set as the DNS server.  I've looked in Windows ipconfig and that's the one it has received from DHCP.

Is there an equivalent to ipconfig in Linux?  I can't find anything which tells me the live DNS server address.

I'm beginning to think that DNS may not be the problem.  What do you think?

---

### Post by basketcase on 2005-11-30
Can you look in the admin panel of the router to get the DNS address that it is using?  I know I can see DNS addresses in the control panel of my linksys routers.

---

### Post by basketcase on 2005-11-30
BTW, 
You could also contact your host and ask them for local DNS servers.

---

### Post by SergeantSunshine on 2005-11-30
I'm wondering why I can't simply get the DNS servers through DHCP like Windows does.  It seems a bit of a crowbar to set them manually.

Actually, Windows ipconfig tells me that it is using the address of the router as its DNS server and I notice that Linux has the same address set in its config. Soooo......  is there a way of checking what it is actually using in the same way that ipconfig does it for Windows?

---

### Post by SergeantSunshine on 2005-11-30
BTW I'm about to go through the reboot and back. It takes a while, but I'll be back soon.

---

### Post by SergeantSunshine on 2005-11-30
I've checked out the dhclient.conf file and it already has the request domain-name-servers set.  I'm running out of ideas.  Perhaps the problem has nothing to do with DNS......  What do you think?

---

### Post by exiztone on 2005-11-30
Hello, I'm having the exact same problem! I also have a D-Link router. Works fine in Windows and just won't work (for me) in Linux. I know it's only has Windows and Mac support BUT I was using Mandriva last week and I managed to get the Internet to work for a little bit (I have no idea what I did though :/)

Anyway, I have a question. To fix this problem, should I be entering my ISPs DNS addresses or my router's DNS address? I'm not too sure?

With that ipconfig command, it says my DNS is 192.168.1.1 (which is my router) sooo, what do you recommend? I have my ISP's handy though :)

Cheers!!

Edit: Someone on the IRC room mentioned that enabling UPnP in the router might help? Can anyone expand on this? I too am also on a dual boot, so I gotta get a good chunk of information before I try anything ;)

---

### Post by SergeantSunshine on 2005-11-30
I just enabled UPNP on the router and it stopped even allowing Windows access to the internet!  It took a bit to disable it again as it kept rebooting itself.  I've got Windows back on line (as you can see), but Linux still doesn't seem interested.

It's a few years since I played with IP protocols, but it seemed easier then.  You just had to ensure that you had an IP address and a DNS server and it all worked.  I wonder why life is more complicated now.

I've run out of ideas and am going to sleep on it (it's midnight here in the UK).  I might have inspiration tomorrow.  In the meantime, if anyone has any ideas (note that I'm not alone with this problem as you can see above), I'd be very grateful.

---

### Post by exiztone on 2005-11-30
Hi. I disabled IPv6 and it seemed to do the trick. I guess that was what was happening in Mandriva before, it must have been accessing the web, but only after a long time of trying. :)

I have one more problem though. Because I fiddled around with the Admin/Networking panel, any time I boot Ubuntu I get a message saying

Could not look up internet address for . (I think I took my hostname out)
This may prevent GNOME from operating correctly.
Add it to etc/hosts

How do I do this? I can't access the Networking panel in Administration anymore. :(

---

### Post by ex` on 2005-11-30
I'd simply start diagnosing the problem, so;

[list][*]Can you ping 62.58.50.5 ?
[*]What are the contents of /etc/resolv.conf?
[*]What's the output of a "nslookup ubuntulinux.org"?[/list]

edit:
Ah, you found the problem already.
About /etc/hosts, read [this](http://ubuntuforums.org/showthread.php?t=97211) topic. :)

---

### Post by SergeantSunshine on 2005-12-01
So disabling ipv6 is the answer is it?  And how do I do that?  I have discovered that DNS isn't the problem since "ping www.ubuntu.com" and "nslookup www.ubuntu.com" both work.  However Firefox still isn't interested.

I was wondering if Ubuntu has some ultra-safe firewall defined, but I can't find any reference to security anywhere.  Actually, I guess that will be the next thing to sort out once the internet is happy.

---

### Post by SergeantSunshine on 2005-12-01
How do I disable ipv6?  

I still can't get Firefox running.  
DHCP is working.  DNS is working.  I can ping [www.ubuntu.com](www.ubuntu.com) and nslookup works.

I've run out of ideas now.

---

### Post by ex` on 2005-12-01
[QUOTE=SergeantSunshine]How do I disable ipv6?  

I still can't get Firefox running.  
DHCP is working.  DNS is working.  I can ping [www.ubuntu.com](www.ubuntu.com) and nslookup works.

I've run out of ideas now.[/QUOTE]
1. sudo gedit /etc/modprobe.d/aliases 
2. Find the line:  alias net-pf-10 ipv6 
3. Replace it with:  alias net-pf-10 off 
4. Save the file and restart your computer
Source: [Ubuntu WiKi](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4). :)

---

### Post by Chippendale on 2005-12-01
[QUOTE=SergeantSunshine]
Is there an equivalent to ipconfig in Linux? 
[/QUOTE]

ifconfig

---

### Post by SergeantSunshine on 2005-12-02
Well - I've found the answer in another post on this forum:

[http://www.ubuntuforums.org/showpost...8&postcount=26](http://www.ubuntuforums.org/showpost...8&postcount=26)

I'll try the other solution above as well.  Thanks for everyone's help with this.

You'd think that Firefox would have something in the help file about using "about:config" wouldn't you?

---

