---
title: "US Medical company &quot;Lilly&quot; on my computer? firewall help and gaim help plz"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by erp2 on 2006-12-31
Hello im pretty nooby on ubuntu and this. Im from sweden and have been on meds on a mental hospital...anyway thats behind me now...i thought.....i just looked up this IP, apparently belonging to the company, Lilly, who were behind my meds... with firestarter. what were they doing on my computer? and is it normal that the computer constantly sends and receives packets. it does that constantly, and i have no azureus or such. strange? how do i stop those packets its constantly sending 2-5 KB/s. also im constantly receiving packets, but that is maybe normal. What are Lilly doin on my computer? How can i stop any intruders or what it is? Its pretty strange that they connect to me...

Source	TTL	Address Type	Record Type1	Resolution
40.24.6.209.in-addr.arpa.	86155	IN	PTR	209-6-24-40.c3-0.sbo-ubr2.sbo.ma.cable.rcn.com.
24.6.209.in-addr.arpa.	86155	IN	NS	auth1.dns.rcn.net.
24.6.209.in-addr.arpa.	86155	IN	NS	auth2.dns.rcn.net.
24.6.209.in-addr.arpa.	86155	IN	NS	auth3.dns.rcn.net.
24.6.209.in-addr.arpa.	86155	IN	NS	auth4.dns.rcn.net.


OrgName:    Eli Lilly and Company 
OrgID:      ELILIL
Address:    Lilly Corporate Center
City:       Indianapolis
StateProv:  IN
PostalCode: 46285
Country:    US

NetRange:   40.0.0.0 - 40.255.255.255 
CIDR:       40.0.0.0/8 
NetName:    LILLY-NET
NetHandle:  NET-40-0-0-0-1
Parent:     
NetType:    Direct Assignment
NameServer: DNS1I.XH1.LILLY.COM
NameServer: NS1.IQUEST.NET
NameServer: AUTH40.NS.UU.NET
NameServer: AUTH62.NS.UU.NET
Comment:    
RegDate:    1991-04-23
Updated:    2001-07-17

RTechHandle: ZE16-ARIN
RTechName:   Eli Lilly and Company 
RTechPhone:  +1-317-277-7000
RTechEmail:  [email]hostmaster@lilly.com[/email] 

# ARIN WHOIS database, last updated 2006-12-30 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

also, when i try to access IRC from gaim, its like nothing happens, it the connection only get to the half, . plz help?

---

### Post by Sef on 2006-12-31
> i just looked up this IP, apparently belonging to the company, Lilly, who were behind my meds... with firestarter. what were they doing on my computer?
> What are Lilly doin on my computer?

Have you ever gone to their website?  If yes, then likely there is a cookie from them on your site.

> and is it normal that the computer constantly sends and receives packets.

Yes it is normal.  

> How can i stop any intruders or what it is?

Edit > Preferences > Privacy > Cookes > set Keep until:  I close firefox

That way when you close firefox, the cookies on your computer will be deleted.

---

### Post by erp2 on 2006-12-31
Well, the thing is ive been to their site some time ago but since then my IP has changed several times and i have removed windows and installed ubuntu, I think you meant Firefox when i said Firestarter, but firestarter is a firewall, not a surf program. anyway, i got the typ to install iptables to ban their IP and i will.

---

### Post by kvonb on 2006-12-31
Evil US drug corporations, you are now their slave!

I would block their IP in Firestarter, goto the "policy" tab, change the drop box from "Inbound traffic policy" to "outbound traffic policy", right click in the "Deny connections to host" box and select "add rule", and enter their ip range as so: 209.6.24.1/24, that will block their entire range.

Also my system doesn't constantly send/receive packets although I connect through my server.  The server "blips" now and then when no-one is using it, but no constant up/download!

Close ALL apps on your computer and see if it still sends/receives.  Are you on a local network or does your computer connect directly to the Internet?

Open a terminal, and type in:

> ps uax > ~/Desktop/processlist.txt

That will show ALL processes that are running, look through it and see if there is anything that looks out of place.  Also you could post the file processlist.txt here and someone (I will if I get back in time) will have a look and let you know if everything is OK.

Regards, KEv :)

---

### Post by steve.horsley on 2006-12-31
It is not normal for the PC to be sending and receiving all the time. How do you know you are sending and receivng all the time - what app tells you that?

The output of this command:
sudo netstat -plantu
might be interesting, although if you have been compromised, it may hide the process and open sockets that it's using. Capturing some of the traffic with Ethereal or Wireshark (it changed its name) may also be interesting, but only if you are familiar with networking.

