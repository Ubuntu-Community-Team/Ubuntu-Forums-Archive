---
title: "PPPoE connection"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by hmsf on 2007-03-05
Last week my internet broadband connection changed a bit... I have a Speedtouch Pro modem, and it was configured to route, so it was way easy to connect to the internet... but my ISP changed something and my modem (that is "a little bit" old) couldn't connect anymore... so I called them and was instructed to change my connection to bridge mode, which I did... But since then I couldn't navigate anymore.

I have dual-boot with windows xp, and it connects easily on windows. In Ubuntu, I tried to use pppoeconf and RP-PPPoE, with no success... It seems to be connected, I can access the modem's config page, I can even see that the authentication was successful (with plog or adsl-status)... But I can't navigate... I was even thinking about changing my modem, but this morning the connection suddenly worked. But unfortunately I had to turn off the computer to go lunch, and when I came back, everything was the same as the other days...

The problem is that I can't determine precisely what I did when the connection worked. I remember that I entered the 'adsl-start', then the 'dhclient' command (but I had done it other times before and it didn't work anyway). No navigation yet, but I started the RP-PPPoE GUI (./go-gui) and everything worked. I didn't need even to start the connection on the GUI...

Now... what may be my problem? When I see the system logs, it seems to have some problem with a PADO ticket, but I have no idea of what's that...

First the errors and the connection hanging up:

