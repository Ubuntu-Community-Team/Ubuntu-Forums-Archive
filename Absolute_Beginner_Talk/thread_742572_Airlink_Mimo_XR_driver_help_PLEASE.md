---
title: "Airlink Mimo XR driver help PLEASE"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by darkfire9 on 2008-04-01
Hey, im a complete newbie to linux, i just installed ubuntu and have dual partition with windows xp. I'm having a problem with my airlink MIMO XR AWLH5025. When I log on, it sees my network, and it requested the WEP key like a dozen times, finally it seemed to accept it, but it never actually connected to my network; it doesnt even say it is searching for an ip address, just that it simply has a 0% connection.

If i go into the network manager thing and try to set it up manually, it doesnt give my network name as an option. when i looked under hardware information, it rocgnized the product completely, listed basically all the details. 

If anybody can help please do.

---

### Post by Matthewslf on 2008-04-01
Just checking, there is no SSID or ESSID option?

---

### Post by mick8985 on 2008-04-01
Could you type lspci into a terminal and paste the output please?

---

### Post by darkfire9 on 2008-04-02
> **mick8985 said:**
> Could you type lspci into a terminal and paste the output please?

the response for the lspci that dealt with my card was
"00:0a.0 Network controller: RaLink RT2600 802.11 MIMO"
hopefully thats what you needed, i can post the entire response if you need that.

> **Matthewslf said:**
> Just checking, there is no SSID or ESSID option?

and it recognizes that the networks when i click on the app in the tray, but if i try to manually insert all the network info the network name should be in the drop down menu, but its blank and id have to type it in, which doesn't work by the way.

---

### Post by Matthewslf on 2008-04-04
Disable Roaming mode in Network preferences. It gives the system control over networks instead of you.

---

### Post by darkfire9 on 2008-04-05
when i do that it doesnt find anything at all....it basically is about what im stuck with IN roaming mode, both ways it ends up with all the network info but never actually connects.

 it seems like there is something wrong with the drivers so if theres a way to change them? like some how convert the windows drivers that apparently work for xp on my xp partition, idk.

---

### Post by Matthewslf on 2008-04-06
There is actually something specifically designed for using windows network drivers called ndiswrapper. I am not familiar with it, so I can't give you advice on it, but it's somewhere to start.

---

### Post by darkfire9 on 2008-04-06
ok thx ill see what it does

---

