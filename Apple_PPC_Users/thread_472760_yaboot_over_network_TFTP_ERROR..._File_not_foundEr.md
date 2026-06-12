---
title: "yaboot over network: TFTP ERROR... File not foundError, can't read config file"
date: 2007-06-13
forum: Apple PPC Users
---

### Post by RudeIota on 2007-06-13
I'm sure this is a configuration problem - but I'm not knowledgeable enough to know where to look.

The 'server' (eMac 1.4GHz, for test purposes) is running Edubuntu (Fiesty / 7.04) server and the client (Indigo blue iMac DV 400) is attempting to boot via LTSP. It does so via the open firmware command *boot enet:0*. Both computers are privately connected via a switch.

Previously, I had an issue getting the Indigo blue iMac DV 400 to boot at all... After clearing the NVRAM + PRAM, I've gotten to where it appears to load yaboot, but then tells me it cannot find / read the config file.

```
CLIENT: 003065daa662
SERVER: 00145111c630
Transfer FILE: yaboot.conf
TFTP ERROR response 1 File not foundError, can't read config file
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information

boot:
```

Here are the rest of my config files as they are at the moment. My dhcpd.conf file is a lightly modified version of another person's posted online. 

**/OPT/LTSP/POWERPC/BOOT/YABOOT.CONF**```
timeout=0
default=ltsp
root=enet:192.168.0.254
#root=/dev/ram


image=/ltsp/powerpc/vmlinux
device=enet:192.168.0.254
        label=ltsp
	initrd=/ltsp/powerpc/initrd.img
	initrd-size=8192
        append="quiet splash"

```

**/ETC/LTSP/DHCPD.CONF**```
ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "local";
#option domain-name-servers 0.0.0.0

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

#Mac NetBoot Options
# (these require dhcpd 3.0+)
option mac-nc-client-unknown code 220 = string;
option mac-nc-client-id code 221 = string;
option mac-version code 230 = string;
option mac-username code 232 = text;
option mac-password code 233 = text;
option mac-nb-img code 234 = string;
option mac-apps-img code 235 = string;
option mac-machine-name code 237 = text;
option mac-client-nb-img code 238 = string;

if (option mac-nc-client-id = "Apple MacNC") {
   option dhcp-max-message-size 576;
   option dhcp-parameter-request-list
                 1, # subnet mask
                 3, # routers
                 220, 221, 230, 232, 233, 234, 235, 236, 237, 238; # mac options

   # put global macnc-specific options here...
   option mac-version 0:0:0:0;
}

#subnet 192.168.0.0 netmask 255.255.255.0 {
#  range 192.168.0.14 192.168.0.253;
#  option routers 192.168.0.10;
#}

# To netboot, you can either specify the hosts explicitly, like so:
#host debian-installer {
#  hardware ethernet 00:05:02:B1:7F:A9;
#  fixed-address 192.168.0.5;
# Or hand out boot boot information dynamically:
subnet 192.168.0.0 netmask 255.255.255.0 {
  range dynamic-bootp 192.168.0.14 192.168.0.253;

  option routers 192.168.0.254;
  filename "/ltsp/powerpc/yaboot";  # relative to the /tftpboot directory, due to the -s option
  option root-path "/opt/ltsp/powerpc";
  server-name "server";
  server-identifier 192.168.0.254; # your tftp server
  next-server 192.168.0.254; # your tftp server
}

```

**/ETC/EXPORTS**```
/opt/ltsp       *(ro,no_root_squash,async)
```


My ultimate goal is to have a PC server and PPC iMac clients (300-400MHz) for a school. For testing, my server will be PPC until I get most of the variables solved, at which point I will setup a PC server to do the same job. The school's network runs on Cisco equipment, so I'll be trying to get this work in parallel with the existing network, gateway/dhcp server and switches... One hurdle at a time though. :D

This thread is a spin-off to the following thread, as events have taken a different (positive) direction: [http://ubuntuforums.org/showthread.php?p=2774500](http://ubuntuforums.org/showthread.php?p=2774500)

Any help - no matter how small - would be awesome. ;)

---

### Post by RudeIota on 2007-06-20
I haven't had any luck yet. Any ideas on what's wrong with my config floating around out there?

---

