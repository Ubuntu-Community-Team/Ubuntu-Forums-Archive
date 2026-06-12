---
title: "Connected to wireless, but nothing works."
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Amablue on 2007-01-04
I connect to my wireless router, type the WEP correctly, and it shows that it's connected, but I can't get FireFox (or any other application that needs the internet) to connect.

---

### Post by meng on 2007-01-04
Try opening a terminal, then:
sudo dhclient eth1
(enter your user password when prompted, then press Enter)

---

### Post by loyaleagle on 2007-01-04
I am a newbie and had the same problem after I installed Ubuntu.
I went to administration menu and clicked on networking.
I unchecked the wireless radio button. I then made sure my network key was correct and rechecked the wireless radio button. All has been well since then.
it connects every time. ( make sure that under connection settings all is correct, especially DHCP)

Thanks, Loyaleagle

---

### Post by rbhigday on 2007-01-04
The photo showed a lan line as connected and not a wireless.

---

### Post by jimrz on 2007-01-04
> **rbhigday said:**
> The photo showed a lan line as connected and not a wireless.

you might check in "Networking" and make sure that you have the correct DNS server info in the "DNS" tab

---

### Post by Amablue on 2007-01-04
> **meng said:**
> Try opening a terminal, then:
sudo dhclient eth1
(enter your user password when prompted, then press Enter)

This is what I get:

```
Listening on LPF/eth1/00:90:4b:d7:d8:55
Sending on   LPF/eth1/00:90:4b:d7:d8:55
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

But it still doesn't work. 

> **jimrz said:**
> you might check in "Networking" and make sure that you have the correct DNS server info in the "DNS" tab

Are you talking about the fact that it says eth1? It's been like that for as long as I've used wireless on my laptop. 

> **jimrz said:**
> you might check in "Networking" and make sure that you have the correct DNS server info in the "DNS" tab

How do I know if it's correct? 

---

I can't think of why it would have stopped working all of the sudden. I havn't made any changes, though I did install the wifi-radar package recently so I could see other local wireless routers. Could that have done it? I've since uninstalled it, but it doesn't make a difference.

---

### Post by SendDerek on 2007-01-04
NetworkManager has always made my wireless life very easy.  I would recommend installing that.  

Otherwise, as far as troubleshooting, you should probably see if you can ping out to places like google.com or yahoo.com.  If you can do that, then it's a problem with DNS.  I know that Qwest services don't really like Linux machines for some reason. lol.

---

### Post by rbhigday on 2007-01-05
eth1 is a cabled network connection, it is not wireless

You should be entering something like wlan0 for a wireless connections

try

sudo dhclient wlan0

Also sometimes you have to ensure all encryption is off to get initial connection then reinstall encryption after you have a solid connection.

---

### Post by rbhigday on 2007-01-05
Try running ifconfig to see what shows up as your wireless connection.
Then use that instead of eth1

---

### Post by jimrz on 2007-01-06
> **Amablue said:**
> This is what I get:

```
Listening on LPF/eth1/00:90:4b:d7:d8:55
Sending on   LPF/eth1/00:90:4b:d7:d8:55
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

But it still doesn't work. 



Are you talking about the fact that it says eth1? It's been like that for as long as I've used wireless on my laptop. 



How do I know if it's correct? 

---

I can't think of why it would have stopped working all of the sudden. I havn't made any changes, though I did install the wifi-radar package recently so I could see other local wireless routers. Could that have done it? I've since uninstalled it, but it doesn't make a difference.

1- no, "eth1" is probably correct ... "eth0" is likley your wired connection ... + your screen shot shows wireless signal strength. Go to System > Administration > Networking (not the network icon on your panel) and select the DNS tab to see what servers it is looking at. Have seen several threads here where people had issues because proper dns for them was not retained. In some cases it was replaced by something like 192.168.0.1 + 255.x.x.x. I have not had this issue, but anytime i run a live cd on my laptop i always have to go manually input the correct info in order to get to the web.

2- the correct dns settings should be available from your isp, or if you have other boxes connected through your router you can go in one of them, see what it is using and enter the same on your laptop.

---

### Post by Amablue on 2007-01-06
Okay, I got it to work, but I don't know exactly what I did. Wireless seems kinda spotty on this laptop overall, but that's probably due in part to the Broadcom chipset I have which I understand is fickle to begin with (I had a hell of a time setting it up in the first place). 

What happens now is that it'll connect, but after a while it'll just drop out. I don't know if it just happens after being on for a certain period of time, or a certain amount of time being idle or what. I just know that the last couple of times I've left my computer on while I do other stuff, when I come back the internet isn't working despite still showing a connection. 

I'll check the DNS settings anyway when I get back to my laptop.

---

### Post by ajmorris on 2007-01-06
correct me if i'm wrong (and i probably am... lol)

Shouldn't it be "dhclient wlan0"

And in the screenshot where it says "eth1 idle" have you tried changing that to wlan0 and seeing what it does? Becuase when i use wireless mine in wlan0.

---

### Post by Amablue on 2007-01-06
Whenever I change it to wlan0 or wlan1 or anything wlan, it doesn't work. It just says "error"

---

