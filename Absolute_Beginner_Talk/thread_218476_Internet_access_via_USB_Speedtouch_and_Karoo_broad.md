---
title: "Internet access via USB Speedtouch and Karoo broadband"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by scunepo on 2006-07-18
Hello

I am new to Linux and have recently loaded Ubuntu Dapper Drake.  

My problem is that I can't get internet access.  I have Karoo broadband via a USB Speedtouch ADSL modem.  I have been trying for a few nights to crack the problem but I am now at a loss.  I have followed two different guides on installing the Speedtouch firmware etc and I think I may eventually) have managed to  get access to my ADSL line.  The syslog reads:

Jul 18 20:30:47 graham-desktop kernel: [4295660.398000] ATM dev 0: ADSL line is up (608 kb/s down | 288 kb/s up)
Jul 18 20:31:02 graham-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jul 18 20:31:02 graham-desktop dhclient: send_packet: Network is down
Jul 18 20:31:15 graham-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jul 18 20:31:15 graham-desktop dhclient: send_packet: Network is down
Jul 18 20:31:28 graham-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jul 18 20:31:28 graham-desktop dhclient: send_packet: Network is down
Jul 18 20:31:41 graham-desktop dhclient: No DHCPOFFERS received.
Jul 18 20:31:41 graham-desktop dhclient: No working leases in persistent database - sleeping.

I don't understand the message , network is down.  When I reboot into XP it is working OK.

I have installed my user name and password in /etc/ppp/chap-secrets and /etc/ppp/pap-secrets as described in the help text.  

I have also installed a boot script as described in the help.

Please can anybody help?  Is my problem that I am not registering on Karoo, my ISP? If so, can anybody let me know what I am going wrong?

Many thanks.

---

### Post by coffeecat on 2006-07-19
Where you are going wrong is trying to use a piece of sub-standard hardware which is specifically designed (if that's the right word) for Windows. Granted, some people get the thing working in Linux. I did myself last year. But it ain't worth the heartache. Consider the following.

It's a USB device. USB was never intended for networking. If you've got the new 8Mbs MAX service, a USB 'modem' will cripple the speed you get. And why do you think ISPs give them away? They're cheap (and nasty), but easily configured in Windows which makes life easier on the ISP call centre help desks.

Get yourself a proper ethernet modem/router - that's my sincere advice. If you don't want wireless (and you avoid PC World :wink:) you needn't spend more than about £20-25. Google around the online stores. Ethernet is designed for networking and with an ethernet modem-router you get a built-in firewall and NAT. Get one which can be configured from a web-browser (that probably means any) and it will be indifferent to the OS you are using. And with a proper modem-router you can use more than one computer with your broadband connection at the same time.

As far as I know the **only** problem you could possibly come across is the IPv6 issue if you get one with legacy firmware. You'll be very unlucky if this happens, but it's easily fixed.

---

### Post by Sonic Alpha on 2006-07-19
Yeah, I had a similar issue.  While I won't be as harsh about it as the person above me, I will say that your best bet (and probably only avenue available) is to go for a new ADSL modem/Router.

---

### Post by coffeecat on 2006-07-19
Sorry if I sounded harsh. That wasn't my intention. In fact I can fully sympathise with the frustration you must be feeling trying to get one of  those ridiculous bits of rubbish working in Linux.

OK, I am being harsh - but only towards the Speedtouch. :D

Best of luck whatever you do.

---

### Post by Sonic Alpha on 2006-07-19
> **Sonic Alpha said:**
> Yeah, I had a similar issue.  While I won't be as harsh about it as the person above me, I will say that your best bet (and probably only avenue available) is to go for a new ADSL modem/Router.

I forgot to mention, you'll also need an ethernet port (network card) on your PC.  I hand top look for an ADSL modem myself, so hopefully, [this thread will help]("http://www.ubuntuforums.org/showthread.php?t=212516").

---

### Post by scunepo on 2006-07-19
Sorry about the delay in replying. Thank you for the advice.  I will take it and replace the Speedtouch.  Also, thanks for the link.  

On a general note, its very off-putting when you are fired up to change to Linux and you stumble at the first hurdle.  However, your speed in responding has encouraged me to continue.

Many thanks.

---