---

### Post by erp2 on 2006-12-31
> **kvonb said:**
> Evil US drug corporations, you are now their slave!

I would block their IP in Firestarter, goto the "policy" tab, change the drop box from "Inbound traffic policy" to "outbound traffic policy", right click in the "Deny connections to host" box and select "add rule", and enter their ip range as so: 209.6.24.1/24, that will block their entire range. ok, thanks
> 
Close ALL apps on your computer and see if it still sends/receives.  Are you on a local network or does your computer connect directly to the Internet? cable, i closed all and it only receives packets now. so maybe thats normal for cable, i dunno 
> 
Open a terminal, and type in:

That will show ALL processes that are running, look through it and see if there is anything that looks out of place.  Also you could post the file processlist.txt here and someone (I will if I get back in time) will have a look and let you know if everything is OK.

Regards, KEv :) thanks mate, i tried to close all programs seemingly open. 

ok, here is the process.txt

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2640   564 ?        S    15:26   0:00 init [2]         
root         2  0.0  0.0      0     0 ?        S    15:26   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   15:26   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    15:26   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   15:26   0:01 [events/0]
root         6  0.0  0.0      0     0 ?        S<   15:26   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   15:26   0:00 [kthread]
root        10  0.0  0.0      0     0 ?        S<   15:26   0:00 [kblockd/0]
root        11  0.0  0.0      0     0 ?        S<   15:26   0:00 [kacpid]
root       135  0.0  0.0      0     0 ?        S    15:26   0:00 [pdflush]
root       136  0.0  0.0      0     0 ?        S    15:26   0:00 [pdflush]
root       138  0.0  0.0      0     0 ?        S<   15:26   0:00 [aio/0]
root       727  0.0  0.0      0     0 ?        S<   15:26   0:00 [kseriod]
root       137  0.0  0.0      0     0 ?        S    15:26   0:00 [kswapd0]
root      1762  0.0  0.0      0     0 ?        S<   15:26   0:00 [ata/0]
root      1763  0.0  0.0      0     0 ?        S<   15:26   0:00 [ata_hotplug/0]
root      1767  0.0  0.0      0     0 ?        S<   15:26   0:00 [scsi_eh_0]
root      1768  0.0  0.0      0     0 ?        S<   15:26   0:00 [scsi_eh_1]
root      1921  0.0  0.0      0     0 ?        S<   15:26   0:00 [khubd]
root      1948  0.0  0.0      0     0 ?        S    15:26   0:00 [khpsbpkt]
root      1958  0.0  0.0      0     0 ?        S    15:26   0:00 [knodemgrd_0]
root      2046  0.0  0.0      0     0 ?        S    15:26   0:01 [kjournald]
root      2273  0.0  0.1  10996  1204 ?        S<s  15:26   0:00 /sbin/udevd --daemon
root      3090  0.0  0.0      0     0 ?        S    15:26   0:00 [shpchpd_event]
root      3170  0.0  0.0      0     0 ?        S    15:26   0:00 [saa7134[0]]
root      3225  0.0  0.0      0     0 ?        S<   15:26   0:00 [scsi_eh_2]
root      3226  0.0  0.0      0     0 ?        S<   15:26   0:00 [usb-storage]
dhcp      3736  0.0  0.0   8828   992 ?        S<s  15:26   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
root      4234  0.0  0.1   7600  1496 ?        Ss   15:26   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4354  0.0  0.0   4812   520 ?        Ss   15:26   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4356  0.0  0.1   3784  1628 ?        Ss   15:26   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      4680  0.0  0.2  52540  2148 ?        Ss   15:26   0:00 /usr/sbin/gdm
root      4697  0.0  0.2  60164  3032 ?        S    15:26   0:00 /usr/sbin/gdm
root      4704 11.7  3.9  77740 40492 tty7     Ss+  15:26  25:54 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
hplip     4723  0.0  0.1  23108  1044 ?        Ssl  15:26   0:00 /usr/sbin/hpiod
hplip     4727  0.0  0.6  48176  6816 ?        S    15:26   0:00 python /usr/sbin/hpssd
cupsys    4784  0.0  0.1  27528  1992 ?        Ss   15:26   0:00 /usr/sbin/cupsd
104       4803  0.0  0.0   8580   956 ?        Ss   15:26   0:00 /usr/bin/dbus-daemon --system
108       4818  0.0  0.5  18940  5684 ?        Ss   15:26   0:01 /usr/sbin/hald
root      4819  0.0  0.1   9072  1088 ?        S    15:26   0:00 hald-runner
108       4824  0.0  0.0   9268   840 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-acpi
108       4828  0.0  0.0   9272   848 ?        S    15:26   0:02 /usr/lib/hal/hald-addon-keyboard
108       4832  0.0  0.0   9268   844 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-keyboard
108       4889  0.0  0.0   9268   840 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-keyboard
108       4895  0.0  0.0   9268   872 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
108       4896  0.0  0.0   9268   868 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
108       4898  0.0  0.0   9272   872 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
108       4899  0.0  0.0   9268   864 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
108       4901  0.0  0.0   9268   868 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
108       4902  0.0  0.0   9268   864 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
108       4904  0.0  0.0   9272   868 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
108       4905  0.0  0.0   9268   868 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
108       4907  0.0  0.0   9268   904 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
108       4908  0.0  0.0   9268   904 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
108       4910  0.0  0.0   9268   904 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
108       4911  0.0  0.0   9272   904 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-storage
root      4951  0.0  0.0   2624   260 ?        SNs  15:26   0:00 /usr/sbin/powernowd -q
root      5003  0.0  0.0   6184   740 ?        Ss   15:26   0:00 hcid: processing events
root      5007  0.0  0.0   3732   484 ?        Ss   15:26   0:00 /usr/sbin/sdpd
root      5025  0.0  0.0      0     0 ?        S<   15:26   0:00 [krfcommd]
root      5038  0.0  0.0   2700   304 ?        Ss   15:26   0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
daemon    5072  0.0  0.0   9016   392 ?        Ss   15:26   0:00 /usr/sbin/atd
root      5085  0.0  0.0  11428   884 ?        Ss   15:26   0:00 /usr/sbin/cron
root      5161  0.0  0.0   2632   524 tty1     Ss+  15:26   0:00 /sbin/getty 38400 tty1
root      5162  0.0  0.0   2636   528 tty2     Ss+  15:26   0:00 /sbin/getty 38400 tty2
root      5163  0.0  0.0   2636   524 tty3     Ss+  15:26   0:00 /sbin/getty 38400 tty3
root      5164  0.0  0.0   2632   528 tty4     Ss+  15:26   0:00 /sbin/getty 38400 tty4
root      5165  0.0  0.0   2632   528 tty5     Ss+  15:26   0:00 /sbin/getty 38400 tty5
root      5166  0.0  0.0   2636   528 tty6     Ss+  15:26   0:00 /sbin/getty 38400 tty6
rot       5177  0.0  1.2  98204 12448 ?        Ss   15:27   0:00 x-session-manager
rot       5219  0.0  0.0  20144   808 ?        Ss   15:27   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
rot       5222  0.0  0.0  10080   684 ?        S    15:27   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
rot       5223  0.0  0.0   8448   980 ?        Ss   15:27   0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
rot       5225  0.0  0.5  24764  5416 ?        S    15:27   0:02 /usr/lib/libgconf2-4/gconfd-2 5
rot       5228  0.0  0.0   8732   816 ?        S    15:27   0:00 /usr/bin/gnome-keyring-daemon
rot       5230  0.0  0.3  27064  3700 ?        Ss   15:27   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
rot       5232  0.0  1.7 234212 17904 ?        Sl   15:27   0:04 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID:GNOME_SettingsDaemon --oaf-ior-fd=25
rot       5538  0.5  1.1  63588 11432 ?        Ss   15:27   1:08 /usr/bin/metacity --sm-client-id=default0
rot       5543  0.2  2.3 136724 24152 ?        Ssl  15:27   0:33 gnome-panel --sm-client-id default1
rot       5545  0.2  4.2 227972 43964 ?        Ssl  15:27   0:30 nautilus --no-default-window --sm-client-id default2
rot       5550  0.0  0.5  98236  6088 ?        Sl   15:27   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=31
rot       5551  0.1  1.1 110264 11568 ?        Ss   15:27   0:14 gnome-volume-manager --sm-client-id default4
rot       5560  0.0  1.4 114128 14632 ?        Ss   15:27   0:01 update-notifier
rot       5569  0.1  0.9 141968 10152 ?        Ss   15:27   0:20 gnome-cups-icon --sm-client-id default3
rot       5572  0.0  0.6  96868  6852 ?        Ss   15:27   0:00 gnome-power-manager
rot       5574  0.0  1.0 115128 10800 ?        Sl   15:27   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=33
rot       5593  0.0  0.0   8548   864 ?        S    15:27   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
rot       5595  0.0  2.1 242712 21632 ?        S    15:27   0:01 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=37
rot       5597  0.0  1.2 118932 13356 ?        S    15:27   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=38
rot       5615  0.0  0.3  78640  3700 ?        Ss   15:28   0:05 gnome-screensaver
rot       7890  0.0  1.1  85780 12012 ?        S    15:36   0:04 /usr/lib/notification-daemon/notification-daemon
syslog    8051  0.0  0.0   6952   700 ?        SNs  15:36   0:00 /sbin/syslogd -u syslog
rot      12931  0.5  1.6 128248 16912 ?        Sl   19:04   0:00 gnome-terminal
rot      12934  0.0  0.0   9568   744 ?        S    19:04   0:00 gnome-pty-helper
rot      12935  0.1  0.3  13412  3792 pts/0    Ss   19:04   0:00 bash
rot      13050  0.0  0.1   8748  1116 pts/0    R+   19:06   0:00 ps uax

