---
title: "Detailed enumeration of default services"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by High_Yield on 2008-01-03
Hi-

I'm looking for a clean, official list and explanation of each of the the "services" which are shown when executing a "ps -ax" command in a terminal.

For example, I don't know what "kgameportd" really is, but I assume it is a program monitoring a game port.  Which is fine, but:
a) I don't use a game port and it's disabled in my bios
b) It takes up very little memory and CPU time, but is a program and will receive cpu slices I assume
c) Because of a and b above, I want to turn "kgameportd" off

There are many other services running which make no sense to me, like vino-session, etc..

So, is there a nice listing of each default service with a description of what it does for Gutsy?  Something like this [http://forums.fedoraforum.org/showthread.php?t=102853]("http://forums.fedoraforum.org/showthread.php?t=102853") only official from ubuntu ?

I really want to know what is running on my PC, why, what it does, and how to turn it off if need be.

<snippet from link above>
Last thing I'm going to say is don't be afraid to disable services; The worst that can happen is something won't work and on reboot you simply re-enable it.

Priorities:
L = Only laptops need this.
D = Only Desktops need this.
A = All need this! Keep it enabled.
HR = Highly Recommended! But not absolutely needed. Better to keep enabled.
R = Not needed at all but nice to have.
NN = Not needed, disable at will. Keep enabled if you're using things itn it's description, though.

[ service ] : [ Description ] : [ Priority ]

NetworkManager : Best network selection : L
acpid : Power managment : HR
anacron : More Cron management : HR
apmd : For laptop's battery monitoring : L
atd : Similar to Cron's functions : NN
autofs : Auto-detect/mount filesystems : HR
ahavi-daemon : Zeroconf stuff : NN
avavi-dnsconfd : DNS Zeroconf stuff : NN
bluetooth : needed for bluetooth wireless devices to work : NN
btseed : BitTorrent Seeding : NN
bttrack : BitTorrent tracking : NN
cpuspeed : dynamic CPU speed daemon : L
crond : Automated tasks : A
cups : Central Unix Printing System : HR
cups-config-daemon: Central Unix Printing System through D-Bus : HR
dc_client : SSL session cache client proxy : NN
dc_server : SSL session server : NN
dhcdbd : D-BUS control of ISC DHCP client : NN
diskdump : Create Dump files if system crashes : NN
firstboot : First-boot configuration utility : NN after your first boot
gpm : Mouse support in terminals (runlevel 3) : NN
haldaemon : Hardware Abstraction Layer : A
hplip : HP Printer service : A for all that use HP Printers
httpd : Apache's Web server : NN
iptables : Firewall. Plain & Simple. : A
isdn : Integrated Services Digital Network : NN
kudzu : hardware probe at startup, only if you're changing hardware : NN
lirc : Infrared controls : NN
lisa : Similar to "Network Neighbourhood" : R
lm_sensors : System sensor monitoring : A that have CPU / fan sensors
mdnsresponder : Howl network : NN
messagebus : The system-messenger dbus : A
mysqld : MySQL's database server : NN
named : BIND DNS server : NN
netdump : netconsole & netcrashdump utility : NN
netfs : Network filesystems : HR
netplugd : Dynamic network managment : NN
network : Network connectivity & services : A
nifd : Network interface monitor daemon : NN
nscd : Name service caching daemon : NN
ntpd: Network Time Protol : NN
nfs + nfslock : NFS servers : NN
portmap : RPC connections, like NFS / NIS : NN
pcmcia : Laptop PCMCIA : L
redahead & readahead_early : Caches boot services & therefore decreases boot time : A
rpcgssd : NFS v4 connection helper : NN
rpcidmapd : NFS v4 connection helper : NN
rpcsvcgssd : NFS v4 connection helper : NN
saslauthd : plaintext auth in cyrus-sasl : NN
sendmail : Mail server, although there are better ones out there I'd disable this one and install something like squirrelmail. Either way, it's enabled by default and can be disabled. : NN
smb : The Samba or SMB server : NN
snmpd : Simple Network Management Protocol : NN
snmptrapd : Simple Network Management Protocol : NN
sshd: remote SSH server : NN
syslog : System & Kernel logger. VITAL!: A
wpa_supplicant : Wireless auth helper : A who use wireless
xfs : X font server. Vital to graphic functioning!: A
xinetd : the replacement for inted, xinetd is a internet superdaemon. HR

ati-fglrx / nvidia-glx : Livna graphics drivers services : HR

Services you want to disable *should* be disabled in runlevels 3, 4 and 5 (the default for editing when using chkconfig [service] [ on | off ])
</snippet from link above>

Thanks - B

---

### Post by fiddledd on 2008-01-03
Here's a link to an explanation of most services:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) 

There's also another link that I can't for the life me remember, if I remember I'll post that too.

---

### Post by High_Yield on 2008-01-04
Thanks fiddledd...

Will review.  I had already found info on sysv-rc-conf, and done some damage ;( but - am learning.

---

