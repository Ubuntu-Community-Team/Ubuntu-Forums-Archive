---
title: "I can't connect to the internet in Ubuntu 6.10"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by mrmonday on 2007-02-11
Hi Everyone,

I recently decided to install Ubuntu 6.10. I have never used Linux before and would like some help.

I am having problems connection to the internet. In windows, I can connect wirelessly to my WPA-PSK secured wireless network, and I can also connect via an Ethernet cable. This allows me to have access to the internet and access to shared resources such as printers and folders.

In Ubuntu I have followed instructions in the support section of the site to connect wirelessly. Ubuntu picked up two wireless cards, (I only have one, a PCI Gigabyte Technology GN-WP01GS), Which I configured with my network settings. I launched Firefox, and was unable to connect to any site, not even my routers page. Using the network tools to ping computers didn't work either. After lots of messing around using different tutorials, (and lots of entering commands in the terminal, which I still have no idea of what they do), I remember using wifi radar and ndiswrapper. Ubuntu now picks up no wireless cards.

I plugged in an Ethernet cable, and I am now able to connect to my routers page and ping any IP address I enter. Both connections still work in windows and I have no idea what to do now.

Any help would be appreciated. Thanks in advance.

---

### Post by bender5788 on 2007-02-17
do you normally use DHCP in windows if so you maybe you should try it in ubuntu the setting is in the network manager. If not what is your routers ip address because with that i can tell you the settings you need.
Also you may need to check in the networking forum because there are heaps of wireless gurus in there.

---

### Post by hatien on 2007-02-27
I'm in Viet nam. I have the same problem. in address bar of firefox browser i type http:://66.249.89.99 is OK.
But i type [www.google.com](www.google.com) wait wait... couldn't access.
I read manual. i find it have a problem about DNS, but i don't known how to solve this problem. Please somebody help me.

I'm using ubuntu 6.10, Modem D-Link DSL router DSL-504T and VNPT ISP.

---

### Post by mrmonday on 2007-02-27
In firefox type about:config, type ipv6 in the filter box then double click the only value there. can you access the internet now? can you do updates?

---

### Post by hatien on 2007-02-27
Great!
I'm replying this thread in ubuntu.

Thanks so much.

---

### Post by mrmonday on 2007-02-27
Glad I could help. Can you do updates?

---

### Post by hatien on 2007-02-28
Yes. I can't add/remove applications. 
please help me again.
Thanks

---

### Post by mrmonday on 2007-02-28
Do you know how to use a terminal?

Go to Applications>Accessories>Terminal then follow the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=282034&highlight=howto+fix+dns")

Basically you type 
```
sudo gedit /etc/dhcp3/dhclient.conf
```
and just before the request line in the dhclient.conf remove the comment (remove the # symbol) the line should read:
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```
You need to replace them with your ISPs DNS settings - they should be lying around somewhere on your ISPs site, or in the documentation you received when you signed up. If you don't know them leave them as they are to use [OpenDNS]("http://www.opendns.com/start/"). If you choose to do this you may need to edit some settings in your router. There are clear instructions on the [OpenDNS website]("http://www.opendns.com/start/").

Reboot and hopefully this will work. If you get stuck, or updates still don't work feel free to ask. Let us know how it turns out.

---

### Post by hatien on 2007-03-03
Thanks mrmonday so much!. Everything is OK.
ubuntu is very nice!

---

### Post by mrmonday on 2007-03-03
Glad to have helped :mrgreen:

---

