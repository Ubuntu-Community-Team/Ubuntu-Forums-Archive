---
title: "Wireless Connection using D-Link and Netgear"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Benji Black Eyes on 2007-02-14
Hi. Installed Ubuntu two days ago, installed a Netgear 108Mbps wireless PCI network adapter, and I am trying to connect to my D-Link DI524 wireless router. No problems on the hardware front; from the looks of it, Ubuntu recognized the PCI card straight up. I have tried changing numerous settings yet can not get DHCP to work. It's becoming quite annoying. I am accessing the 'net via the wireless router over this XP-based laptop, so that end is fine.

---

### Post by IronMac on 2007-02-14
There's a poster here named Derryk who's been having wireless problems too over the last day. Look at his **two** threads to see if any of the advice there will help you.

Please be a bit more specific too as to what your difficulty is.  :)

---

### Post by Benji Black Eyes on 2007-02-14
IronMac; no more than a minute after my post I saw his thread :/

Sorry! I read yours and others' responses to his problems. Nothing of any real help. My problem is a network settings one I feel. DHCP is meant to automatically assign my computer an IP address upon wireless connection right? 

If you or someone else could tell me exactly what I should have in each field in the "Properties" box (which I am accessing via clicking on my wireless adaptor in the 
"Network Settings" dialog box), that would be fantastic. It's about 4 years since my last (and rather fruitless) daliance with Linux and apart from lack of connectivity, I am loving the Ubuntu interface and easy of use.

---

### Post by IronMac on 2007-02-14
> **Benji Black Eyes said:**
> IronMac; no more than a minute after my post I saw his thread :/

Sorry! I read yours and others' responses to his problems. Nothing of any real help. My problem is a network settings one I feel. DHCP is meant to automatically assign my computer an IP address upon wireless connection right? 

If you or someone else could tell me exactly what I should have in each field in the "Properties" box (which I am accessing via clicking on my wireless adaptor in the 
"Network Settings" dialog box), that would be fantastic. It's about 4 years since my last (and rather fruitless) daliance with Linux and apart from lack of connectivity, I am loving the Ubuntu interface and easy of use.

BBE, you're right when you say that DHCP is supposed to automatically assign your computer with an IP. I was also in your shoes a week ago when the deal-breaker with Ubuntu was the lack of connectivity.

First off, you may want to try running your wireless router wide open and seeing if you have a connection then. If that works, then, you should try securiing your router with WEP (go on to WPA afterwards but I have no clue on that).
Set your wireless router to WEP, then, go to your Network settings. Find your connection (mine is Device: eth0) and click the enable this connection box.
Select your ESSID in the next box down. Hopefully, your wireless card will be able to detect this.
Key Type is Hexadecimal.
WEP key (this is the tricky part) is something that I found in my Linksys router. Selecting WEP there and entering the passphrase will generate four different WEP keys and I used the first one to enter into the WEP key box.
Configuration is DHCP and the others are left alone.

You may want to log off and on after making these changes to make sure that they "stick".

---

### Post by MicheleZ on 2007-02-14
Hello BBE,

I have the same wireless router and a very similar problem.
under WinXP my compaq WLAN card and D-Link router work fine, but when booting up in ubuntu, after a few minutes I stop receiving packets. If I disconnect then I cannot get an IP address anymore, and actually it stops working also under WinXP.
I had to reset the wireless router and re-enter the configuration (fortunately you can save the configuration in a file and load it).

Disabling the WEP mitigates somewhat the problem, but you really don't want to do that!
If I find a solution I will let you know.

Cheers,

Michele

---

### Post by matheuu on 2007-02-14
Hey Mate,
Had similar probs with a d-link, ubuntu and a belkin card.
I had a xp laptop running, got the connection, WEP, mask, IP addresses and DNS address off the laptop via the routers ip address. Then copied them into the ubuntu wireless network thing..

something like that.
Think the router ip could be 192.168.0.1  ??? if you type that in the laptops browser.... the password/login is probably admin/admin ....maybe

might want to check the ip on the d-link site if it doesnt work.

Cheers
Mat

---

### Post by MicheleZ on 2007-02-14
Hi Matheuu,

You are correct: the web interface to configure the router can be accessed at 192.168.0.1, user name admin password <void>. 
After a full reset (press for 5seconds the reset button next to the power supply) the ESSID is default (all small caps), the WLAN is open (no WEP, WPA etc...).
The DHCP (on by default) assigns addresses in the range 192.168.0.100/255 to be renewed every 24 hours (IIRC)

Got that bits, still after a while the router decides it does not like my WLAN anymore and stops talking to it.

Cheers,

Michele

---

