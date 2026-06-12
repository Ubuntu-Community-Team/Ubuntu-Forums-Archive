---
title: "security setting"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by byenary on 2006-05-02
Hellow im looking for a gui way to set security settings like opening ports and that kinda stuff, or to just turn firewalling of, but i can't find such thing, but im sure its there somewhere no ?

Grts

---

### Post by frodon on 2006-05-02
Install firestarter, it's a really good front end for iptables which handle the lubuntu firewall. ```
sudo apt-get install firestarter
```

---

### Post by byenary on 2006-05-02
Thx 

I installed firestarter,
Had a look at it, but when ik look at the inbound traffic policy and want to add one i get all kinds of services but TCP is not one of them ?
And i just need to open a tcp port...

---

### Post by frodon on 2006-05-02
By default, i mean after an ubuntu installation all the ports are opened (usable), so maybe there is no need for you to run a firewall if the only thing you want is to use one port.
Anyway here is how to open a port in tcp with iptables, open a terminal and paste that: ```
sudo iptables -A INPUT -p tcp -m tcp --sport *port_number* -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m tcp --dport *port_number* -j ACCEPT
```The only thing that firestarter do is to set iptables rules so you should be able to do the same with the firestarter GUI.
If you want to learn more about iptables have a look to my guide : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

### Post by byenary on 2006-05-02
Have a look @ this please,
What i want to do infact is connect with mysql workbench to the linux machine. When i do this i get an error and this is probably cause the port is only open for the localhost. sql is running cause webaplication is fine.
nmap for localhost gives a running sqldaemon on 3306 @localhost but when using the ipadres the 3306 is not there...

Thx



root@backupserver2:~# sudo iptables -A OUTPUT -p tcp -m tcp --dport 3306 -j ACCEPT
root@backupserver2:~# sudo iptables -A OUTPUT -p tcp -m tcp --sport 3306 -j ACCEPT
root@backupserver2:~# nmap localhost

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-05-02 10:44 CEST
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1650 ports scanned but not shown below are in state: closed)
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
80/tcp    open  http
111/tcp   open  rpcbind
631/tcp   open  ipp
656/tcp   open  unknown
848/tcp   open  unknown
1234/tcp  open  hotline
2049/tcp  open  nfs
3306/tcp  open  mysql
5900/tcp  open  vnc
32770/tcp open  sometimes-rpc3
32771/tcp open  sometimes-rpc5

Nmap finished: 1 IP address (1 host up) scanned in 0.338 seconds
root@backupserver2:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:3D:5C:F9  
          inet addr:192.168.123.124  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe3d:5cf9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5775257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5785013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:402555877 (383.9 MiB)  TX bytes:3549327216 (3.3 GiB)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:119097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6492648 (6.1 MiB)  TX bytes:6492648 (6.1 MiB)

root@backupserver2:~# nmap 192.168.123.124

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-05-02 10:44 CEST
Interesting ports on 192.168.123.124:
(The 1653 ports scanned but not shown below are in state: closed)
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
80/tcp    open  http
111/tcp   open  rpcbind
656/tcp   open  unknown
848/tcp   open  unknown
1234/tcp  open  hotline
2049/tcp  open  nfs
5900/tcp  open  vnc
32771/tcp open  sometimes-rpc5

Nmap finished: 1 IP address (1 host up) scanned in 0.351 seconds
root@backupserver2:~#

---

### Post by frodon on 2006-05-02
What error do you get exactly ?

I think you forgot to open your port for incoming trafic : *sudo iptables -A INPUT -p tcp -m tcp --sport 3306 -j ACCEPT*

---

