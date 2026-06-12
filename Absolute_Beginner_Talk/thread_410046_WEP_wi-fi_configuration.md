---
title: "WEP wi-fi configuration"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by surfwizz on 2007-04-15
I am trying to configure the wireless networking settings in 7.04, but I don't know enough about wi-fi networking to figure out how to correctly fill out the fields.  I have a Verizon FIOS router configured with default WEP settings.  Does anyone have one of these who can tell me how to fill in the fields?
Thanks!

---

### Post by Bachstelze on 2007-04-15
For a WEP encrypted network, you usuall just need to fill in the ESSID and the key. I use the command line for this so I'm afraid I can't tell you exactly what to do in the GUI.

---

### Post by Fascination on 2007-04-15
If you're the only machine on the network, try setting your IP to 192.168.0.100, the sub to 255.255.255.0 and set the default gateway (and dns) to 192.168.0.2. I believe if you havent changed from the defaults on the router then there will be no WEP key set up.
Ideally, you want to log into [http://192.168.0.2](http://192.168.0.2) (your router) and set up some form of security; [http://aplawrence.com/Reviews/verizon_fios.html](http://aplawrence.com/Reviews/verizon_fios.html) contains some good advice, and coupled with the user manual you should be fine. :)

---

### Post by n3tfury on 2007-04-15
> **Fascination said:**
> If you're the only machine on the network, try setting your IP to 192.168.0.100, the sub to 255.255.255.0 and set the default gateway (and dns) to 192.168.0.2. I believe if you havent changed from the defaults on the router then there will be no WEP key set up.
Ideally, you want to log into [http://192.168.0.2](http://192.168.0.2) (your router) and set up some form of security; [http://aplawrence.com/Reviews/verizon_fios.html](http://aplawrence.com/Reviews/verizon_fios.html) contains some good advice, and coupled with the user manual you should be fine. :)

the gateway address should be 192.168.0.1 or 192.168.1.1 depending on manufacturer.

---

### Post by Fascination on 2007-04-15
> **n3tfury said:**
> the gateway address should be 192.168.0.1 or 192.168.1.1 depending on manufacturer.

I was just going by what I was reading on the support foras I checked. :)
Incidently, mine is 192.168.2.1 - those IPs you mention arent a surefire way to know each manufacturers default IP choice. :)

---

### Post by surfwizz on 2007-04-15
The router configuration includes a password, but I'm not sure about the other settings, like the passphrase encryption.  I am not the only system on the network, nor the configuration machine.  Also, I've tried entering everything into the network setup assistant, but it's not connecting.

---

### Post by n3tfury on 2007-04-15
> **Fascination said:**
> I was just going by what I was reading on the support foras I checked. :)
Incidently, mine is 192.168.2.1 - those IPs you mention arent a surefire way to know each manufacturers default IP choice. :)

from your link:

> The router is a D-Link AirPlus Extreme G (DI-624). At defaults, it has an address of 192.168.0.1 and hands out DHCP addresses starting at 100

that's the default.  

most of the big manufacturers use what i mentioned.

---

### Post by n3tfury on 2007-04-15
> **surfwizz said:**
> The router configuration includes a password, but I'm not sure about the other settings, like the passphrase encryption.  I am not the only system on the network, nor the configuration machine.  Also, I've tried entering everything into the network setup assistant, but it's not connecting.

sounds like you need to contact whoever administers that network to get the information you need.

---

### Post by surfwizz on 2007-04-15
I have the password and SSID, but I don't know what the Verizon FIOS router's default security settings for WEP are.  The router is an Actiontec M1424WR.

---

### Post by Fascination on 2007-04-15
> **n3tfury said:**
> that's the default.

Hmm, mis-read it with the IP it later mentions to access the router.

> **n3tfury said:**
> **most** of the big manufacturers use what i mentioned.

Its still folly to say thats **the** two ips to use; as you said yourself, 'most'.

---

### Post by n3tfury on 2007-04-15
> **Fascination said:**
> 



Its still folly to say thats **the** two ips to use; as you said yourself, 'most'.

yep, shoulda said most in the first post.

---

