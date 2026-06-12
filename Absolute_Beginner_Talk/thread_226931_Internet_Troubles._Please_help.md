---
title: "Internet Troubles. Please help"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by knyfer on 2006-07-31
Ok, I use wireless internet and ubuntu doesnt seem to have anything to support it, and if there is it wont let me download it.  I went into the Synaptic Package Manager and searched for "Network Manager" and came up with 1 result which was already installed and it wasn't what I need anyway.  I use a Linksys wireless router which is secured with WPA, and the IP is 192.168.1.1.  When I try it "ifconfig" it shows the IP as 127.0.0.1, as an invalid IP.  If anyone can help it would be greatly appreciated.  The result I get for "network manager" is pcmcia-cs.  Installed version 3.2.8-5.2ubuntu5 and latest version 3.2.8-5.2.  I don't know exactly what card it uses as it is built into the computer, but it's an HP Media Center PC.


Also, it wont let me change screen resolution and it's stuck on 640 X 480.  If you could help with that too it would help out a lot.

Thanks. :)

---

### Post by Mike Tomasello on 2006-07-31
> **knyfer said:**
> Ok, I use wireless internet and ubuntu doesnt seem to have anything to support it, and if there is it wont let me download it.  I went into the Synaptic Package Manager and searched for "Network Manager" and came up with 1 result which was already installed and it wasn't what I need anyway.  I use a Linksys wireless router which is secured with WPA, and the IP is 192.168.1.1.  When I try it "ifconfig" it shows the IP as 127.0.0.1, as an invalid IP.  If anyone can help it would be greatly appreciated.  The result I get for "network manager" is pcmcia-cs.  Installed version 3.2.8-5.2ubuntu5 and latest version 3.2.8-5.2.  I don't know exactly what card it uses as it is built into the computer, but it's an HP Media Center PC.


Also, it wont let me change screen resolution and it's stuck on 640 X 480.  If you could help with that too it would help out a lot.

Thanks. :)
System-> Preferences-> Networking-> Wireless Networking-> "Properties" Button.

The network name I think is "linksys" on linksys routers by default? Put in the key and use DHCP and it should work, I think? (Or it does with mine).

---

### Post by knyfer on 2006-07-31
I dont have that in preferences.  I have network proxy and that's the only thing even remotely close. :(

---

### Post by knyfer on 2006-07-31
Ok, I found networking.  I have Connections, General, DNS, Hosts.  On connections it says Ethernet and Modem.

---

### Post by tehnad on 2006-07-31
If you get WPA encryption to work, PLEASE POST.  I had to change my wireless to WEP encryption because of issues with WPA authentication. I am running a Linksys wireless G router also

---

### Post by knyfer on 2006-07-31
I have that enabled on other computers.  Go to your router IP and click security, it should come up with WPA.

---

### Post by Mike Tomasello on 2006-07-31
Yeah, I'm using WEP aswell because of that. :(

On the "Connections" list I had Wireless, Ethernet and Modem when I installed Ubuntu, so I just configured it through the 'Wireless'. I'm not sure what to do since that's not there on yours, I assume that means you don't have the driver? Could try [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by tehnad on 2006-07-31
Yeah I haven't had a chance to do much research and actually lurk the forums to get a break form programming.  I need to find out why I couldn't get Ubuntu to work with WPA encryption.  Sure it isn't a hard fix, just lazy and was hoping the other poster knew a magic trick ;)

---