```
 11:59:48  dhclient: Internet Systems Consortium DHCP Client V3.0.4
 11:59:48  dhclient: wifi0: unknown hardware address type 801
 11:59:49  dhclient: can't create /var/lib/dhcp3/dhclient.leases: Permission denied
 11:59:49  dhclient: Can't create /var/run/dhclient.pid: Permission denied
 11:59:54  dhclient: Internet Systems Consortium DHCP Client V3.0.4
 11:59:54  dhclient: wifi0: unknown hardware address type 801
 11:59:55  avahi-daemon[4437]: Withdrawing address record for 192.168.1.10 on eth0.
 11:59:55  avahi-daemon[4437]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.10.
 11:59:55  avahi-daemon[4437]: iface.c: interface_mdns_mcast_join() called but no local address available.
 11:59:55  avahi-daemon[4437]: Interface eth0.IPv4 no longer relevant for mDNS.
 11:59:56  avahi-daemon[4437]: Withdrawing address record for 192.168.1.101 on ath0.
 11:59:56  avahi-daemon[4437]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.101.
 11:59:56  avahi-daemon[4437]: iface.c: interface_mdns_mcast_join() called but no local address available.
 11:59:56  avahi-daemon[4437]: Interface ath0.IPv4 no longer relevant for mDNS.
 11:59:57  dhclient: wifi0: unknown hardware address type 801
 11:59:58  dhclient: Listening on LPF/wifi0/
 11:59:58  dhclient: Sending on   LPF/wifi0/
 11:59:58  dhclient: Listening on LPF/eth0/xx:xx:xx:xx:xx:xx
 11:59:58  dhclient: Sending on   LPF/eth0/xx:xx:xx:xx:xx:xx
 11:59:58  dhclient: Listening on LPF/ath0/xx:xx:xx:xx:xx:xx
 11:59:58  dhclient: Sending on   LPF/ath0/xx:xx:xx:xx:xx:xx
 11:59:58  dhclient: Sending on   Socket/fallback
 11:59:59  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 5
 12:00:00  dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
 12:00:00  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
 12:00:00  dhclient: DHCPACK from 192.168.1.1
 12:00:00  avahi-daemon[4437]: New relevant interface eth0.IPv4 for mDNS.
 12:00:00  avahi-daemon[4437]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.10.
 12:00:00  avahi-daemon[4437]: Registering new address record for 192.168.1.10 on eth0.
 12:00:00  dhclient: bound to 192.168.1.10 -- renewal in 2878 seconds.
 12:00:03  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
 12:00:04  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 12
 12:00:06  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
 12:00:12  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
 12:00:16  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 10
 12:00:20  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
 12:00:26  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
 12:00:33  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
 12:00:33  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 8
 12:00:40  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
 12:00:41  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 11
 12:00:48  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
 12:00:52  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 8
 12:00:58  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
 12:01:00  dhclient: No DHCPOFFERS received.
 12:01:00  dhclient: No working leases in persistent database - sleeping.
 12:01:01  dhclient: No DHCPOFFERS received.
 12:01:01  dhclient: No working leases in persistent database - sleeping.
 12:03:36  dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 3350
 12:03:36  dhclient: killed old client process, removed PID file
 12:03:36  dhclient: Internet Systems Consortium DHCP Client V3.0.4
 12:03:36  dhclient: wifi0: unknown hardware address type 801
 12:03:36  dhclient: wifi0: unknown hardware address type 801
 12:03:36  dhclient: Listening on LPF/eth0/xx:xx:xx:xx:xx:xx
 12:03:36  dhclient: Sending on   LPF/eth0/xx:xx:xx:xx:xx:xx
 12:03:36  dhclient: Sending on   Socket/fallback
 12:03:36  dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
 12:03:36  avahi-daemon[4437]: Withdrawing address record for 192.168.1.10 on eth0.
 12:03:36  avahi-daemon[4437]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.10.
 12:03:36  avahi-daemon[4437]: iface.c: interface_mdns_mcast_join() called but no local address available.
 12:03:36  avahi-daemon[4437]: Interface eth0.IPv4 no longer relevant for mDNS.
 12:03:36  pppoe[5636]: recv (receivePacket): Network is down
 12:03:36  pppoe[5636]: send (sendPacket): Network is down
 12:03:36  dhclient: receive_packet failed on eth0: Network is down
 12:03:36  pppd[5632]: Modem hangup
 12:03:36  pppd[5632]: Connect time 78.1 minutes.
 12:03:36  pppd[5632]: Sent 0 bytes, received 858 bytes.
 12:03:36  pppd[5632]: Connection terminated.
 12:03:37  pppd[5632]: Exit.
 12:03:37  avahi-daemon[4437]: New relevant interface eth0.IPv4 for mDNS.
 12:03:37  avahi-daemon[4437]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.10.
 12:03:37  kernel: [17185018.020000] ADDRCONF(NETDEV_UP): eth0: link is not ready
 12:03:37  avahi-daemon[4437]: Registering new address record for 192.168.1.10 on eth0.
 12:03:37  kernel: [17185018.024000] e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
 12:03:37  adsl-connect: ADSL connection lost; attempting re-connection.
 12:03:37  pppd[8797]: pppd 2.4.4 started by root, uid 0
 12:03:37  pppd[8797]: Using interface ppp0
 12:03:37  pppd[8797]: Connect: ppp0 <--> /dev/pts/1
 12:03:37  kernel: [17185018.356000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
 12:03:37  ntpdate[8809]: can't find host ntp.ubuntu.com 
 12:03:37  ntpdate[8809]: no servers can be used, exiting
 12:03:39  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 8
 12:03:47  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 14
 12:03:48  kernel: [17185028.764000] eth0: no IPv6 routers present
 12:04:01  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 12
 12:04:08  pppd[8797]: LCP: timeout sending Config-Requests 
 12:04:08  pppd[8797]: Connection terminated.
 12:04:08  pppd[8797]: Modem hangup
 12:04:13  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 10
 12:04:13  pppd[8797]: Exit.
 12:04:13  adsl-connect: ADSL connection lost; attempting re-connection.
 12:04:13  pppd[8844]: pppd 2.4.4 started by root, uid 0
 12:04:13  pppd[8844]: Using interface ppp0
 12:04:13  pppd[8844]: Connect: ppp0 <--> /dev/pts/2
 12:04:23  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 11
 12:04:33  pppoe[8800]: Timeout waiting for PADS packets
 12:04:34  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 6
 12:04:40  dhclient: No DHCPOFFERS received.
 12:04:40  dhclient: No working leases in persistent database - sleeping.
 12:04:44  pppd[8844]: LCP: timeout sending Config-Requests 
 12:04:44  pppd[8844]: Connection terminated.
 12:04:44  pppd[8844]: Modem hangup
 12:04:48  pppoe[8846]: Timeout waiting for PADS packets
 12:04:48  pppd[8844]: Exit.
 12:04:48  adsl-connect: ADSL connection lost; attempting re-connection.
 12:04:48  pppd[8872]: pppd 2.4.4 started by root, uid 0
 12:04:48  pppd[8872]: Using interface ppp0
 12:04:48  pppd[8872]: Connect: ppp0 <--> /dev/pts/1
 12:05:19  pppd[8872]: LCP: timeout sending Config-Requests 
 12:05:19  pppd[8872]: Connection terminated.
 12:05:19  pppd[8872]: Modem hangup
 12:05:23  pppoe[8874]: Timeout waiting for PADS packets
 12:05:23  pppd[8872]: Exit.
 12:05:23  adsl-connect: ADSL connection lost; attempting re-connection.
 12:05:23  pppd[8909]: pppd 2.4.4 started by root, uid 0
 12:05:23  pppd[8909]: Using interface ppp0
 12:05:23  pppd[8909]: Connect: ppp0 <--> /dev/pts/1
 12:05:52  kernel: [17185153.644000] HDLC line discipline: version $Revision: 4.8 $, maxframe=4096
 12:05:52  kernel: [17185153.644000] N_HDLC line discipline registered.
 12:05:54  pppd[8909]: LCP: timeout sending Config-Requests 
 12:05:54  pppd[8909]: Connection terminated.
 12:05:54  pppd[8909]: Modem hangup
 12:05:59  pppd[8909]: Exit.
 12:05:59  adsl-connect: ADSL connection lost; attempting re-connection.
 12:05:59  pppd[11803]: pppd 2.4.4 started by root, uid 0
 12:05:59  pppd[11803]: Using interface ppp0
 12:05:59  pppd[11803]: Connect: ppp0 <--> /dev/pts/2
 12:05:59  pppoe[8911]: PADS: Service-Name: ''
 12:05:59  pppoe[8911]: PPP session is 3674
 12:05:59  pppoe[11805]: PADS: Service-Name: ''
 12:05:59  pppoe[11805]: PPP session is 3674 (0xe5a)
 12:05:59  pppoe[8911]: read (asyncReadFromPPP): Input/output error
 12:05:59  pppoe[8911]: Sent PADT
 12:06:30  pppd[11803]: LCP: timeout sending Config-Requests 
 12:06:30  pppd[11803]: Connection terminated.
 12:06:30  pppoe[11805]: read (asyncReadFromPPP): Session 3674: Input/output error
 12:06:30  pppoe[11805]: Sent PADT
 12:06:30  pppd[11803]: Modem hangup
 12:06:30  pppd[11803]: Exit.

``` 

