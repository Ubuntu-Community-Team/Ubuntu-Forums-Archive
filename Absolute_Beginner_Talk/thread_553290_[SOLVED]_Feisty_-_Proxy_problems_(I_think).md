---
title: "[SOLVED] Feisty - Proxy problems (I think)"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by nowhere@cox.net on 2007-09-17
Ok I have a strange problem. Feisty is installed behind my corporate proxy. I have an auto script location set up in Firefox for proxy config and it's working fine. I have $http_proxy set and apt-get seems to work, as well as wget. ntpdate, ping, and  nslookup do not however.  Doesnt seem to be a DNS thing because wget resolves Jarod's website addy just fine.

Any ideas?

Thanks,
Eric

PING NOT WORKING
emorgan@ubuntu-desktop:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)


WGET WORKING
gemorgan@ubuntu-desktop:~$ wget [http://wilsonet.com/mythtv/lirc.modules](http://wilsonet.com/mythtv/lirc.modules)
--13:08:54--  [http://wilsonet.com/mythtv/lirc.modules](http://wilsonet.com/mythtv/lirc.modules)
           => `lirc.modules'
Resolving lps3.phx.st.com... 167.4.190.9
Connecting to lps3.phx.st.com|167.4.190.9|:8080... connected.
Proxy request sent, awaiting response... 200 OK
Length: 145 [text/plain]

100%[==================================================================>] 145           --.--K/s             

13:08:55 (3.97 MB/s) - `lirc.modules' saved [145/145]

---

### Post by Mr.Beast on 2007-09-17
Are you sure that your corporate firewall is not blocking these protocols / port numbers by default? can you carry out the same operations but with responses from the websites if done from different boxes.

just a thought.

---

### Post by nowhere@cox.net on 2007-09-17
You may be right. I figured, however, if the ports were blocked, that the name would still resolve but I would not be able to connect. But I suppose if ping is not allowed to connect to the DNS server then it wouldn't be able to resolve the name. 

Looks like Im stuck with updating my clock manually. 

Thanks,
Eric

---

### Post by Mr.Beast on 2007-09-17
> **nowhere@cox.net said:**
> You may be right. I figured, however, if the ports were blocked, that the name would still resolve but I would not be able to connect. But I suppose if ping is not allowed to connect to the DNS server then it wouldn't be able to resolve the name. 

Looks like Im stuck with updating my clock manually. 

Thanks,
Eric

You could always ask your IT dept what the address is of the NTP server service they run.
They'll either gaze at you blankly, ask you why... or just tell you an address.
Quite often there is one box in a DMZ somewhere that talks to NTP services, and then that box is allowed to update other servers on the main network that can service NTP requests for you on the main network.

---

### Post by nowhere@cox.net on 2007-09-17
I beat yah to it. Talked to em and got the addy to the internal ntp server. Works fine...

Thanks for the help!

Eric

---

