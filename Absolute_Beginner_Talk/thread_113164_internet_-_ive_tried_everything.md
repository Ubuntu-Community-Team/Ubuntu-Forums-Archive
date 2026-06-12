---
title: "internet - ive tried everything"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by hen3rz on 2006-01-05
Hello,

I've set up internet and everything is working fine. The only problem I'm having is that its run quite slow.. Ive read through many other posts explaining how to fix this problem and have done all of them with no luck.

I have done the following:

- IPv6 thing
- Modprobe thing
- Firefox tweaks (network.http.pipelining...)
- Using DHCP not Static Ip Address (As apparently its faster)

The main problem I have is that the first time i load a new web server it is really slow then after thats its fine.. and this happens every time i go to a new server. I was told using DHCP and not a Static IP would fix this but unfortunately it hasnt.

BTW: In windows it's fast either way.

---

### Post by tokyovigilante on 2006-01-05
Sounds like you're having a DNS resolution problem. If you're using a static IP, it's likely you've omitted your DNS servers from either the Network configuration in Gnome or in /etc/network/interfaces.

How are you connected to the net? eg Dialup with DHCP, Broadband with Static IP, PPPoE vs PPPoA etc?

---

### Post by hen3rz on 2006-01-05
Im on ADSL its my comp straight into the modem (I have a SpeedTouch 530 modem) if that helps.

---

### Post by TeeAhr1 on 2006-01-05
Are you hanging at "looking up thiswebsite.com..."?  If so, it's a DNS problem.  See [this thread]("http://www.ubuntuforums.org/showthread.php?t=111584").

---

### Post by tokyovigilante on 2006-01-05
Does Windows use DHCP from your modem? ie do you ever have to use a static IP when using Windows? 

If Windows is using DHCP, I'd suggest opening the Advanced section of your Network Status, obtaining the DNS server addresses you're using, and adding them to your Ubuntu network configuration. This should speed things up to normal.

---

### Post by hen3rz on 2006-01-06
Ok in my networking thing under eth0 i have it set to use DHCP and i have listed two DNS servers my ISP has given me.

When I change it to Use static IP and put in my details it still does the same thing eg. when i go to [www.google.com](www.google.com) it will take like 1min to load the main page but once the first page has loaded everything else loads extremelly fast. This happens everytime i visit a website even if i have visited it before the first page takes ages to load.

In other words it takes ages to look up the address but once it finds it, it is fast.

Ok i have done that mod to that file that updates resolv stilll no luck....

---

### Post by hen3rz on 2006-01-06
OMG HOOOOOOOOOOORAY YAYAYAYAY

Thank you guys so much. After you mentioned DNS i went and looked at my ISP's DNS servers and it turns out the first DNS server i listed was incorrect and once i corrected it everything ran smoooothely!!!!!!!

Thank you to everyone who helped me with this.

**Problem solved by correcting an incorrect DNS server in Networking**

---

### Post by tokyovigilante on 2006-01-06
Great, glad to help.

---

