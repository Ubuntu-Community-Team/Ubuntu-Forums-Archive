---
title: "Problem connecting to internet"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Ic3y on 2007-01-17
](*,) 

Hi i just freshly installed ubuntu today with desktop 6.10 edgy I am having problems connecting to the internet I tried contecting on both the LiveCd and also when I installed ubuntu and had no luck either way I have two NIC/LAN cards and tried both of them without any luck.

I have gone into networking and configured them manually and still had no luck.

I can connect to other computers on the network as well so there is no problem there just the problem of connecting to the internet.

Can anyone who may know how to fix this that would be greatly appreciated thanks

---

### Post by Ic3y on 2007-01-17
For all those who viewed this I solved the problem that I had with my connection
I currently have a D-Link ADSL/Router and what I found was that Ubuntu 6.10 Edgy does not support IPv6 which is fortunately on the modem, so I was able to disable it through the following means and got the connection to work.

Here is my solution that I found:

[LIST]Open Firefox and in the URL type 'about:config' without the ' '
[/LIST]
[LIST]In the filter type in 'IPv6' again without the ' '
[/LIST]
[LIST]Then you should see a line that says 'network.dns.disableIPv6' the value will state false double click it to make the value true
[/LIST]
[LIST]Once this is done close the browser re-open it and all should be working
[/LIST]

Regards
Ic3y :mrgreen:

---

