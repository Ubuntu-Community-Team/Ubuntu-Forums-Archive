---
title: "Vpn - pptp"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by mirec on 2006-10-19
Hello!

I need to connect to a vpn network, trought pptp. I installed pptpconfig_20060821-0_all.deb and insetred the required data into the client, but its not working and I become this log:


pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.12 2006/08/21 06:19:12
# pptp --version
pptp: unrecognized option `--version'
pptp version 1.7.0
Usage:
  pptp <hostname> [<pptp options>] [[--] <pppd options>]

Or using pppd's pty option:
  pppd pty "pptp <hostname> --nolaunchpppd <pptp options>"

Available pptp options:
  --phone <number>      Pass <number> to remote host as phone number
  --nolaunchpppd        Do not launch pppd, for use as a pppd pty
  --quirks <quirk>      Work around a buggy PPTP implementation
                        Currently recognised values are BEZEQ_ISRAEL only
  --debug               Run in foreground (for debugging with gdb)
  --sync                Enable Synchronous HDLC (pppd must use it too)
  --timeout <secs>      Time to wait for reordered packets (0.01 to 10 secs)
  --nobuffer            Disable packet buffering and reordering completely
  --idle-wait           Time to wait before sending echo request
  --max-echo-wait               Time to wait before giving up on lack of reply
  --logstring <name>    Use <name> instead of 'anon' in syslog messages
  --localbind <addr>    Bind to specified IP address instead of wildcard
  --loglevel <level>    Sets the debugging level (0=low, 1=default, 2=high)
# pppd --version
pppd version 2.4.4b1
# uname -a
Linux mirec-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 G NU/Linux
# modinfo ppp_mppe || modinfo ppp_mppe_mppc
filename:       /lib/modules/2.6.15-27-386/kernel/drivers/net/ppp_mppe.ko
author:         Frank Cusack <fcusack@fcusack.com>
description:    Point-to-Point Protocol Microsoft Point-to-Point Encryption supp ort
license:        Dual BSD/GPL
alias:          ppp-compress-18
version:        1.0.2
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
depends:        ppp_generic
srcversion:     6B88E623CA7C4D7FE2F11FA
# grep mppe /proc/modules
Array
(
    [name] => tunelName
    [server] => server
    [domain] => (hidden by pptpconfig)
    [username] => login
    [password] => (hidden by pptpconfig)
    [pppd-options] => noipdefault 50
    [pptp-options] =>
    [resolv] =>
    [dns-options] =>
    [routing] => routing_interface_only
    [usepeerdns] => 1
    [require-mppe] =>
    [nomppe-40] =>
    [nomppe-128] =>
    [refuse-eap] =>
    [mppe-stateful] =>
    [autostart] =>
    [iconify] =>
    [persist] =>
    [debug] => 1
    [client-to-lan] =>
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xx.x    0.0.0.0         zzz.zzz.zzz.z   U     0      0        0 eth0
0.0.0.0         yyy.yyy.yy.y    0.0.0.0         UG    0      0        0 eth0
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug           # (from /etc/ppp/peers/tunelName)
updetach                # (from command line)
logfd 1         # (from command line)
linkname tunelName               # (from /etc/ppp/peers/tunelName)
dump            # (from /etc/ppp/peers/tunelName)
noauth          # (from /etc/ppp/options.pptp)
refuse-chap             # (from /etc/ppp/options.pptp)
refuse-mschap           # (from /etc/ppp/options.pptp)
refuse-eap              # (from /etc/ppp/options.pptp)
name server\\login           # (from /etc/ppp/peers/tunelName)
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xx.x    0.0.0.0         zzz.zzz.zzz.z   U     0      0        0 eth0
0.0.0.0         yyy.yyy.yy.y    0.0.0.0         UG    0      0        0 eth0
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1
start failed: SIGUSR1

The authenticatio of the vpn network is mschap-v2.

---

