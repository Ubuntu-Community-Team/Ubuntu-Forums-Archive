---
title: "Wi-Fi connection keeps dropping"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by drunkardivan on 2008-02-18
This is probably something really simple, and I'm just missing the right command. I'm running Gutsy, fresh install on a new Vaio laptop, and any time I leave the system idle for more than a few minutes, my wireless connection drops. Network manager will still be running, but it will not show any wireless networks (mine, or my neighbors' unsecured ones). The only way I have found to get back online is to reboot. 

Any suggestions would be greatly appreciated.

---

### Post by randy78 on 2008-02-18
> **drunkardivan said:**
> This is probably something really simple, and I'm just missing the right command. I'm running Gutsy, fresh install on a new Vaio laptop, and any time I leave the system idle for more than a few minutes, my wireless connection drops. Network manager will still be running, but it will not show any wireless networks (mine, or my neighbors' unsecured ones). The only way I have found to get back online is to reboot. 

Any suggestions would be greatly appreciated.

If Roaming Mode is enabled in Network Manager, try disabling it and either setting a Static IP Address or Setting DHCP.

---

### Post by drunkardivan on 2008-02-18
Hmm... lost my connection right after posting, restarted, downloaded the updates, and it appears to have solved the issue. Thanks, though, Randy78. Once I finally get settled in, I may go with a static address.

---

### Post by randy78 on 2008-02-18
Sounds good...

Setting a static IP is a good idea if you have several computers that will be sharing the wireless connection, as it designates a specific address to that computer.
It can get chaotic using DHCP if more than one device is trying to use the connection, as the router might assign an identical IP address to another device, which can cause conflicts.

---

### Post by stchman on 2008-02-18
> **randy78 said:**
> If Roaming Mode is enabled in Network Manager, try disabling it and either setting a Static IP Address or Setting DHCP.

Network Manager does not support static IPs with wireless running encryption from what I see.

---

### Post by randy78 on 2008-02-18
> **stchman said:**
> Network Manager does not support static IPs with wireless running encryption from what I see.

It does here at my house ;)

I'm using WEP, and I have used WPA as well without any issues...

---

### Post by stchman on 2008-02-18
> **randy78 said:**
> It does here at my house ;)

I'm using WEP, and I have used WPA as well without any issues...

Can you please detail how to do this.  I have tried and come to the conclusion that NM does not do Static IPs.

Thanks.

---

### Post by randy78 on 2008-02-18
Okay...
First, in a terminal, do this:
cat /etc/network/interfaces
And note the IP Address.

In Network Manager, select your wireless connection and then properties

Disable Roaming Mode

Then, in the drop down box, select the wireless network that you will be connecting to.
Enter the network password and encryption type
In the next drop down box (Configuration), select Static IP

Type in the IP address obtained earlier and enter it into the box next to IP Address
Subnet should auto-fill
I have my Gateway set to 192.168.1.1 (yours may differ)

After that, just close out and it should reset itself with your new static IP...
The problem with this is, is that DHCP can still assign your static IP to anybody else who is using the wireless, if they aren't using a static IP as well, and that can cause problems with Internet access, kind of like two people trying to drive the same car.

---

### Post by stchman on 2008-02-18
> **randy78 said:**
> Okay...
First, in a terminal, do this:
cat /etc/network/interfaces
And note the IP Address.

In Network Manager, select your wireless connection and then properties

Disable Roaming Mode

Then, in the drop down box, select the wireless network that you will be connecting to.
Enter the network password and encryption type
In the next drop down box (Configuration), select Static IP

Type in the IP address obtained earlier and enter it into the box next to IP Address
Subnet should auto-fill
I have my Gateway set to 192.168.1.1 (yours may differ)

After that, just close out and it should reset itself with your new static IP...
The problem with this is, is that DHCP can still assign your static IP to anybody else who is using the wireless, if they aren't using a static IP as well, and that can cause problems with Internet access, kind of like two people trying to drive the same car.

That only works for unencrypted and WEP.  I use WPA2.

---

### Post by randy78 on 2008-02-18
It works for my WPA-PSK as well...

I don't know why you are having those problems, but I'd be glad to help if you want :D

Also, do a Google search for "ubuntu wpa2 7.10"

---

