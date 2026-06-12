---
title: "firefox wont find server."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Chasmo on 2008-02-23
Hi This is my first post. I am new to ubuntu and am just learning to get around in it. I bought an old dell inspirion 7000 and installed ubuntu. I have managed to get it to find my network but firefox will not find server. Do you know of any simple fixes. I hope so Thanks.

---

### Post by HereInOz on 2008-02-23
Probably it is a DNS issue.

First up, open a terminal and try pinging your gateway (router/modem).  If you can do that, then you are connected to the gateway.

Then find out the IP addresses of your ISP's DNS servers, and see if you can ping them.  If you can, then you are probably experiencing a problem in the way that your modem is passing on the DNS information.  (If it is a D-Link or a Netcomm, then this is probably the case). 

To fix that problem go to System > Administration > Network  and find your active network connection.  Click on Properties and then:

1. Disable roaming mode
2. Select the option of Static IP address
3. Enter an IP address for your computer which is in the same subnet as your gateway IP (keep the first 3 sets of 3 numbers the same)
4. Enter the IP address of your gateway in the appropriate field.
5. Click OK

Then in the network dialog box, click on the DNS tab, and enter the address(es) of your ISP's DNS servers and then click close.

You then need to restart your network interface, and the easiest way for a novice is to restart the machine.

See if that helps your cause.

---

### Post by Chasmo on 2008-02-23
Thanks for the advice. It is still not working. I did notice that i have chosen WEP key Hexadecimal for password type and my router uses WPA.PSK security. I dont know if that has anything to to with it. This is a NETGEAR router wgt624 and the user name and password that I have recorded don't work when I tried to access it through firefox. 
After I made the changes you suggested and rebooted I tried firefox. still cant find server. I tried the ping. no packets sent none received. I am well and truly stuck. Do you have any other Ideas. Thanks again for your help

---

### Post by Chasmo on 2008-02-23
When I ping my router in the automatic config (DHCP)mode I get Packets transmitted 5 Packets received 0 successful packets 0%  

Then I pinged the isp server. same result. 5 packets transmited none received

after configuring manually the way you said. I ping 0 packets sent 0 packets received. Does this mean anything to you? Thanks again

---

### Post by HereInOz on 2008-02-24
If you have chosen WEP on the computer, you must have the wireless router set up the same.  If you have WPA-PSK on the router, and WEP on the computer, you will not have a wireless connection at all.

That is your problem - not that Firefox can't find the server, rather your computer is not connected to anything to start with.

Set up your wireless with no security to start with, and get a connection.  Once you have that, and all is working, set up WEP 64 bit on the router and WEP 64 bit on the computer, and see if that works.  If it does, try the next highest level of security and so on, until it ceases to work, then go back to the settings which did work.

---

### Post by Chasmo on 2008-02-24
I am very new at this. How do I choose on my computer? What I see in settings  is "Password type." there are two choices." WEP (hexadecimal)" and "WEP(ascii)" Is there another way to choose security? As I said in an earlyer post. I cant access my router for some reason. I try to log in at http:/192.168.1.1 but when it asks for user name and password it wont recognize the U/N P/W That I have recorded. I have read in other posts that there is a way to reboot your router but all info is lost and you have to imput all info again. That may be my only option, but I hate to risk losing my internet connections to my other computers. Also the icon that shows two computers in the upper right hand corner of my screen is the icon for connected. and it shows the name of my wireless connection in network settings and it pings through to my router and my isp. but nothing comes back. Where do I go from Here?

---

### Post by Mazza558 on 2008-02-24
> **Chasmo said:**
> I am very new at this. How do I choose on my computer? What I see in settings  is "Password type." there are two choices." WEP (hexadecimal)" and "WEP(ascii)" Is there another way to choose security? As I said in an earlyer post. I cant access my router for some reason. I try to log in at http:/192.168.1.1 but when it asks for user name and password it wont recognize the U/N P/W That I have recorded. I have read in other posts that there is a way to reboot your router but all info is lost and you have to imput all info again. That may be my only option, but I hate to risk losing my internet connections to my other computers. Also the icon that shows two computers in the upper right hand corner of my screen is the icon for connected. and it shows the name of my wireless connection in network settings and it pings through to my router and my isp. but nothing comes back. Where do I go from Here?

Are your user and password settings different from the default (e.g did you change them at all)? If you didn't change them, what's your router make?

---

### Post by Chasmo on 2008-02-24
I had changed them. After a long search I found what I needed and got logged on to my router and turned off security. I have retried to log on with the laptop using both static ip address and automatic configuration. still no connection. But I am starting to get hopeful!!
An hour ago I couldn't get into my router. This is a netgear wg624 router. On their web page I found another security service that they recomended to turn off so I did that too.

---

### Post by Chasmo on 2008-02-24
Thanks so much for your help. I have gotten a connection!!!!!!!!!!!! Thanks

---

