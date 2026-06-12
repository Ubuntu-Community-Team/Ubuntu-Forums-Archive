---
title: "Broadband internet conectiom"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by DarkAllien on 2006-09-23
just installed Ubuntu 6.06 and can't make it conect to the net...

my internet conection details>
- i have a lan card on my computer (in windowze TCP/IP setings it is set to "Obtain ip adress automaticly...")
- and a broadband connection (PPPoE)that requires a username suplied by the ISP provider....

my question is ... How do i set it up to work in ubuntu???...it does in windowze...

---

### Post by wildseven on 2006-09-23
did u try to change the interface on the network manager?

on the top right corner of ur screen, there should be a picture of 2 computer ( like the one from windows ) and make sure the name says the right interface. On default it is lo which is loopback to make sure tcp/ip is working.

if not, do
```
ifconfig
```
then take the correct interface and do
( i will use my interface as an example )
```
sudo ifconfig eth1 up
sudo dhclient eth1
```

hopefully that works

good luck

---

### Post by DarkAllien on 2006-09-23
i have eth0 and lo .....
rand the commands with eth0....did something but still no go.....
if u can tell me the steps in order to configure the connection from A to Z...ignoring what unbutu might have set up already it would help alot...tx

---

### Post by DarkAllien on 2006-09-23
and don't have the picture of 2 comps either

---

### Post by bulldog on 2006-09-23
You have to right click a panel and choose add to panel.
Now choose network monitor and you have the icon.

Go to administration--network and it pops up a box with your connections
Choose the proper one and choose preferences,and configure it the way you want,in your case I should set it at DHCP to try out.

If it's not working,try other possibillity's like setting a IP and so on.

---

### Post by DarkAllien on 2006-09-23
^^^ no good and no permanent ip either....

---

### Post by bulldog on 2006-09-23
You get an IP from your ISP,this might change over time but you will not notice an effect,because your modem router will take care of that.

This must be all setup inside your modem router.
Things like login name and password provided by your ISP and the rest of the settings required for your ISP to provide you an internet connection.

You can setup the modem router as a DHCP and DNS server,but you should the DNS IP's setup as well in your modem,they are given to you by your provider.

When you atach a computer at your modem it will be detected and your computer gets a intern IP from the modem using the IP of the modem as the gateway and  it detects your IP given by your provider and you have an connection.

Now if there's a need to do so,you want to host a website or what ever from your home computer,you have to redirect your port to your computer and then it's handy if your computer has an IP what stay's the same and not will be changed by the modem.

This you can setup in your Linux or windows box by typing an IP within the range of your modem setting your modem IP as the gateway.

Assuming,
Your modem has an internal IP 192.168.2.1
Subnet gateway                255.255.255.0

Your computer
Intern IP by DHCP             192.168.2.3
Subnet gateway                255.255.255.0
Gateway                       192.168.2.1

But if there are more computers at the modem your IP can switch and by setting an IP by yourself it stays the same.

But as said you have to setup your modem router first to connect to the internet,by the given info from your ISP.

---

### Post by DarkAllien on 2006-09-25
got the eth0 in administration networking to dhcp
and with sudo pppoeconf configured the pppoe and still it does not work

here are the links from the ISP about configuring in windows
just watch for the bolded text (is in english)...

[http://www.rdslink.ro/fiber/fiber_support.htm](http://www.rdslink.ro/fiber/fiber_support.htm)
[http://www.rdslink.ro/fiber/fiber_support_conectarea.htm](http://www.rdslink.ro/fiber/fiber_support_conectarea.htm)

the isp just gave me a username for the pppoe and that's it...
please help

---

