---
title: "Yet another internet\wireless network problem"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by VJ42 on 2005-11-13
OK, Ubuntu seems to be picking up my home (Windows) network:
[[IMG]http://img323.imageshack.us/img323/8162/screenshot9vi.th.png[/IMG]](http://img323.imageshack.us/my.php?image=screenshot9vi.png),
[[IMG]http://img337.imageshack.us/img337/1492/screenshot24ma.th.png[/IMG]](http://img337.imageshack.us/my.php?image=screenshot24ma.png)
[[IMG]http://img318.imageshack.us/img318/5792/screenshot11wv.th.png[/IMG]](http://img318.imageshack.us/my.php?image=screenshot11wv.png)

Yet I can't connect to the internet via my wireless card (D-Link DWL-120) and router (D-Link DWL 604+). What am I doing wrong??

Hardware Config:
AMD Athalon 64
3000+
512Mg RAM

---

### Post by chazzjazz on 2005-11-13
you got the WEP key for the router ?? :D

---

### Post by VJ42 on 2005-11-13
[QUOTE=chazzjazz]you got the WEP key for the router ?? :D[/QUOTE]
It's a 10 digit number that begins with 6 and ends in 9:p ; I have it blu-tacked to my monitor:D (I think it's pointless, but my Dad's a bit paranoid, and thought somone was trying to 'borrow' our net connection)

---

### Post by chazzjazz on 2005-11-13
well if that doesnt work i pass you over to the experts ;)

---

### Post by endersshadow on 2005-11-13
Did you allow the connection on the router?  I know some routers make you okay every computer that connects.

---

### Post by VJ42 on 2005-11-13
[QUOTE=endersshadow]Did you allow the connection on the router?  I know some routers make you okay every computer that connects.[/QUOTE]
Our router dosn't, however it's occoured to me that it might be somthing to do with the IP address, a similar thing happened on my brothers windows box, for some reason it was seeing the network, but not connecting, IIRC it was getting an IP outside the range allowed to connect to the net, How do I check my IP address from within UBUNTU?:)

---

### Post by majed on 2005-11-13
why don't u specify an IP address and key in your gateway manually. I'm doing this and its working fine with me..

and for ur IP address.. in a terminal, run this command:

```
sudo ifconfig -a
```

---

### Post by Dr. Nick on 2005-11-13
I dont use the gui to configure mine, but I dont think you can use the wep passphrase, which is the 10 digit key most likely. I had to input the HEX value into mine which is 26 digits into the /etc/network/interfaces file. This key is stored in the router. Is it a 64 or 128 bit wep? 64bit is 10 digits which in that case set ASCII to HEX in the menu

---

### Post by chazzjazz on 2005-11-13
i have the 604+ nice adsl and router....i use the 26 digit hex, or you can use the string with it....

in any case if your windows boxes are working then dont mess with the wwep key

All you need is specifiy the SSID and WEP....you havent mentioned SSID yet..its defaults to you guess it "default" in windows...

dunno about ubuntu

---

### Post by Dr. Nick on 2005-11-13
If you believe all is set up correctly including the wep then open a terminal and run "sudo dhclient wlan0" to try to get an IP

---

### Post by VJ42 on 2005-11-14
[QUOTE=chazzjazz]i have the 604+ nice adsl and router....i use the 26 digit hex, or you can use the string with it....

in any case if your windows boxes are working then dont mess with the wwep key

All you need is specifiy the SSID and WEP....you havent mentioned SSID yet..its defaults to you guess it "default" in windows...

dunno about ubuntu[/QUOTE]
Actually, we've changed it (again due to my dad's paranoia), it's set to "Yellowstone", and I've set it to that via the GUI in Ubuntu, aswell as setting the WEP to the same 10 digit number that Windows uses. :) 

 thanks for the advice though, and the same goes for everyone else; I havn't tried all the proposed solutions yet*, but I'm sure one of them will work

*Timezone problem, I live in the UK, so I'm reading this thread on Monday morning at Uni, so can't try them untill this evening GMT:p

---