These lines below are the log when I got the connection working:

```
 12:06:30  adsl-connect: ADSL connection lost; attempting re-connection.
 12:06:30  pppd[11837]: pppd 2.4.4 started by root, uid 0
 12:06:30  pppd[11837]: Using interface ppp0
 12:06:30  pppd[11837]: Connect: ppp0 <--> /dev/pts/1
 12:06:31  pppoe[11839]: PADS: Service-Name: ''
 12:06:31  pppoe[11839]: PPP session is 3681 (0xe61)
 12:06:32  pppd[11837]: PAP authentication succeeded
 12:06:32  pppd[11837]: Cannot determine ethernet address for proxy ARP
 12:06:32  pppd[11837]: local  IP address xxx.xx.xx.xx
 12:06:32  pppd[11837]: remote IP address xxx.xx.xx.x
 12:06:32  pppd[11837]: primary   DNS address 200.175.5.139
 12:06:32  pppd[11837]: secondary DNS address 200.175.182.139
 12:06:38  ddclient[11861]: SUCCESS:  updating xxxx.dnsalias.org: good: IP address set to xxx.xx.xx.xx
 12:08:30  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
 12:08:34  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
 12:08:40  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
 12:08:53  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
 12:09:07  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
 12:09:24  dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
 12:09:31  dhclient: No DHCPOFFERS received.
 12:09:31  dhclient: No working leases in persistent database - sleeping.
 12:11:28  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
 12:11:31  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 8
 12:11:39  dhclient: DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 14

```

Can anybody help me? I don't want to keep on using windows all day long... :confused: 

Thanks!!!

---

### Post by hmsf on 2007-03-05
OK, now it's working!!

But I don't know for sure what made it work...

I just uninstalled some PPP-related programs that I had to connect with my old dial-up ISP... maybe this was the problem...

---

