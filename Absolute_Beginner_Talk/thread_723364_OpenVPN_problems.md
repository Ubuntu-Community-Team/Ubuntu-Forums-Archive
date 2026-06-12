---
title: "OpenVPN problems"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by auddin2 on 2008-03-13
Hi, I have looked at the other threads and I didn't seem to find anything useful.
I have gotten openvpn to work on windows, but I can't get it to work correctly on gutsy.
Here's what I get when I run it:
```

atif@atif-laptop:~$ sudo /etc/init.d/openvpn restart
[sudo] password for atif:
Stopping virtual private network daemon: atif.
Starting virtual private network daemon: atif(OK).
atif@atif-laptop:~$ 

```
It looks like it runs fine, but it doesn't connect to any of the webpages of my company's internal network.

I've tried using Network-Manager, and "create vpn connection" , but even if I enter all the fields, the "forward" button is grayed out and won't let me go forward.

What steps should I take?
Thanks.

---

### Post by SpaceTeddy on 2008-03-13
can you post the content of the atif.conf located in your /etc/openvpn directory please. Also, blank out any ip's or hostnames that are found in there. i've got a feeling that either the assiciation of the tun/tap device fails, or the daemonize does not work properly... but i need to see the file for that. 

Also, if there is a log for openvpn (should be written in your config file where the log is), can you please check if there are any error messages in there ?

thanks

---

### Post by auddin2 on 2008-03-13
Thank you for replying!

```


# Use a dynamic tun device.
dev tun

# Our OpenVPN peer is the office gateway.
remote ###

# We'll be running as a client
client

# In SSL/TLS key exchange, Office will
# assume server role and Home
# will assume client role.
tls-client

# Certificate Authority file
ca /etc/openvpn/atif/ca.crt

# Our certificate/public key
cert /etc/openvpn/atif/atif.crt

# Our private key
key /etc/openvpn/atif/atif.key

# OpenVPN uses UDP port 1194 by default.
# We are multiplpexing over that port so
# everyone uses the same port
; port 1194

# Downgrade UID and GID to
# "nobody" after initialization
# for extra security.
# This can break connection re-establishment
# and post connection changes since the openvpn
# process will no longer have root privs.  Make
# sure you use sudo or some other privelege 
# escalation tool ro comment out these two lines.
user nobody
group daemon

# We'll compress when we can
comp-lzo

# Send a UDP ping to remote once
# every 15 seconds to keep
# stateful firewall connection
# alive.  Uncomment this
# out if you are using a stateful
# firewall.
ping 15

# Uncomment this section for a more reliable detection when a system
# loses its connection.  For example, dial-ups or laptops that
# travel to other locations.
# See the comment on the User and Group settings above.
; ping 15
; ping-restart 45
; ping-timer-rem
; persist-tun
; persist-key

# Verbosity level.
# 0 -- quiet except for fatal errors.
# 1 -- mostly quiet, but display non-fatal network errors.
# 3 -- medium output, good for normal operation.
# 9 -- verbose, good for troubleshooting
verb 3

```

Where is the log file?

---

### Post by SpaceTeddy on 2008-03-13
the logfiel is not specified, which means that your log is defaulting to (i think) /var/log/openvpn.log and /var/log/openvpn-status.log

also, check if you have a group daemon - your config specifies that it should degrade it self to run under that group - if the group does not exist it would abort the connection.

to acctually get some debug output, also try running the openvpn command directly and not over daemon wrapper...

if i am not mistaken, this could be done with the following command
```
sudo openvpn --config /etc/openvpn/atik.conf
```
that will give you status information on the console and tell you if something i wrong... 
if you are in doubt, paste the log output here

as a sidenode - i am not sure if you need it, but there is no daemo specified in the config file - you might want to add that later on when the config works... that could be a problem aswell, as the openvpn process will not go into the background without it

---