---

### Post by erp2 on 2006-12-31
> **steve.horsley said:**
> It is not normal for the PC to be sending and receiving all the time. How do you know you are sending and receivng all the time - what app tells you that?
 I watched Network Tools, Devices, Interface statistics for my ethernet card, but your right it only says received and transmitted packets, not sent.
> 
The output of this command:
sudo netstat -plantu
might be interesting, although if you have been compromised, it may hide the process and open sockets that it's using. Capturing some of the traffic with Ethereal or Wireshark (it changed its name) may also be interesting, but only if you are familiar with networking. well, i guess id go with wireshark, or not, im quite new to theese depths. ive only swimmed the surface till now...who knows what lurks beneath me? :D.

well, idontknow but ill just post the netstat list aswell and then go and hide myself in the woods with some aluminium foil wrapped to my head...

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:46162         0.0.0.0:*               LISTEN     4723/hpiod
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4784/cupsd
tcp        0      0 127.0.0.1:46106         0.0.0.0:*               LISTEN     4727/python
tcp        0      0 **.***.***.**:46226    66.249.93.147:80        ESTABLISHED13985/firefox-bin
tcp        0      0 **.***.***.**:37957    66.249.93.99:80         ESTABLISHED13985/firefox-bin
tcp        0      0 127.0.0.1:46162         127.0.0.1:59448         ESTABLISHED4723/hpiod
tcp        0      0 127.0.0.1:59448         127.0.0.1:46162         ESTABLISHED4727/python
udp        0      0 0.0.0.0:68              0.0.0.0:*                          3736/dhclient3