### Post by Fascination on 2007-04-15
> **n3tfury said:**
> yep, shoulda said most in the first post.

Yes, well, Ill forgive you this once - cant be easy to concentrate with a burning paper bag on your head. ;)

---

### Post by n3tfury on 2007-04-15
> **surfwizz said:**
> I have the password and SSID, but I don't know what the Verizon FIOS router's default security settings for WEP are.  The router is an Actiontec M1424WR.

i'm not sure what you mean here.  you have the password as in the WEP key?  or the password to access the router via telnet or a browser?

---

### Post by n3tfury on 2007-04-15
> **Fascination said:**
> Yes, well, Ill forgive you this once - cant be easy to concentrate with a burning paper bag on your head. ;)

that was a long time ago.  i've since switched paper.

---

### Post by TheWizzard on 2007-04-15
> **Fascination said:**
> If you're the only machine on the network, try setting your IP to 192.168.0.100, the sub to 255.255.255.0 and set the default gateway (and dns) to 192.168.0.2. I believe if you havent changed from the defaults on the router then there will be no WEP key set up.
Ideally, you want to log into [http://192.168.0.2](http://192.168.0.2) (your router) and set up some form of security; [http://aplawrence.com/Reviews/verizon_fios.html](http://aplawrence.com/Reviews/verizon_fios.html) contains some good advice, and coupled with the user manual you should be fine. :)

i disagree. it is much easier to have dynamic ip.

you can change the setting using a gui. in kde 'system settings' -> 'network settings'
the settings are stored in /etc/network/interfaces 
you can change these settings with a text editor like nano. 
```
sudo nano -B /etc/network/interfaces 
```

it should look like:

```
auto eth1
iface eth1 inet dhcp
wireless-essid XXXXXXX
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXXX
```

---

### Post by Fascination on 2007-04-15
But isnt dynamic a pain if you then go on to set up MAC address filtering and so on?

---

### Post by n3tfury on 2007-04-15
> **Fascination said:**
> But isnt dynamic a pain if you then go on to set up MAC address filtering and so on?

mac address filtering is, unfortunately, extremely easy to spoof.  it's easier and more bulletproof to set up for dhcp and WPA/WPA2 encryption.

---

### Post by Fascination on 2007-04-15
> **n3tfury said:**
> mac address filtering is, unfortunately, extremely easy to spoof.  it's easier and more bulletproof to set up for dhcp and WPA/WPA2 encryption.

Considering the issues the user is having at the moment, isnt WPA a bit far off for now? Where as MAC address filtering is an easily clickable option in the GUI for the router in question.

---

### Post by n3tfury on 2007-04-15
> **Fascination said:**
> Considering the issues the user is having at the moment, isnt WPA a bit far off for now? Where as MAC address filtering is an easily clickable option in the GUI for the router in question.

perhaps, but both WEP and mac address filtering are both poor security "features".  there's a fine line between convenience and a secure network.

---

### Post by TheWizzard on 2007-04-15
> **n3tfury said:**
> perhaps, but both WEP and mac address filtering are both poor security "features".  there's a fine line between convenience and a secure network.

as far as i know wep and mac filtering go well together with dynamic ip. i'm using that at the moment. 

as for security: wep and mac filtering are easy to crack. but is that a problem? 
depends on the pupose of your network. if you want to be super secure, don't use wifi. 

you can also crack wpa. see [http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks#Differences](http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks#Differences)

---

### Post by n3tfury on 2007-04-15
> **TheWizzard said:**
> as far as i know wep and mac filtering go well together with dynamic ip. i'm using that at the moment. 

as for security: wep and mac filtering are easy to crack. but is that a problem? 
depends on the pupose of your network. if you want to be super secure, don't use wifi. 

you can also crack wpa. see [http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks#Differences](http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks#Differences)

/sarcasm  thanks for that  /sarcasm, but i never said that WPA cannot be cracked.  the only way a box is totally secure is unplugged and in a warehouse somewhere.  Cracking a WEP key can be done in a matter of minutes and mac spoofing a matter of seconds.  i fully understand that under most linux distros that using WPA/WPA2 is certainly harder to configure unfortunatel, but they are inherently more secure.

---

