---
title: "can use Live Cd to online?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by allensim81 on 2008-04-01
Hi,
I am now using Ubuntu Live cd.. But i realised that i cant connect to the internet....wad's wrong??? can anyone help me??? 
I selected System>Administration>Network>Wired Connection>
Configuration:Static IP address
and i filled in the IP address,subnet mask & gateway address.
But still, i cannot connect to Internet...Can anyone help me??? 

Do i need to do any setting on General,DNS & Hostst tab??

---

### Post by Mogurijin on 2008-04-01
If you plan to access the internet you'll need a dns. You can either get this through dhcp (if your using a router or something that will do it for ya) or you need to punch some in your self. There is openDNS but I'm not sure what they are exactly, I'll Google it for you ;).

Try this:

[https://www.opendns.com/start?device=ubuntu]("https://www.opendns.com/start?device=ubuntu")

---

### Post by Victormd on 2008-04-01
Are you trying to connect through a DSL or a Router (wired)? If so, it might be better to leave the values as default, using a dhcp to determine your IP... Normally, the live CD will connect directly if your network card is detected.  If you're connected through a router, then the DNS will most likely be your router IP (e.g., 192.168.0.1) but again this is normally detected automatically... What's your hardware?

---

### Post by allensim81 on 2008-04-01
i tried to use the dhcp to auto detect, but it doestn work.
HELPPPPP!!!

---

### Post by N1N31NCHN41L5 on 2008-04-01
Using Live cd - i just plugged in and was online. I turned on a wireless app in add/rmove and was on wireless just as easy.

---

### Post by allensim81 on 2008-04-02
Because i am now in the office. and actually i am using CentOS, i jz set my IP address,subnet mask and default gateway address and primary DNS...and it can online.... 

However, i do the same steeing to my Ubuntu Live CD...still i cannot connect to internet..
wad's wrong?

---

### Post by linux phreak on 2008-04-02
Open terminal and type   sudo pppoeconf

---

### Post by ugm6hr on 2008-04-02
Perhaps an ipv6 issue: [http://ubuntuforums.org/showthread.php?t=87798&page=14](http://ubuntuforums.org/showthread.php?t=87798&page=14)

To check - try going here: [http://64.233.161.99/](http://64.233.161.99/)

---

### Post by allensim81 on 2008-04-02
After i typed sudo pppoeconf;
it can detected eth0
but the following error message appear:
Not Connected
Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network & modem cables. Another reason for the scan failure may also be another running pppoe process which controls modem....

appreciate your feedback...tq

---

