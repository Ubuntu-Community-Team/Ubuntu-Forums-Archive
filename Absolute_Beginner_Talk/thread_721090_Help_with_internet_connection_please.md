---
title: "Help with internet connection please"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by crusader1968 on 2008-03-11
I just installed ubuntu today, that went fine I put it on an older computer, making the second hard drive all for ubuntu no problems there.

I am having problems with connecting to the internet using a wired connection, works fine when I boot to windows xp but nothing when I boot to ubuntu.

System 
AMD 3000 + 
Gigabyte motherboard GA-7VT600(on board realtek RTL8139/810x Family Fast Ethernet NIC)
1 gig ram
nvidia geforce 6200
Cable Modem / Router Microsoft MN700 

I have tried both manual and enable roaming mode.
Under connection active  information it shows speed 100 Mb/s / driver 8139too and everything at 0.0.0.0 below that minus the hardware address.

Can anyone help?

Thanks :)

---

### Post by dokdoom on 2008-03-11
What is between your new ubuntu computer and the internet? Or, if you are able to get dhcp. Test by running this on your command line. 

sudo dhclient

When it's done notice if at the end you see you were given an IP address. 
Test by pinging 4.2.2.1 then google.com.

If both pings reply you can edit your /etc/network/interfaces file to grab an address when booting.

---

### Post by crusader1968 on 2008-03-11
Thanks! But no luck with that.:(

I put in sudo dhclient in the terminal command line
it said in the end that
No DHCPOFFERS received.
No working leases in persistent database - sleeping

what type of manual config could I do? 

Thanks again for any help

---

### Post by aashay on 2008-03-11
If someone else had setup the networking for you, you could try copying the settings (IP, subnet, dns, etc) from windows xp into ubuntu

---

### Post by bharadwaj on 2008-03-11
[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html) 
this would help you out ii guess...

---

