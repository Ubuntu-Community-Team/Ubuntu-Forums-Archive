---
title: "Mol and DSL networking"
date: 2007-02-11
forum: Apple PPC Users
---

### Post by Ptero-4 on 2007-02-11
Hi. I`m trying to set up OSX under mol, since I use Ethernet DSL as my internet conection, I wanted to send the internet conection to OSX (within mol) but so far it doesn`t work. Can you tell me, step by step, how to get the internet to work inside mol?

---

### Post by calum on 2007-02-13
> **Ptero-4 said:**
> Hi. I`m trying to set up OSX under mol, since I use Ethernet DSL as my internet conection, I wanted to send the internet conection to OSX (within mol) but so far it doesn`t work. Can you tell me, step by step, how to get the internet to work inside mol?

Turning that around a little, what have you tried so far to get it to work?  E.g. Have you installed the necessary MOL networking drivers from within OSX?

---

### Post by Ptero-4 on 2007-02-13
I have installed the networking drivers already. A year ago I installed mol and OSX (HD crash forced me to reinstall months later). Back then I was on dial-up and installing the networking drivers, enabling tun (in /etc/mol/molrc.net) and restarting mol was enough to get networking going. The problem now is that I`m not transferring conection from a modem to the tun driver (which simulates a router) but from a DSL router, so basically I need to ¨hook¨ the actual router to the one emulated by the tun driver. So far I also installed ipmasq and dnsmasq, The DSL router IP is 192.168.1.1 and it uses DHCP, during mol startup there´s a line saying ¨DHCP nameserver exported: 192.168.1.1¨ followed by ¨Ethernet Interface `tun-<tun0>` @ 00:00:0D:EA:dB:EE¨. The IP`s in mol are 192.168.40.2, 192.168.40.1 and 255.255.255.0, set to DHCP and client ID is empty. OSX version is 10.3.4 Panther.

Hope it`s enough info.

---

### Post by calum on 2007-02-14
> **Ptero-4 said:**
> I have installed the networking drivers already. A year ago I installed mol and OSX (HD crash forced me to reinstall months later). Back then I was on dial-up and installing the networking drivers, enabling tun (in /etc/mol/molrc.net) and restarting mol was enough to get networking going. The problem now is that I`m not transferring conection from a modem to the tun driver (which simulates a router) but from a DSL router, so basically I need to ¨hook¨ the actual router to the one emulated by the tun driver. So far I also installed ipmasq and dnsmasq, The DSL router IP is 192.168.1.1 and it uses DHCP, during mol startup there´s a line saying ¨DHCP nameserver exported: 192.168.1.1¨ followed by ¨Ethernet Interface `tun-<tun0>` @ 00:00:0D:EA:dB:EE¨. The IP`s in mol are 192.168.40.2, 192.168.40.1 and 255.255.255.0, set to DHCP and client ID is empty. OSX version is 10.3.4 Panther.

Hope it`s enough info.

Hmm, sounds like you shouldn't be too far away from getting this working, all that sounds pretty similar to my config (except I don't use DHCP on my router at home, but I do use it when I'm in the office).  I'll check my config and startup log etc. tomorrow when I'm running MOL, and see if we can figure out what the differences are.

---

### Post by calum on 2007-02-16
So, here's what I see when I run 'startmol -X':

