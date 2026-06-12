---
title: "vpn problem"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by NooR on 2005-08-01
h1 2 all. I have a problem with my vpn connection. I havr tied to install pptp client but i have failed. There is a connection for several seconds but then it ends. But internet resources are not available...

my local connection
DHCP server - 192.168.1.1
DNS server -   192.168.1.1
my ip -            192.168.15.179
mask -            255.255.0.0

vpn connection
server type - PPP
server ip - 10.0.0.1
my ip - 10.0.8.115

Pleeeezzee help...  :roll: 

P.S. excuse my english  ;-)

---

### Post by Nequeo on 2005-08-01
Hi NooR,

I'm assuming here you're using the linux pptp-client program to connect to a Microsoft PC/server via the VPN? If not, please correct me. 

But if you are, please post the exact series of commands you are typing to try and established the VPN, along with any config files you have created, and error messages you get.

Lastly, and forgive me if you already know this, but consider using using 'code' tags (the # button at the top of the advanced reply editor) when you're quoting large blocks of text. It makes it much easier to read.

Cheers,

---

### Post by NooR on 2005-08-02
/etc/ppp/chap-secrets

# Secrets for authentication using CHAP
# client        server  secret                  IP addresses
"Fin"   vpn     "******"

/etc/ppp/options

name "Fin"
remotename vpn
defaultroute
noauth
asyncmap 0
crtscts
lock
hide-password
local
noproxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx


root:~ # /sbin/route add -host 10.0.0.1 gw 192.168.1.1

root:~ # route -n

Kernel IP routing table
Destination     Gateway         Genmask             Flags Metric Ref    Use  Iface
10.0.0.1        192.168.1.1     255.255.255.255  UGH   0      0        0      eth0
192.168.0.0     0.0.0.0          255.255.0.0          U        0      0       0     eth0

root:~ # pptp vpn.cable.breezein.net
root:~ # ping [www.ya.ru](www.ya.ru)
connect: Network is unreachable
root:~ # nslookup [www.ya.ru](www.ya.ru)

It's interesting but I get ip of this site - 213.180.204.8 but i can't see it.  ](*,) 

In WinXP:
in my connection properties:
It's use **clear password (PAP)** and **unnecessary cryptooperation**

---

### Post by Nequeo on 2005-08-03
For pptp I created a new file: /etc/ppp/options.pptp with the following inside:

```

lock noauth nobsdcomp nodeflate

```

That's all you really need, option wise, for a pptp connection.

The chap-secrets file should look like this:

```

fin PPTP password * 

```
If you're connecting to a domain, you'll need 'domain\\fin PPTP password *' instead.

You then need to to create a file in /etc/ppp/peers/ with the name of your connection. The name can be anything. So, if you're dialing into work, you could create a file called /etc/ppp/peers/work

In that file, put the following 

```

pty "pptp xxx.xxx.xxx.xxx --nolaunchpppd"
name fin
remotename PPTP
require-mppe-128
file /etc/ppp/options.pptp
ipparam work

```

where xxx.xxx.xxx.xxx is the IP address of the host you are connecting to. Then to connect, type
```

$ sudo pon work

```

After that, you can add the route you need. 

Let me know how it goes.

Cheers!

---

### Post by bb|!2b on 2005-08-04
Hi,

maybe i run into the same problem.

After my pptp-connection is established, i can't ping no ip-adress in the tunnel, all other ip's still runs.

Here is my config.

my ip: 192.168.0.6
my dsl-router 192.168.0.1

pptp-gateway: 62.154.171.130

my options.pptp:

```

lock
noauth
nobsdcomp
nodeflate
noproxyarp

```

my peers/work file:
```

remotename work
linkname work
ipparam work
pty "pptp 62.154.174.130 --nolaunchpppd"
name SAP_Krcek
usepeerdns
require-mppe-128
debug
kdebug 2
defaultroute
mtu 1492
file /etc/ppp/options.pptp

```

After starting.
pon work debug dump logfd 2 nodetach  &

my cons shows this:

```

using channel 39
Using interface ppp0
Connect: ppp0 <--> /dev/pts/6
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb19ff219> <pcomp> <accomp>]
root@lombardi:/etc # sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb19ff219> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 338> <auth chap MS-v2> <magic 0x58725f0c> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 338> <auth chap MS-v2> <magic 0x58725f0c> <pcomp> <accomp>]
rcvd [LCP ConfRej id=0x1 <asyncmap 0x0>]
sent [LCP ConfReq id=0x2 <magic 0xb19ff219> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x2 <magic 0xb19ff219> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xb19ff219]
rcvd [CHAP Challenge id=0x1 <4ce6de1b38c6e88c169c4ca1f2dd7ee5>, name = "watchguard"]
sent [CHAP Response id=0x1 <79d3b87bad91584d1535c9a07945431800000000000000008429c4f76d70a7c594679acf5475ea076edb9c77c07f7c8700>, name = "XXX"]
rcvd [LCP EchoRep id=0x0 magic=0x58725f0c]
rcvd [CHAP Success id=0x1 "S=BD6C37255FAEC21001817AF11AFD562F7803DEC2"]
sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [IPCP ConfReq id=0x1 <addr 62.154.171.130>]
sent [IPCP TermAck id=0x1]
rcvd [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
sent [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 168.121.121.153> <ms-dns1 194.25.0.60> <ms-dns3 194.25.0.68>]
sent [IPCP ConfReq id=0x3 <addr 168.121.121.153> <ms-dns1 194.25.0.60> <ms-dns3 194.25.0.68>]
rcvd [IPCP ConfAck id=0x3 <addr 168.121.121.153> <ms-dns1 194.25.0.60> <ms-dns3 194.25.0.68>]
rcvd [IPCP ConfReq id=0x1 <addr 62.154.171.130>]
sent [IPCP ConfAck id=0x1 <addr 62.154.171.130>]
not replacing default route to ath0 [192.168.0.1]
local  IP address 168.121.121.153
remote IP address 62.154.171.130
primary   DNS address 194.25.0.60
secondary DNS address 194.25.0.68
Script /etc/ppp/ip-up started (pid 30429)
Script /etc/ppp/ip-up finished (pid 30429), status = 0x0
sent [LCP EchoReq id=0x1 magic=0xb19ff219]

```

When i try to ping the existing adress 168.121.121.210, i get no response.

netstat -rn shows:
```

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
62.154.171.130  0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 ath0

```


What's wrong with my config  ](*,)   ?


LL&p
2b

---

### Post by Nequeo on 2005-08-04
Bb|!2b:

It sounds like we need to configure the routing for that connection. But in order to do that, we need to know a bit more about what you're trying to connect to. 

Can I ask what's on the other end of your connection? I.e. are you trying to VPN into a single PC, or a remote network. Do you need to specifically access the internet through that VPN, or just the machine on the other end?

Cheers,

---

