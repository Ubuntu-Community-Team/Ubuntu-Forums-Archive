---
title: "helloowwww"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by stamateviorel on 2007-03-01
so I have nvidia nforce network controller NIC and on my windowz box works just fine and on  fedora to but when I plug my ubuntu edgy my dhcp ISP server give`s me the ip like in windows all is good but when I try to open an webpage nothing happens .... so a little help pleaseeee :)

---

### Post by taurus on 2007-03-01
What are the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal?

```
ping -c 3 www.google.com
/sbin/ifconfig
```

---

### Post by janz84 on 2007-03-01
Is there only one nic on the mobo?

---

### Post by stamateviorel on 2007-03-01
I have only one nick

---

### Post by stamateviorel on 2007-03-01
ok so I will be back with that stuff luckly I have a linux partion to save :D

---

### Post by stamateviorel on 2007-03-01
I am back with some information ... as I suspected the ping thing told me this "host uknown" so ... for the first time I went to the network tools and on the device tab there was a combo with lo and eth0 so I click on the eth0 and woow on the bottom box I saw my ip and subnet and gateway like in windows ... so I think my nic works but the browser and other`s don`t so there should be some think to do ....

---

### Post by stamateviorel on 2007-03-01
eth0 Link encap Ethernet Hwaddr 00:01:02:aa:bb:cc
inet addr : 81.181.124.43 Bcast : 81.181.124.255 Mask : 255.255.255.255.255
inet6 addr : fe80::201:2ff:feaa:bbcc/64 Scope : Link
UP BROADCAST RUNNING MULTICAST MTU : 1500 Metric :1
Rx pachets 9 errors : 0 droppet : 0 overruns : 0 carrier : : collisions : 0 txqueuelen : 1000
Rx bytes :78806 (76.9 KiB) Tx bytes :1494 (1.4 KiB)
interrupt : 185 Base adress : 0xe000
lo Link encap : Local Loopback
inet addr :127.0.0.1 Mask 255.0.0.0
inet addr : : : 1/128 Scope : Host
UP LOOPBACK RUNNING MTU : 16436 Metric :1
Rx packets:4 errors : 0 dropped : 0 overruns : 0 frame :0
Tx packets : 4 errors : 0 dropped : 0 overruns : 0 carrrier : 0 collisions : 0 txqueuelen : 0
Rx bytes : 200 (200.0 b) Tx byte : 200 (200.0b)

---

### Post by jkeyes0 on 2007-03-01
Can you post the contents of your /etc/resolv.conf file?

---

### Post by stamateviorel on 2007-03-01
Oh goosh that is too much handwriting for me isnt that enought ?

---

