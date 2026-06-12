---
title: "Trying to get ICS working"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by heat84 on 2007-10-29
I'm trying to get internet connection sharing working. Evenhough the client PC's  NIC "can't aquire a network address", I can see it on the network and access the drives and files. I followed the instructions in [another]("http://ubuntuforums.org/showthread.php?t=91370") thread here to enable ICS in Ubuntu. I'm not sure if it took. Hopfully when the network is fully working, ICS will wok. Apparently the problem is DHCP. I have it enabled. But it doesn't sem to be working.

---

### Post by Austin_KW on 2007-10-29
It sounds like it is is just connecting using a 169.x.x.x address, not nat or dhcp.

If you install firestarter and run the wizard it will  prompt you and set up ics using the gui.

---

### Post by heat84 on 2007-10-30
I tried Firestarter but it won't start. It keeps saying: Failed to start the firewall. The device eth1 is not ready. Eth1 is the NIC that the other computer i connected to. Where did you see 169.x.x.x? Is that a default IP address? I have eth1 set for DHCP. So why wouldn't it be working?

---

### Post by Austin_KW on 2007-10-30
Try rerunning the wizard and tell it that eth0? is internet connnection, that you want to share internet with eth1 and use dhcp on local network.

169.x address are the zeroconfig address used when you connect 2 computers but do not configure the addressing manually.
It has been some time since i had to use ICS, before the avahi deamon allocated the 169 address. The two things may be interfering with each other. You may need to set a static 192.168.0.x address on eth1, I need to think about this.

---

### Post by heat84 on 2007-11-01
Why is DHCP greyed out in the Firestarter Wizard? Could that be part of the problem or linked to the cause?

Is there anyway I could use Zeroconf?


Edit: I just figured out the DHCP is grayed there because DHCP isn't working in Ubuntu. Where do you enable it? I have the NIC set to use it. 

When I try to start it in a terminal it says:** invoke-rc.d: initscript dhcp3-server, action "start" failed**.

---

### Post by Austin_KW on 2007-11-01
Probably no dhcp server installed

---

### Post by heat84 on 2007-11-01
Doesn't Ubuntu install one by default? Why would it let you enable DHCP for a NIC if not? I also installed it myself just to make sure and got that error message.

Edit: Make sure you read the edit in my previous post.

---

### Post by Austin_KW on 2007-11-01
Ok, I remember reading about this,

The file path for dhcp server start may be wrong in /etc/firestarter/firestarter.sh ?

from firestarter.sh
```
   if [ -e /etc/init.d/dhcp3-server ]; then
                /etc/init.d/dhcp3-server restart > /dev/null
        elif [ -e /etc/init.d/dhcpd ]; then
                  /etc/init.d/dhcpd restart > /dev/null
                /usr/sbin/dhcpd 2> /dev/null
                start_dhcp_server

```

check your /etc/init.d/dhcp* for the proper name and fix in firestarter.sh or add a sym link in  /etc/init.d/

---

### Post by ByteJuggler on 2007-11-01
> **heat84 said:**
> Why is DHCP greyed out in the Firestarter Wizard? Could that be part of the problem or linked to the cause?

Is there anyway I could use Zeroconf?


Edit: I just figured out the DHCP is grayed there because DHCP isn't working in Ubuntu. Where do you enable it? I have the NIC set to use it. 

When I try to start it in a terminal it says:** invoke-rc.d: initscript dhcp3-server, action "start" failed**.

Let me just point out as a general observation there's a difference between a NIC using DHCP (as a client) to get an IP from **another** DHCP server (e.g. maybe your router) and having DHCP (a server) installed on your Linux box, so it hands out IP's to **other** PC's etc.  Firestarter/Linux cannot enable DHCP serving unless a DHCP server is installed, irrespective of whether existing NIC's are set up to get their IP's from another DHCP server.

---

### Post by heat84 on 2007-11-01
@ByteJuggler: There is a DHCP server installed but it won't start.

