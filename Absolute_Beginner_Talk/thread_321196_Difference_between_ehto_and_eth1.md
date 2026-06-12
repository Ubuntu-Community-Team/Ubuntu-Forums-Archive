---
title: "Difference between ehto and eth1"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-18
Guys , i am looking at the networking file "/etc/network/interfaces" . I see entries for eth0 and eth1 . I am going to change the IP address of my ubuntu

Can some one tell me which entry should i be looking to modify

---

### Post by benuski on 2006-12-18
Well, eth0 is typicall your wired connection, while eth1 is usually your wireless connection.  So change the one you need.  But you can also do the same thing graphically in the System=>Administration=>Networking box.  Just click on your connection, then on properties.

---

### Post by greyhill on 2006-12-18
If you're on a laptop, eth0 is probably your ethernet device.  eth1 is your wireless device.  If you're using GNOME, I'd reccommend using System->Administration->Networking to configure your network as you can see specifically which device is which, and it allows you to set up static IP addresses.

---

### Post by lance_klusener on 2006-12-18
I have manually modified the file and have made the eht1 as the static Ip . The machine appears to be pingable from other machines on the network ,

Should i reconfigure the static IP back to eth0 or should i let the thing which is working remain as it is 

Thanks for your response

---

### Post by lucky_chouhan on 2006-12-18
my system is - 
eth0 is my Realtek 
eth1 is my ADSL modem

eth0 - 192.168.0.11
eth1 - 192.168.1.1

then adsl work fine as well as network.

---

### Post by greyhill on 2006-12-18
I'm not sure exactly what you want to do.  Most of the time, it's a good idea to leave the wireless device on DHCP so you can connect to public wireless access points.  Are you trying to bridge a connection or something like that?  Will both devices be connected to the same network?

---

### Post by lance_klusener on 2006-12-18
This mahcine that i am talking about isnt a laptop so i dont know wheter i have done any wrong .

b.t.w . can we have two different static IP addresses on eth0 and eth1

---

### Post by greyhill on 2006-12-18
Okay, cool.  Yeah, you can have two different static IP addresses for eth0 and eth1.  Make sure you're getting your DNS/gateway configuration without DHCP! :)

---

### Post by lance_klusener on 2006-12-18
yes that was just for my own know-how . I dont have another static address in spare. But i dont know what use does one have in having 2 different ip addresses for the same machine . can u tell me some application ??

---

### Post by greyhill on 2006-12-18
I can't think of a good reason why you'd want two ip addresses for the same machine on the same network, but I'm sure there are some.

However, if you'd set up your machine as a bridge between two networks, it certainly makes sense to have two different ip addresses, though they'll sit on different networks.  This is handy if you want to run your own firewall for your network, access points, or something along those lines.

---

### Post by zgornel on 2006-12-18
> **greyhill said:**
> I can't think of a good reason why you'd want two ip addresses for the same machine on the same network, but I'm sure there are some.
 You are running a ftp/web server on one interface (ip address) and the other one is used for normal local/internet usage. You can also create aliases (multiple ip adresses for the same physical device) for the same reason.

---

### Post by majalee on 2006-12-29
I liked Ubuntu 6.10 and was trying to configure a dual ethernet interface.. i am able to configure only one static address at a single time.. when i try to setup the second interface, it works and then the initial one is disabled.
i tried to setup 'eth0' for internet connection and 'eth1' for the internal LAN.. 

i tried to write down in the /etc/network/interfaces file..but only one ip is working.. one static address is used for internal usage of the computers in our office.. the second interface is used to connect to the internet..

i have setup this dual interface in redhat 9.0 in my system.. but i am not able to configure it in Ubuntu 6.10.. 

please help..

thanks in advance..

regards,
majalee

---

