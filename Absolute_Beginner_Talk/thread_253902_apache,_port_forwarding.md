---
title: "apache, port forwarding"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-09-09
I successfully installed apache on my machine earlier. If I enter my ip or localhost it takes me to my index page which must mean it was set up correctly. One small problem however, I cannot access my site from outside my small network. I have searched the forums which have halped somewhat but I am still stuck. I tried to configure my router to forward port 80 but still no luck. I created a dns account which also only works within my network and not externally. Any ideas as to what could be wrong? I don't believe it's a firewall issue. Here is the output from iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

By the way, I have a d-link router and I used the instructions to port forward 80 so I don't think thats a problem. The only idea I have is maybe my isp blocks 80? My isp is adelphia which is now time warner cable

---

### Post by Uluen on 2006-09-09
Sounds like your ISP is blocking port 80. If you forward port 1111 (for example) external to port 80 internal, does that work? [http://yourdomain:1111/](http://yourdomain:1111/)

---

### Post by emprog on 2006-09-09
Thanks for the reply. So swap port 80 to 1111 in my router settings? This is the current settings..

name:http
ip address:my local ip address
port start:80
port end:80
traffic type:TCP
schedule:always

---

### Post by Uluen on 2006-09-09
It looks like your portforwarding is a range of ports to be forwarded, not a different port from outside->inside so you might have to configure apache to listen to the port you specify here.
It doesn't matter what port you choose but it's a good idea to pick one not used by other [services]("http://www.iana.org/assignments/port-numbers").

---

### Post by emprog on 2006-09-09
I see, do you know the config file I need to edit to allow apache to listen on other ports?

---

### Post by scxtt on 2006-09-09
```
:> cat /etc/apache2/ports.conf
Listen 80
```edit that file, put in a different port # - the higher it is the more unlikely it's unused - then restart apache, **sudo /etc/init.d/apache restart**

---

### Post by emprog on 2006-09-09
Thanks for the reply. I edited ports.conf to listen to port 1111 and restarted apache like you mentioned. Now I opened up my router settings and here are my port forwarding settings..

name: http
ip: my local ip in my small network
port start: 1111
port end: 1111
traffic type: TCP
schedule: Always

Now entering my local ip in my network opens my site. If I enter ip:1111 it will get me a connection refused. Trying to open my site from outside the network still does not work however :/

Besides apache, do I need to open this port on my computer too?

---

### Post by scxtt on 2006-09-09
all i have to do is edit my ports.conf file as mentioned above and forward the port on my router - it just works for me [tho i have no problems using 80] ... short of a firewall issue, i'm not sure what your problem would be ...

---

### Post by emprog on 2006-09-09
Thanks for the help, it's very strange because my call to iptables -L shows there is no firewall in the way correct? Is there a way I can verify which ports are open on my computer in terminal?

EDIT: wow, I can even telnet into my dyn dsn host which points to my ip address but of course only within my network.

---