@Austin_KW: According to Firestarters DHCP page: **If a DHCP binary is not detected on the system, the DHCP controls will remain inactive** . So I don't think Firestarter is the problem. I think the problem just that DHCP won't start for some reason. As I already said, I tried to start it manually.

---

### Post by Austin_KW on 2007-11-01
Just to reiterate ByteJuggler's point you do not wan to run the dhcpserver for the internet connection nic.

I am assuming that it is failing because it is not configured.  Been awhile as I have used a router for years. What is the failure message on "tail -n 20 /var/log/syslog"

---

### Post by Austin_KW on 2007-11-01
Also I think firestarter can write the dhcpd.conf for you, if you tell it to create a new dhcp config for the ICS interface?

---

### Post by Austin_KW on 2007-11-01
Also you may want to give the ICS interface a static address on the same subnet that you tell firestarter to used for the ICS dhcp clients

---

### Post by heat84 on 2007-11-01
```
Nov  1 14:08:30 Server kernel: [  367.844431] Unknown OutputIN= OUT=eth0 SRC=160.160.160.160 DST=160.160.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32790 DPT=137 LEN=58 
Nov  1 14:08:31 Server kernel: [  368.790968] Unknown OutputIN= OUT=eth0 SRC=160.160.160.160 DST=160.160.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32790 DPT=137 LEN=58 
Nov  1 14:08:45 Server kernel: [  383.199521] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6782 PROTO=UDP SPT=68 DPT=67 LEN=308 
Nov  1 14:13:33 Server kernel: [  670.396310] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.198 DST=65.2.36.228 LEN=485 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=54874 DPT=1026 LEN=465 
Nov  1 14:14:24 Server kernel: [  721.023938] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.199 DST=65.2.36.228 LEN=485 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=50555 DPT=1027 LEN=465 
Nov  1 14:14:27 Server kernel: [  724.932926] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6783 PROTO=UDP SPT=68 DPT=67 LEN=308 
Nov  1 14:14:31 Server kernel: [  728.929865] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6784 PROTO=UDP SPT=68 DPT=67 LEN=308 
Nov  1 14:14:38 Server kernel: [  735.924392] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6785 PROTO=UDP SPT=68 DPT=67 LEN=308 
Nov  1 14:14:54 Server kernel: [  751.911882] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6786 PROTO=UDP SPT=68 DPT=67 LEN=308 
Nov  1 14:16:45 Server kernel: [  862.468566] Inbound IN=ppp0 OUT= MAC= SRC=6.37.193.139 DST=65.2.36.228 LEN=388 TOS=0x00 PREC=0x00 TTL=51 ID=24438 PROTO=UDP SPT=31082 DPT=1026 LEN=368 
Nov  1 14:17:01 Server /USR/SBIN/CRON[7308]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 14:17:38 Server kernel: [  915.693659] Inbound IN=ppp0 OUT= MAC= SRC=221.209.110.13 DST=65.2.36.228 LEN=485 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=UDP SPT=43962 DPT=1026 LEN=465 
Nov  1 14:17:38 Server kernel: [  915.696023] Inbound IN=ppp0 OUT= MAC= SRC=221.209.110.13 DST=65.2.36.228 LEN=485 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=UDP SPT=43962 DPT=1027 LEN=465 
Nov  1 14:19:08 Server kernel: [ 1005.219695] Inbound IN=ppp0 OUT= MAC= SRC=221.208.208.97 DST=65.2.36.228 LEN=486 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=UDP SPT=49626 DPT=1026 LEN=466 
Nov  1 14:19:08 Server kernel: [ 1005.222058] Inbound IN=ppp0 OUT= MAC= SRC=221.208.208.97 DST=65.2.36.228 LEN=486 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=UDP SPT=49626 DPT=1027 LEN=466 
Nov  1 14:20:38 Server kernel: [ 1094.645562] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6787 PROTO=UDP SPT=68 DPT=67 LEN=308 
Nov  1 14:20:43 Server kernel: [ 1099.641627] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6788 PROTO=UDP SPT=68 DPT=67 LEN=308 
Nov  1 14:20:49 Server kernel: [ 1105.822590] Inbound IN=ppp0 OUT= MAC= SRC=221.209.110.9 DST=65.2.36.228 LEN=485 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=UDP SPT=38690 DPT=1027 LEN=465 
Nov  1 14:20:50 Server kernel: [ 1106.636160] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6789 PROTO=UDP SPT=68 DPT=67 LEN=308 
Nov  1 14:21:05 Server kernel: [ 1121.624427] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6790 PROTO=UDP SPT=68 DPT=67 LEN=308 

```