### Post by auddin2 on 2008-03-13
I looked for log files (by searching in the places you told, searching for "openvpn" and "*.log" in the file search), and I couldn't find any for openvpn.
I ran the command you told me and here is the output (I masked my company name, my full name, and parts of the ip addresses with #)
```

Thu Mar 13 20:43:07 2008 OpenVPN 2.0.9 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] built on May 21 2007
Thu Mar 13 20:43:07 2008 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Thu Mar 13 20:43:07 2008 WARNING: you are using user/group/chroot without persist-key/persist-tun -- this may cause restarts to fail
Thu Mar 13 20:43:07 2008 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Thu Mar 13 20:43:07 2008 WARNING: file '/etc/openvpn/atif/atif.key' is group or others accessible
Thu Mar 13 20:43:07 2008 LZO compression initialized
Thu Mar 13 20:43:07 2008 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Thu Mar 13 20:43:07 2008 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Thu Mar 13 20:43:07 2008 Local Options hash (VER=V4): '41690919'
Thu Mar 13 20:43:07 2008 Expected Remote Options hash (VER=V4): '530fdded'
Thu Mar 13 20:43:07 2008 NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Thu Mar 13 20:43:07 2008 UDPv4 link local (bound): [undef]:1194
Thu Mar 13 20:43:07 2008 UDPv4 link remote: #.#.#.#:1194
Thu Mar 13 20:43:07 2008 TLS: Initial packet from #.#.#.#:1194, sid=e5980f88 f20b5334
Thu Mar 13 20:43:07 2008 VERIFY OK: depth=1, /C=US/ST=IL/L=CHICAGO/O=company_Security/emailAddress=vpn@company.net
Thu Mar 13 20:43:07 2008 VERIFY OK: depth=0, /C=US/ST=IL/O=company_Security/CN=chi-vpn-server/emailAddress=vpn@company.net
Thu Mar 13 20:43:08 2008 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Mar 13 20:43:08 2008 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Mar 13 20:43:08 2008 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Mar 13 20:43:08 2008 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Mar 13 20:43:08 2008 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Thu Mar 13 20:43:08 2008 [chi-vpn-server] Peer Connection Initiated with 66.113.128.237:1194
Thu Mar 13 20:43:09 2008 SENT CONTROL [chi-vpn-server]: 'PUSH_REQUEST' (status=1)
Thu Mar 13 20:43:09 2008 PUSH: Received control message: 'PUSH_REPLY,route 10.0.0.0 255.0.0.0,route #.#.#2.1,ifconfig #.#.#3.54 #.#.#3.53'
Thu Mar 13 20:43:09 2008 OPTIONS IMPORT: --ifconfig/up options modified
Thu Mar 13 20:43:09 2008 OPTIONS IMPORT: route options modified
Thu Mar 13 20:43:09 2008 TUN/TAP device tun0 opened
Thu Mar 13 20:43:09 2008 ifconfig tun0 #.#.#3.54 pointopoint #.#.#3.53 mtu 1500
Thu Mar 13 20:43:09 2008 route add -net 10.0.0.0 netmask 255.0.0.0 gw #.#.#3.53
Thu Mar 13 20:43:09 2008 route add -net #.#.#2.1 netmask 255.255.255.255 gw #.#.#3.53
Thu Mar 13 20:43:09 2008 GID set to daemon
Thu Mar 13 20:43:09 2008 UID set to nobody
Thu Mar 13 20:43:09 2008 Initialization Sequence Completed

```

---

### Post by SpaceTeddy on 2008-03-14
it looks fine so far - the init completed and the link seems to be up (the warnings at the top should be fixed, but are not essential).

once the thing is conncted, you should have a new network device (in your case tun0) which should have an ip address assigned. When using openvpn Servers, the server always gets the first ip (so if your netwok 192.168.0.0/24 your server would be 192.168.0.1).

after the connection, try to ping the server and see if it answers. Also check with 
```
route -n
```
if the route for the vpn network was set (but the looks of the log they are).
A known issue with openvpn connection in linux is that they do not set the pushed dns servers correctly, but i do not see any push for DNS server in the log, so i think that might not be the issue either.

But i do see that the network which gets pushed to be over the vpn is rather large (the full 10.0.0.0/8). Make sure you are not using this subnet, or any fraction of this subnet at home, since that would collide with the VPN. So check the ip address of your network card against the pushed one from the VPN-server.

maybe there is a fix in there :)

---

### Post by auddin2 on 2008-04-05
I see the ip address of my tun0.
1.  How do I find the IP address of the server?
2. Here is the output of "route -n":
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.33.53     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.10.32.1      10.10.33.53     255.255.255.255 UGH   0      0        0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
10.0.0.0        10.10.33.53     255.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
```
3. How do I find the ip address of my network card?
4. I can also post the log of the vpn (which works successfully) in Windows, if that could help.
Thanks!

---

### Post by auddin2 on 2008-04-08
anyone please?

---

### Post by auddin2 on 2008-04-22
Will problems like these be fixed with the next release of Ubuntu?

---

### Post by SpaceTeddy on 2008-04-22
i've read through the thread twice and don't know what i was on about :( sorry. from the logs and outputs i an tell that your vpn connection is established sucessfully. Also, the routes (10.x.x.x) is set correctly over the VPN ( i would say that is the network you want to forward ?), while your local network is 192.168.0.x. This also means you have no overlapping networks. 

The only thing i can possibly think of being wrong here is that your DNS Server do not get pushed into your resolv.conf... come to think of it... This line
```
Thu Mar 13 20:43:09 2008 PUSH: Received control message: 'PUSH_REPLY,route 10.0.0.0 255.0.0.0,route #.#.#2.1,ifconfig #.#.#3.54 #.#.#3.53'
```
does not even hold any nameservers to be pushed to you. That would explain why you are not able to resolve any internal names. Also, somehting about those routes seems odd to me... can pin down what is tho... 

Ok, once you are connected, the VPN server ALWAYS has the first ip addres in the range - so if your server is configured with 10.0.0.0/8 that would mean your server has the 10.0.0.1. If you network is 172.51.63.0/24 then your vpn server would have the 172.51.63.1 (the i've chosen here is totally random - i don't know it !)

that would also be my first question - once you are connected to the VPN, can you ping the server (i.e. the first IP address in the range). if you can do that, can you ping other internal hosts (probably within in the 10.0.0.0/8 network) by the ip address ?

Sorry that i have to get into this thread again... 

PS: if you want me to fully debug your network, send me a picture of the network layout including the essential IP's assigned via pm. Also attach the config of the server as well as a config of any client. **DON'T send me any keys or certificates** !!!!!

---

### Post by auddin2 on 2008-04-22
I found that if I ping the server (and the internal server addresses) without the port (1194), the ping works. However, if I do specify the port, then the ping fails.

---

### Post by SpaceTeddy on 2008-04-23
ok, so you can contact the server with the vpn ip - can you reach anything trough the server, i.e. any ip that would be tunneled through the tun device ? (this should be an ip like 10.x.x.x).

meaning that the server also forwards...

---

