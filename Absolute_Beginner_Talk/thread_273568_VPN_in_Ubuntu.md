---
title: "VPN in Ubuntu?"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Olly1234 on 2006-10-08
Hello everyone, I can connect to my school's network through a VPN oonnection on Windows- I was wondering if this was also possible on Ubuntu?

---

### Post by meng on 2006-10-08
Yes. What sort of VPN software are you using on Windows? Is there VPN software for Mac users at your school? If either can connect through the Cisco client, you should download/install vpnc, it works great with the Cisco concentrators.

---

### Post by DeusEx on 2006-10-08
this script is what i use:

NOTE: it can be considered security breach because it leaves your existing  internet connection active thus connecting your company/instance network with the unsecure outside-world!

Packages: vpnc, tsclient


vpntunnel.sh (chmod 766):
```

#!/bin/bash
#
# variables
#
ROOT_UID=0			#root UID
VPN_ACCOUNT=myvpnconfig		#vpn conf file
VPNC_PATH=/etc/vpnc/		#path to vpnc
TUNNEL_DEVICE=tun0		#how ifconfig probably names the vpn tunnel
VPN_SERVER_GW=192.168.1.0	#dns route will be added to routing table
VPN_SERVER_NM=255.255.255.0	#it's netmask
TUNNEL_UP=false			#tunnel up?

#----------------------------------------------------------#
#                      functions                           #

tunnel_disconnect ()
{
#
# Disconnect VPN tunnel?
#
echo -n "Disconnect VPN tunnel? (Y/n): "
read -e YN
case $YN in
  n* | N* ) ;;
  * ) vpnc-disconnect;;
esac
}

tunnel_status ()
{
#
# Status of tunnel?
#
if ! (ifconfig |grep -q $TUNNEL_DEVICE) then
  echo "VPN tunnel $TUNNEL_DEVICE is down."
  TUNNEL_UP=false
else
  echo "VPN tunnel $TUNNEL_DEVICE is up!"
  TUNNEL_UP=true
fi
}
#                                                          #  
#----------------------------------------------------------#


#
# Run as root, of course.
#
if [ "$UID" -ne "$ROOT_UID" ]
then
  echo "Please run as Root!"
  exit
fi 

#
# If the tunnel is running, try to stop it
#
tunnel_status
if [ $TUNNEL_UP = true ]; then
  tunnel_disconnect
  tunnel_status
  # if tunnel still up there's a problem
  if [ $TUNNEL_UP = true ]; then
    echo "There was a problem with VPNC."
    echo "Could not disconnect $TUNNEL_DEVICE. Exitting..."
    exit
  fi
fi


#
# Check if vpn conf exists
#
if ! [ -e "$VPNC_PATH$VPN_ACCOUNT.conf" ]; then
  echo "Could not find $VPNC_PATH$VPN_ACCOUNT.conf!"
  exit
fi

#
# Create the VPN tunnel
#
echo "Connecting to the VPN using config '$VPN_ACCOUNT'"
vpnc-connect $VPN_ACCOUNT

#
# check if tunnel still stands
#
tunnel_status
echo "ifconfig should show a $TUNNEL_DEVICE device"
echo -n "show output of ifconfig? (y/N): "
read -e YN
case $YN in
  y* | Y* ) ifconfig;;
esac
if [ $TUNNEL_UP = false ]; then
  echo "Could not bring up the VPN tunnel. Exitting..."
  exit
fi

#
# Modify routing table
#
echo "Modifying the routing table"
route add -net $VPN_SERVER_GW netmask $VPN_SERVER_NM dev $TUNNEL_DEVICE

#
# Launch tsclient?
#
echo -n "Launch tsclient? (Y/n): "
read -e YN
case $YN in
  n* | N* ) ;;
  * ) tsclient;;
esac

tunnel_disconnect
tunnel_status
exit


```

/etc/vpnc/myvpnconfig (chown root:root):
```

IPSec gateway 123.456.789.10
IPSec ID username
IPSec secret password
Xauth username anotherusername

# OPTIONAL
# ========

#
#
# Varios options not undestood by vpnc itself but by some other scripts
#
# Target networks 123.234.210.0/24 10.1.0.0/16
# If Target networks is defined here, the default route is not replaced!

# Don't update resolv.conf though resolvconf is installed
# DNSUpdate no

```

---