i hid my IP in stat above.. lilly, connected to my port: 27589  is that strange, via UDP and TCP, is that normal?

Well, Happy New Year to all of u anyways, :KS

---

### Post by steve.horsley on 2006-12-31
I don't see anything bad in your netstat output. The only listening ports are listening on 127.0.0.1 only so they are not publicly accessible. The only outgoing connections are from firefox.

> lilly, connected to my port: 27589 is that strange, via UDP and TCP, is that normal?
I don't understand what you're saying here. But I don't see any mention of lilly or port 27589 in there.

---

### Post by erp2 on 2006-12-31
> **steve.horsley said:**
> I don't see anything bad in your netstat output. The only listening ports are listening on 127.0.0.1 only so they are not publicly accessible. The only outgoing connections are from firefox.


I don't understand what you're saying here. But I don't see any mention of lilly or port 27589 in there.

oh that Lilly info was from Firestarters Events list, dont know how to copy that though. thanks anyway.

---

### Post by kvonb on 2006-12-31
Have you ran ANY bittorrent client EVER on your computer, even when you had Windows on there?  That would explain the activity (although it is a bit strange that Lilly is showing up!).  I use Azureus on my server and even when it has been closed for a week I still get clients trying to connect, it's normal as you are still registered in the databases of clients.  What I did is changed Azureus to use only 2 ports, one for incoming, and one for outgoing, that way you know if the connection is just for Azureus.  There is also a nice little prog called "etherape", you can install it from "Add/Remove" on your menu, but install both and use the "Etherape as root" one, it will show you a graphical representation of all connections.  Also you could ask someone you trust who has Linux to do a nessus scan of your system from the net, that will show up ANY open ports and services!  Also send Lilly an e-mail (from a public account like hotmail etc') asking them why they are connecting to your computer and give them times and other info, maybe they have been hacked!

---

### Post by erp2 on 2007-01-10
Good point, might be the jolly torrent tailfire, thanks alot for the tips, help and recommendation, kvonb and y'all.

---