```
Mac-on-Linux 0.9.72_pre2 [Feb 14 2007 12:13]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Loading Mac-on-Linux kernel module:
   /usr/local/lib/mol/0.9.72/modules/2.6.20-8-powerpc/mol.ko
The kernel module '/usr/local/lib/mol/0.9.72/modules/2.6.20-8-powerpc/tun.o' appears to be missing.
Running in PowerPC 7400 mode, 768 MB RAM
Timebase: 18.43 MHz, Bus: 73.72 MHz, Clock: 749 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered 
Serving VNC on port 5900
Fullscreen video on VT 9.
Could not open '/var/local/mol/console.kbd'
Video driver(s): [vnc] [console_video] 

     640* 480, depth 8,15,32   { 59.9, 72.1, 74.9, 89.9, 99.7 } Hz
     640* 480, depth 8,15   { 116.6 } Hz
     800* 600, depth 8,15,32   { 56.2, 60.3, 70.0, 72.1, 74.9, 89.9 } Hz
     800* 600, depth 8,15   { 94.8 } Hz
     800* 600, depth 8,15,32   { 99.9 } Hz
    1024* 768, depth 8,15,32   { 60.0, 70.0 } Hz
    1024* 768, depth 8,15   { 74.8 } Hz
    1024* 768, depth 8,15,32   { 75.0 } Hz
    1152* 768, depth 8,15,32   { 54.7 } Hz
    1280* 854, depth 8,15,32   { 0.0, 60.0 } Hz
    1152* 864, depth 8,15,32   { 0.0 } Hz
    1280*1024, depth 8,15,32   { 0.0 } Hz
    1440* 960, depth 8,15,32   { 0.0 } Hz
    1600*1024, depth 8,15,32   { 0.0 } Hz
    1600*1200, depth 8,15,32   { 0.0 } Hz
    1680*1050, depth 8,15,32   { 0.0 } Hz

vncvideo: vopen called
---> DHCP server not installed
Initializing IP Masquerading...done.
Restarting DNS forwarder and DHCP server: dnsmasq.
Ethernet Interface 'tun-<tun1>' @ 00:00:0D:EA:DB:EE

    ip/mask: 192.168.41.2/255.255.255.0  gw: 192.168.41.1
    broadcast: 192.168.41.255  nameserver: 192.168.41.1

OSS sound driver

    CD    /dev/cdrom       CD/DVD         <read-only>   ------ 
    Unembedded HFS+ /dev/hda3                       <rw> 76672 MB BOOT
    Unembedded HFS+ /dev/hda4                       <rw>    8 MB BOOT
------> /dev/hda5 is linux-mounted with write privileges.
Could not open '/dev/hda5' with read-write permissions
    HFS   /dev/hda6        bootstrap      <rw>    0 MB BOOT

<snip bunch of errors about everything in /dev/sdb being zero length>

No volumes found in '/dev/sdb'

SCSI devices:

    SCSI  /dev/cdrom       [CDROM/DVD driver]


>> ==================================================
>> MacOS X Boot Loader 0.9.72_pre2
>> Candidate boot volume: /mol-blk@0/disk@2:0
>> /mol-blk@0/disk@2:0,\mach_kernel (4343332 bytes)
>> /mol-blk@0/disk@2:0,\System\Library\Extensions.mkext
>> ==================================================

<*> IRQ vectorCanBeShared 3
<*> IRQ vectorCanBeShared 4
<*> IRQ vectorCanBeShared 2
<*> Block Driver v1.1
<*> SCSI driver v1.03
<*> IRQ vectorCanBeShared 6
<*> IRQ vectorCanBeShared 24
<*> MolAudio 1.2
<*> IRQ vectorCanBeShared 1
<*> IRQ vectorCanBeShared 5
<*> Ethernet driver 1.1
+ Video Driver v1.12
<*> MolEnet: Link up at 100 Mbps - Full Duplex
DHCP lease: 192.168.41.2

```

As you can see, I'm not seeing is "DHCP nameserver exported: 192.168.1.1", instead I get:
```
---> DHCP server not installed
Initializing IP Masquerading...done.
Restarting DNS forwarder and DHCP server: dnsmasq.
Ethernet Interface 'tun-<tun1>' @ 00:00:0D:EA:DB:EE
```

Are you running a DHCP server other than dnsmasq?  And do you have the lines at the end of /etc/mol/tunconfig that restart ipmasq and dnsmasq?

---

### Post by Ptero-4 on 2007-02-17
I removed the dhcp package and added the commands:
```
/etc/init.d/ipmasq restart
/etc/init.d/dnsmasq restart
```
as the two last lines of the /etc/mol/tunconfig, and then ran startmol -0 -X but it still doesn`t display the lines about the ip masquerading and dns forwarder, how do I need to add those lines.

---

### Post by calum on 2007-02-19
Hmm, those are the exact two lines I have in tunconfig, right before "exit 0".  Running out of ideas to be honest, I'm not really an expert :confused:   You might well have more luck on the [mol-users mailing list]("http://sourceforge.net/mail/?group_id=179078"), where the current maintainer hangs out and is pretty reponsive.

---

### Post by Ptero-4 on 2007-02-19
If you could post your /etc/mol/tunconfig

---

### Post by calum on 2007-02-21
> **Ptero-4 said:**
> If you could post your /etc/mol/tunconfig

Sure, here you go:
```

#!/bin/bash
###########################################################################
# Configuration of the tunN devices for usage with MOL.
#
# This script should be named /etc/mol/tunconfig (unless the default name
# has been changed with the 'tunconfig' keyword).
#
# The molrc file should contain
#
#	netdev:		tun0 -tun
#
# More information is available in the doc directory.
#
#	Usage:		tunconfig iface up|down
#
# If the linux box is configured as a firewall, the rules below might
# need some adjustments.
#
#############################################################################

PROVIDE_DHCP=yes
DNS_REDIRECT=yes	# Redirect DNS queries

