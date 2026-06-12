---
title: "Shorewall"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-02-25
Need help people!

OS: Ubuntu 5.10 in terminal mode

I have a router/switch which contains the normal Firewall/Nat stuff, I only port forward the ports I need.

Now I've just installed shorewall and I'm totally out of my depth!! I've looked at the help files, but it's all meaningless to me.

---

### Post by John.Michael.Kane on 2006-02-25
[http://rouke.freeasanerd.com/manuals/](http://rouke.freeasanerd.com/manuals/)
[http://www.shorewall.net/shorewall_setup_guide.htm](http://www.shorewall.net/shorewall_setup_guide.htm)
[http://www.my-opensource.org/howto/qostrafficshaping-shorewall-wondershaper-howto.html](http://www.my-opensource.org/howto/qostrafficshaping-shorewall-wondershaper-howto.html)
[https://users.cs.jmu.edu/aboutams/Public/CS482_Spring2005/Module%204-%20Firewall/Shorewall%20Tutorial.doc](https://users.cs.jmu.edu/aboutams/Public/CS482_Spring2005/Module%204-%20Firewall/Shorewall%20Tutorial.doc)

---

### Post by My-dial-up on 2006-03-01
Struggling with this, but trying to sort it out. 

I have a ADSL DHCP router/switch which feeds the internet/intranet to my Ubuntu PC. The Ubunu PC has a static IP address & obviously only one network card.

Does this mean that I use the 'one-interface model' or the 'two-interface model'??

---

### Post by My-dial-up on 2006-03-02
Please? Anyone?

---

### Post by darth_vector on 2006-03-02
you would use the two interface model if your ubuntu machine was acting as a gateway; that is, if it had an external (real world) IP on one interface and an internal network address on another interface.

if the ubuntu machine is on the internal network then you should use the single interface model.

having said that, doesnt your adsl modem/router have a built in firewall and NAT? if so, why do you need shorewall on the box? to get rid of it```
sudo apt-get remove --purge shorewall
```

---

### Post by My-dial-up on 2006-03-02
The Ubuntu PC doesn't act as a gateway; it can access the internet/intranet though.

ifconfig reports back;
eth0      Link encap:Ethernet  HWaddr 00:50:04:33:33:BB
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fe33:33bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14668 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14220131 (13.5 MiB)  TX bytes:3529346 (3.3 MiB)
          Interrupt:11 Base address:0x1080

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:42391451 (40.4 MiB)  TX bytes:42391451 (40.4 MiB)


so I would have thought the one-interface modal was best. Correct?



Re: Router - yes, it does have a firewall + NAT which is active, and I only 'port-forward' the ports I need, but I was advised elsewhere that it's still a good idea to setup shorewall.

---

### Post by darth_vector on 2006-03-02
correct, you want the one interface model.

---

### Post by My-dial-up on 2006-03-02
Many thanks.

---