Well there it is.

So when you enable DHCP in a NIC's connection settings, thats just for client purposes? I should've known that.:oops:

---

### Post by Austin_KW on 2007-11-01
Looks like you missed it, lots of iptable logs, rerun the commands
```

sudo /etc/init.d/dhcp3-server start
tail -n 20 /var/log/syslog   

```

EDIT;
might be easier to just search the log
```

grep dhcp /var/log/syslog     

```

---

### Post by heat84 on 2007-11-01
```
Nov  1 14:56:15 Server dhcpd: Wrote 0 leases to leases file.
Nov  1 14:56:15 Server dhcpd: 
Nov  1 14:56:15 Server dhcpd: No subnet declaration for eth1 (160.160.160.161).
Nov  1 14:56:15 Server dhcpd: ** Ignoring requests on eth1.  If this is not what
Nov  1 14:56:15 Server dhcpd:    you want, please write a subnet declaration
Nov  1 14:56:15 Server dhcpd:    in your dhcpd.conf file for the network segment
Nov  1 14:56:15 Server dhcpd:    to which interface eth1 is attached. **
Nov  1 14:56:15 Server dhcpd: 
Nov  1 14:56:15 Server dhcpd: 
Nov  1 14:56:15 Server dhcpd: No subnet declaration for eth0 (160.160.160.160).
Nov  1 14:56:15 Server dhcpd: ** Ignoring requests on eth0.  If this is not what
Nov  1 14:56:15 Server dhcpd:    you want, please write a subnet declaration
Nov  1 14:56:15 Server dhcpd:    in your dhcpd.conf file for the network segment
Nov  1 14:56:15 Server dhcpd:    to which interface eth0 is attached. **
Nov  1 14:56:15 Server dhcpd: 
Nov  1 14:56:15 Server dhcpd: 
Nov  1 14:56:15 Server dhcpd: Not configured to listen on any interfaces!
Nov  1 14:56:58 Server kernel: [ 3281.939010] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6814 PROTO=UDP SPT=68 DPT=67 LEN=308 
Nov  1 14:57:02 Server kernel: [ 3285.935993] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6815 PROTO=UDP SPT=68 DPT=67 LEN=308 
Nov  1 14:57:10 Server kernel: [ 3293.929734] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:31:0d:e0:94:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=6816 PROTO=UDP SPT=68 DPT=67 LEN=308 

```

---

### Post by Austin_KW on 2007-11-01
I dont know about those 160.x addresses

Assuming you are using eth1 to be ICS interface on your local network

Set eth1 to use a static IP 192.168.0.1 Mask:255.255.255.0

Use firestarter wizard  to configure ICS on eth1 and select the option to configure a new dhcp range; Use the 192.168.0.x subnet, it should fill in the defaults.

Save the options and start the firewall.
Hopefully now the dhcp server should start on eth1

---

### Post by heat84 on 2007-11-01
I booted into Live CD mode and installed the DHCP server and it still wouldn't start. If that indicates anything. 

DHCP is still grayed ut in the wizard. Soit still won't start it that way.

---

### Post by Austin_KW on 2007-11-01
Have you given the interface a satic address and configured dhcpd.conf

---

### Post by heat84 on 2007-11-01
I got it working![IMG]http://www.miamiheatwave.com/forums/style_emoticons/default/dancing.gif[/IMG]

What I did was I went into the Firestarter preferences and enabled DHCP there. Its still grayed in the wizard (although the box is now checked) :confused:. It specifically says in the Firestarter documetation:* The DHCP service can be configured from the firewall wizard, **or** from the preferences.* But it only works in the preferences. A bug maybe?:confused:

---

