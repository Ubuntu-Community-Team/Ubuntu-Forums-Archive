---
title: "apt problems"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by drtvasudevan on 2006-06-10
will some resident guru join in?
i have had problems with apt-get /synaptic across distroes.
it has never worked
never got solved.
would someone help me try?
i will log in after 12 hours

tv

---

### Post by weasel fierce on 2006-06-10
What specifically happens, when you try to open it ?

Are you using the terminal, or synaptic ?

---

### Post by %hMa@?b&lt;C on 2006-06-10
I cant help if you dont say what the problem is...:(

---

### Post by drtvasudevan on 2006-06-10
> error connection timed out is the usual message.
whether it is synaptic or apt-get from terminal.
same problem in ubuntu/kububtu/xubuntu/zenwalk
but it works in vector linux

no update from any of the ubuntu servers.
regards
tv

---

### Post by richbarna on 2006-06-10
Try this thread, you maybe having a proxy problem :-
[http://www.ubuntuforums.org/showthread.php?t=171126&highlight=synaptic+proxy]("http://www.ubuntuforums.org/showthread.php?t=171126&highlight=synaptic+proxy")

---

### Post by drtvasudevan on 2006-06-10
thanks
i followed the link
i have disabled ipv6 long back.
wwithout that my net does not even connect.
that i learnt long back.

> Most probably, your system uses a proxy. If that is so, follow these steps:
(Steps 1-2 are required evenif your system is not under proxy. Hopefully you have already done it. Here, your_proxy:the_port is that you entered in firefox connection, for example:
proxy.iitc.ernet.in:8080)

i have no proxy settings. in firefox the setting is direct connection to net.
> 
Log into your router through a web browser, mine is 192.168.0.1. Find what your dns server IP's are (on my router there under "status"). Copy these 2 adresses down. Then go to System->Administration->Networking, or network-admin in the comand line. Click on the DNS tab and enter the DNS server addresses you got from your router are on the top of the list.


the isp given dns tally with the setting in network
i connect with adsl modem through eth0

another person had suggested disabling the dns relay.
> Open modem config in any browser (address 10.1.1.1), goto "DNS" and choose "Disable DNS Relay". Now add any DNS addresses to your local /etc/resolver.conf, or simply via the GUI in "System Settings" -> "Network Settings" -> "Domain Name System".
If you don't disable the modem's DNS relay, the local settings will be reset by the modem via DHCP.
Good luck!

i will try that from ubuntu in another partition which i use for experiments.

will be back

tv

---

### Post by drtvasudevan on 2006-06-11
:KS :D 
SOLVED!
thanks all you people.

i disabled dhcp and entered the DNS settings manually.
and i was able to update.

now i shall go over to the main working installation and do it.
tv

---

