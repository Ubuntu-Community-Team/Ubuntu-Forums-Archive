---
title: "IPW 2200 not working out of the box with feisty"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by kbarron on 2007-04-28
I am using Ubuntu for the first time and have no linux experience. I just got a new HD and decided to do away with windows are start with Ubuntu from scratch.

I cant get my wireless connection to work. The wired is working but I cant locate any wireless networks. I have read over the threads but havent been able to figure things out.

I have an Intel IPW2200 which is pretty standard. I had played around with the live CD of Edgy before and it was able to locate the network

but now that I did a full install of Fiesty I cant figure things out.

any help or directions or links would be appreciated. I really need this thing to get working.

thanks

---

### Post by gerrymoth on 2007-05-02
I've got the same problem.

I initially started with the Feisty Beta and wireless work straight away, but over the weekend I couldn't access any networks and had to do a re-install, so I had downloaded the official 7.04 CD and installed this.

Network Manager can see all the available network, but will either not connect to them, doesn't like the password or I think its connected, but no internet access.

I've eventually turned network manager off and I'm inputting the SSID, Password, IP Address, gateway, etc.. via the Sysytem/Administrator/Network with roaming not enabled.

Thought I'd at least got internet access, but most sites I go into just seem to be slow or will not open.
Also Gaim will access AIM, but not MSN and Amarok freezes when playing Last.fm streams.

I've enjoyed using ubuntu or the last few months, but I'm spending more time having to sort problems with it at the moment rather than just using it.

---

### Post by Rhesuso on 2007-05-10
That is really odd. With Network Manager (NM) enabled by default in Feisty, the ipw2200 adaptor should really just work. It does for me (It did in Edgy too, once I'd installed network manager).

Let's see, in System -> Administration -> Network, your wireless connection should be set to 'Roaming Mode Enabled'.
When you click on the network manager applet to create a wireless network, that should be pretty easy to fill in the dialog. Re-check that you're entering the details as are set on your Access Point(AP). I use WPA Personal security, and the encryption type is TKIP, but there is also the choice of AES. I think TKIP is the most common one to use but maybe you've set up your AP differently. Setting encryption type to Automatic might work, but I haven't tried it, and it's probably better to set it to what you know you're using.

Unfortunately with NM, you can't assign a static IP address to your adapter (I've recently discovered). It has to use DHCP, so make sure your AP offers a DHCP server and that it's enabled. If you can't run DHCP, you'll need to get rid of NM, and configure your static IP in System -> Administration -> Network, and use wpa_supplicant to provide WPA encryption (you really should use WPA rather than WEP). It's not hard to set up, search here on the forum for a guide, & I'll try to find the guide I used and post the link here.

@kbarron
If you can see your surrounding wireless networks under windows, but not linux, maybe your adapter is switched off. Run iwconfig or ifconfig in a terminal, and also in a terminal:

```
dmesg | grep ipw2200
```

to see if that provides a clue. I know on my laptop, when the wi-fi is switched off in windows and I reboot to ubuntu the adapter is still off, and I can't get it back on without rebooting and enabling it in windows again. There may be a fix for this, but it's not a priority for me right now so I just work around it for the moment.

I hope you get it working, it's pretty essential to have a net connection. On the plus side, when you do get it working, I've found wireless reception under linux to be much better than in windows (with no detrimental effect on the battery life of my laptop).

---