#NAMESERVER=10.0.0.1

IPTABLES=/sbin/iptables
DHCPD=/usr/sbin/dhcpd3

####################################################################

TUN_DEV=$1
ACTION=$2

TUN_NUM=`echo $TUN_DEV | sed s/[^0-9]//g`
NET_NUM=`expr 40 + $TUN_NUM`
TUN_NET=192.168.$NET_NUM.0/24
TUN_HOST=192.168.$NET_NUM.1


#########################################################
# Misc Checks
#########################################################

[ $# = 2  ] || {
    echo "Usage: tunconfig iface up|down"
    exit 2
}

[ -x $DHCPD ] || {
    echo "---> DHCP server not installed" 1>&2
    PROVIDE_DHCP=no
}

[ -x $IPTABLES ] || {
    echo "---> $IPTABLES not found." 1>&2
    exit 1
}

$IPTABLES -L -n -t nat > /dev/null || exit 1


#########################################################
# Remove old (possibly stale) ruleset
#########################################################

{
    $IPTABLES -t nat -D POSTROUTING -s $TUN_NET -d ! $TUN_NET -j MASQUERADE
    $IPTABLES -t nat -D PREROUTING -p tcp -i $TUN_DEV -d $TUN_HOST --dport 53 -j mol-ns-redirect
    $IPTABLES -t nat -D PREROUTING -p udp -i $TUN_DEV -d $TUN_HOST --dport 53 -j mol-ns-redirect
    $IPTABLES -t nat -F mol-ns-redirect
} >& /dev/null


#########################################################
# Stop the DHCP server (no dynamical reconfiguration)
#########################################################

[ -f /var/run/dhcpd.pid -a "$PROVIDE_DHCP" = yes ] && {
    kill -TERM `cat /var/run/dhcpd.pid`
} > /dev/null 2>&1


#########################################################
# Bring down interface
#########################################################

[ "$ACTION" = down ] && {
    /sbin/ifconfig $TUN_DEV down
}


#########################################################
# Configure interface
#########################################################

[ "$ACTION" = up ] && {
    /sbin/ifconfig $TUN_DEV $TUN_HOST

    # the dhcpd server can get stuck if the MOL side of the
    # tun device is shutdown uncleanly
    [ "$?" != 0 ] && {
	[ -f /var/run/dhcpd.pid -a "$PROVIDE_DHCP" = yes ] && {
	    echo "killing -9 stale dhcpd server"
	    kill -9 `cat /var/run/dhcpd.pid` > /dev/null 2>&1
	} 
	/sbin/ifconfig $TUN_DEV $TUN_HOST
    }

    # masquerade the tun network
    $IPTABLES -t nat -A POSTROUTING -s $TUN_NET -d ! $TUN_NET -j MASQUERADE

    # DNS redirection
    [ "$DNS_REDIRECT" = yes -a "$PROVIDE_DHCP" = yes ] && {
	[ ! "$NAMESERVER" ] && {
	    NAMESERVER=`grep ^nameserver /etc/resolv.conf | awk -- '{ print $2 ; exit 0; }'`
	    [ ! "$NAMESERVER" ] && {
		echo "Could not determine the nameserver (localhost is used)."
		NAMESERVER=$TUN_HOST
	    }
        }
	echo "DHCP nameserver exported: $NAMESERVER"

	$IPTABLES -t nat -N mol-ns-redirect 2> /dev/null
	$IPTABLES -t nat -A mol-ns-redirect -j DNAT --to $NAMESERVER

	# redirect tcp/udp port 53 (nameserver queries)
	$IPTABLES -t nat -A PREROUTING -p tcp -i $TUN_DEV -d $TUN_HOST --dport 53 -j mol-ns-redirect
	$IPTABLES -t nat -A PREROUTING -p udp -i $TUN_DEV -d $TUN_HOST --dport 53 -j mol-ns-redirect
    }
}


#########################################################
# Start the DHCP
#########################################################

IFACES=`netstat -i | sed -n -e 's/^\(tun[0-9]\).*/\1/gp'`

if [ "$IFACES" ] ; then
    [ "$PROVIDE_DHCP" = yes ] && $DHCPD -q -cf /etc/mol/dhcpd-mol.conf $IFACES
    echo 1 > /proc/sys/net/ipv4/ip_forward
else
    $IPTABLES -t nat -X mol-ns-redirect >& /dev/null
    #echo 0 > /proc/sys/net/ipv4/ip_forward
fi

/etc/init.d/ipmasq restart
/etc/init.d/dnsmasq restart

exit 0

```

---

