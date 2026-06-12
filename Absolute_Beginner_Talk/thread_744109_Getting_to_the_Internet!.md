---
title: "Getting to the Internet!"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Dragonlaw on 2008-04-03
Hello I'm so sorry for asking but I have not been able to connect to the internet via my desktop so I have to borrow a laptop to ask this question.

I just installed Ubuntu 7.10 yesterday without the modem. I plugged in the Modem today and went to system > network > wired connection with the dhcp setting. However, I have not been able to connect to the internet! I'm using a Speedstream Router 4100.

Please help me!

---

### Post by TeoBigusGeekus on 2008-04-03
Pressuming that your router is properly configured (username, password, etc.), try to use roaming mode instead of dhcp.

---

### Post by Dragonlaw on 2008-04-03
I did that already. I also tried going into the terminal and using sudo econf.

What I got was that the terminal saying that "Sorry I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cabes. Another reason for the scan failure may also be another running pppoe process which controls the modem"

---

### Post by bumanie on 2008-04-03
This is not always the problem, but sometimes is. I had to do this to connect gutsy. Put in roaming mode as you have. Open firefox and in the address bar 
type about:config 
In the filter type ipv6
Right click on the resulting line and then left click toggle to change the value to true. I fit doesn't work, you can reverse the process and change the toggle back to false.
Hope it works.

---

### Post by TeoBigusGeekus on 2008-04-03
I can't think of anything else...Put it on roaming mode and try to reset your router...
Sorry...

---

### Post by adi_das on 2008-04-03
Type sudo pppoeconf in the terminal and try it.

---

### Post by Dragonlaw on 2008-04-03
Ok I settled the problem. I reinstalled Ubuntu from the start, making sure that the DSL modem was connected at all times for Ubuntu to detect it. Once I did that I could install the Modem already.

---

