---
title: "[openvpn] VPN Routing with Android? Server side or Clientside issue?"
date: 2017-02-08
forum: Any Other OS
---

### Post by wpearsall on 2017-02-08
Hi guys

I've got an android device... when i connect to vpn with it, via 4g, it shows my home network ip address (img 6), and traffic is routed via my server as it should be.  So no worries there.

However, when i connect to VPN via o2 wifi (img 1), it is showing the o2wifi ip address - 46.x.x.x (img 4)

I can still browse my network (img 3). i noticed on the log of the vpn client theres a conflict with the keys (see top img 5).

Is this an android issue, or is this a serverside issue? or even a o2 wifi issue (i havent tried on other wifi networks yet)

My LAPTOP works fine on other networks, but im looking to upload photos etc to my server. so ideally want to ensure the connection is secure.

anyone had this issue?

I know theres the issue of TAP not being valid on unrooted android, is this likely to cause an issue?

If I connect my laptop to my phone via hotspot (no vpn connection on mobile)  and then initiate a vpn connection to my home network via the mobile hotspot, all traffic is routed via vpn too.  HOWEVER, if I setup a vpn on the mobile, and hotspot into mobile, the hotspot uses the 4g data, and doesnt use the tunnel for connected device, but does use it for the programs on the mobile.

this is the android vpn client:
[https://play.google.com/store/apps/details?id=it.colucciweb.openvpn](https://play.google.com/store/apps/details?id=it.colucciweb.openvpn)

server vpn conf
```

mode server
tls-server


local x.x.x.x## ip/hostname of server
port xxxx ## default openvpn port
proto udp


#bridging directive
dev-type tap
dev tap0 ## If you need multiple tap devices, add them here
script-security 2 ## allow calling up.sh and down.sh
up "/etc/openvpn/up.sh br0 tap0 1500"
down "/etc/openvpn/down.sh br0 tap0"


persist-key
persist-tun


#certificates and encryption
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh2048.pem
tls-auth ta.key 0 # This file is secret


cipher AES-256-CBC #BF-CBC        # Blowfish (default)
comp-lzo yes
#push 'comp-lzo yes'


#DHCP Information
ifconfig-pool-persist ipp.txt
server-bridge 192.168.1.200 255.255.255.0 192.168.1.201 192.168.1.210
push "dhcp-option DNS 192.168.1.254"
push "dhcp-option DOMAIN xxxxxxx.com"
max-clients 10 ## set this to the max number of clients that should be connected at a time
# force internet traffic through the vpn tunnel
push "redirect-gateway autolocal" 
push "comp-lzo"


#log and security
user nobody
group nogroup
keepalive 10 120
status openvpn-status.log
verb 3

```

client vpn conf

```

### Client configuration file for OpenVPN


# Specify that this is a client
client


# Bridge device setting
dev-type tap
dev tap0


# Host name and port for the server (default port is 1194)
# note: replace with the correct values your server set up
remote xxxx.com xxxx


# Client does not need to bind to a specific local port
nobind


# Keep trying to resolve the host name of OpenVPN server.
## The windows GUI seems to dislike the following rule. 
##You may need to comment it out.
resolv-retry infinite


# Preserve state across restarts
persist-key
persist-tun


# SSL/TLS parameters - files created previously
ca ca.crt
cert client.crt
key client.key


# Since we specified the tls-auth for server, we need it for the client
# note: 0 = server, 1 = client
tls-auth ta.key 1


# Specify same cipher as server
#cipher BF-CBC
cipher AES-256-CBC


# Use compression
comp-lzo


# Log verbosity (to help if there are problems)
verb 3

```

---

### Post by howefield on 2017-02-08
Thread moved to the "*Any Other OS*" forum.

---

### Post by wpearsall on 2017-02-08
> **howefield said:**
> Thread moved to the "*Any Other OS*" forum.

Actually, im leaning to thinking this is actually an ANDROID issue - and not the server (Ubuntu / OpenVPN) issue...

I can see a few tutorials (IE: [https://digiex.net/threads/android-phone-as-a-vpn-gateway-bypass-tethering-block.13974/](https://digiex.net/threads/android-phone-as-a-vpn-gateway-bypass-tethering-block.13974/) ) to share the hotspot, but i think the big issue is that i've not rooted my android device ( it's in warranty etc, so leaning against it, but i am tempted to play with one of the many devices i have lay around - gathering dust ;) - i've got an (old but half decent) tablet with wifi, ethernet, real usb ports, micro sd slots  mini hdmi out, (and a broken screen - *kids*) - so might have a bash with it connected to my tv / mouse / keyboard.

---

