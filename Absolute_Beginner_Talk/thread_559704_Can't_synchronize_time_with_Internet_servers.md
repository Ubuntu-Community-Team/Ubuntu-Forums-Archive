---
title: "Can't synchronize time with Internet servers"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2007-09-25
I've read a few threads here about trying to get the system clock to sync with Internet servers, and they all seem to go into "nightmare territory" (by my definition).  I don't know why this is... if it's not ready, maybe it shouldn't be an option in the GUI!

That said, here's my pertinent info:

> mjpatey@shekkers:~$ ps aux | grep ntpd
ntp      21247  0.0  0.0   4256  1248 ?        Ss   13:34   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 112:120 -g
mjpatey  21353  0.0  0.0   2884   764 pts/0    R+   13:36   0:00 grep ntpd

and my ntp.conf:

```
# /etc/ntp.conf, configuration for ntpd

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).

# By default, exchange time with everybody, but don't allow configuration.
# See /usr/share/doc/ntp-doc/html/accopt.html for details.
restrict default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1 nomodify

# Clients from this (example!) subnet have unlimited access,
# but only if cryptographically authenticated
#restrict 192.168.123.0  mask  255.255.255.0 notrust

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet,
# de-comment the next lines. Please do this only if you trust everybody
# on the network!
#disable auth
#broadcastclient
server ntp.cmr.gov
```

I've now selected all US servers as well as Eastern Canadian ones (because I'm on the East Coast of the US), and nothing is happening.  How often does it check with servers to update?

-Mark

---

### Post by gareththered on 2007-09-25
Did you configure this by using the GUI (i.e. right click on the time and choose´Adjust Date & Time´) or did you modify ntp.conf manually?
What does```
grep ntp /var/log/daemon.log
``` say?

---

### Post by mjpatey on 2007-09-25
I hope this is what you asked for:

> Sep 21 19:44:59 shekkers NetworkManager: <information>^Istarting... 
Sep 21 19:45:00 shekkers avahi-daemon[5210]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Sep 21 19:45:00 shekkers avahi-daemon[5210]: Successfully dropped root privileges.
Sep 21 19:45:00 shekkers avahi-daemon[5210]: avahi-daemon 0.6.17 starting up.
Sep 21 19:45:00 shekkers avahi-daemon[5210]: Successfully called chroot().
Sep 21 19:45:00 shekkers avahi-daemon[5210]: Successfully dropped remaining capabilities.
Sep 21 19:45:00 shekkers avahi-daemon[5210]: No service found in /etc/avahi/services.
Sep 21 19:45:00 shekkers avahi-daemon[5210]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.11.
Sep 21 19:45:00 shekkers avahi-daemon[5210]: New relevant interface eth0.IPv4 for mDNS.
Sep 21 19:45:00 shekkers avahi-daemon[5210]: Network interface enumeration completed.
Sep 21 19:45:00 shekkers avahi-daemon[5210]: Registering new address record for fe80::20b:6aff:fece:96fd on eth0.*.
Sep 21 19:45:00 shekkers avahi-daemon[5210]: Registering new address record for 192.168.1.11 on eth0.IPv4.
Sep 21 19:45:00 shekkers avahi-daemon[5210]: Registering HINFO record with values 'I686'/'LINUX'.
Sep 21 19:45:00 shekkers avahi-daemon[5210]: Server startup complete. Host name is shekkers.local. Local service cookie is 1004800509.
Sep 21 19:45:05 shekkers nfsd[5471]: nfssvc: writing fds to kernel failed: errno 0 (Success)
Sep 21 19:45:05 shekkers nfsd[5471]: nfssvc: writing fds to kernel failed: errno 0 (Success)
Sep 21 19:45:07 shekkers rpc.statd[5566]: Version 1.0.11 Starting
Sep 21 19:45:08 shekkers hcid[5595]: Bluetooth HCI daemon
Sep 21 19:45:08 shekkers NetworkManager: <debug info>^I[1190418308.654998] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Sep 21 19:45:08 shekkers hcid[5595]: Starting SDP server
Sep 21 19:45:25 shekkers hald: mounted /dev/sda1 on behalf of uid 1000
Sep 21 19:45:28 shekkers NetworkManager: <information>^IUpdating allowed wireless network lists. 
Sep 21 19:45:28 shekkers NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Sep 24 01:04:21 shekkers NetworkManager: <debug info>^I[1190610261.259954] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3110_noserial'). 
Sep 24 01:04:21 shekkers NetworkManager: <debug info>^I[1190610261.368455] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3110_noserial_if0'). 
Sep 24 01:04:21 shekkers NetworkManager: <debug info>^I[1190610261.379058] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3110_noserial_usbraw'). 
Sep 24 01:10:01 shekkers NetworkManager: <debug info>^I[1190610601.647486] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3110_noserial_if0'). 
Sep 24 01:10:01 shekkers NetworkManager: <debug info>^I[1190610601.655807] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3110_noserial'). 
Sep 24 01:10:01 shekkers NetworkManager: <debug info>^I[1190610601.661340] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3110_noserial_usbraw'). 
Sep 24 21:52:53 shekkers ntpd[23506]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Sep 24 21:52:53 shekkers ntpd[23507]: precision = 1.000 usec
Sep 24 21:52:53 shekkers ntpd[23507]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Sep 24 21:52:53 shekkers ntpd[23507]: Listening on interface wildcard, ::#123 Disabled
Sep 24 21:52:53 shekkers ntpd[23507]: Listening on interface lo, ::1#123 Enabled
Sep 24 21:52:53 shekkers ntpd[23507]: Listening on interface eth0, fe80::20b:6aff:fece:96fd#123 Enabled
Sep 24 21:52:53 shekkers ntpd[23507]: Listening on interface lo, 127.0.0.1#123 Enabled
Sep 24 21:52:53 shekkers ntpd[23507]: Listening on interface eth0, 192.168.1.11#123 Enabled
Sep 24 21:52:53 shekkers ntpd[23507]: kernel time sync status 0040
Sep 24 21:54:09 shekkers ntpd[23507]: ntpd exiting on signal 15
Sep 24 21:54:11 shekkers ntpd[23824]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Sep 24 21:54:11 shekkers ntpd[23825]: precision = 1.000 usec
Sep 24 21:54:11 shekkers ntpd[23825]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Sep 24 21:54:11 shekkers ntpd[23825]: Listening on interface wildcard, ::#123 Disabled
Sep 24 21:54:11 shekkers ntpd[23825]: Listening on interface lo, ::1#123 Enabled
Sep 24 21:54:11 shekkers ntpd[23825]: Listening on interface eth0, fe80::20b:6aff:fece:96fd#123 Enabled
Sep 24 21:54:11 shekkers ntpd[23825]: Listening on interface lo, 127.0.0.1#123 Enabled
Sep 24 21:54:11 shekkers ntpd[23825]: Listening on interface eth0, 192.168.1.11#123 Enabled
Sep 24 21:54:11 shekkers ntpd[23825]: kernel time sync status 0040
Sep 24 21:54:11 shekkers ntpd[23825]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Sep 24 21:56:49 shekkers ntpd[23825]: ntpd exiting on signal 15
Sep 24 22:03:50 shekkers ntpd[24276]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Sep 24 22:03:50 shekkers ntpd[24277]: precision = 1.000 usec
Sep 24 22:03:50 shekkers ntpd[24277]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Sep 24 22:03:50 shekkers ntpd[24277]: Listening on interface wildcard, ::#123 Disabled
Sep 24 22:03:50 shekkers ntpd[24277]: Listening on interface lo, ::1#123 Enabled
Sep 24 22:03:50 shekkers ntpd[24277]: Listening on interface eth0, fe80::20b:6aff:fece:96fd#123 Enabled
Sep 24 22:03:50 shekkers ntpd[24277]: Listening on interface lo, 127.0.0.1#123 Enabled
Sep 24 22:03:50 shekkers ntpd[24277]: Listening on interface eth0, 192.168.1.11#123 Enabled
Sep 24 22:03:50 shekkers ntpd[24277]: kernel time sync status 0040
Sep 24 22:03:50 shekkers ntpd[24277]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Sep 24 22:06:23 shekkers ntpd[24277]: ntpd exiting on signal 15
Sep 25 08:36:15 shekkers NetworkManager: <information>^Istarting... 
Sep 25 08:36:15 shekkers avahi-daemon[5144]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Sep 25 08:36:15 shekkers avahi-daemon[5144]: Successfully dropped root privileges.
Sep 25 08:36:15 shekkers avahi-daemon[5144]: avahi-daemon 0.6.17 starting up.
Sep 25 08:36:15 shekkers avahi-daemon[5144]: Successfully called chroot().
Sep 25 08:36:15 shekkers avahi-daemon[5144]: Successfully dropped remaining capabilities.
Sep 25 08:36:15 shekkers avahi-daemon[5144]: No service found in /etc/avahi/services.
Sep 25 08:36:15 shekkers avahi-daemon[5144]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.11.
Sep 25 08:36:15 shekkers avahi-daemon[5144]: New relevant interface eth0.IPv4 for mDNS.
Sep 25 08:36:15 shekkers avahi-daemon[5144]: Network interface enumeration completed.
Sep 25 08:36:15 shekkers avahi-daemon[5144]: Registering new address record for fe80::20b:6aff:fece:96fd on eth0.*.
Sep 25 08:36:15 shekkers avahi-daemon[5144]: Registering new address record for 192.168.1.11 on eth0.IPv4.
Sep 25 08:36:15 shekkers avahi-daemon[5144]: Registering HINFO record with values 'I686'/'LINUX'.
Sep 25 08:36:16 shekkers avahi-daemon[5144]: Server startup complete. Host name is shekkers.local. Local service cookie is 2664668535.
Sep 25 08:36:21 shekkers nfsd[5401]: nfssvc: writing fds to kernel failed: errno 0 (Success)
Sep 25 08:36:21 shekkers nfsd[5401]: nfssvc: writing fds to kernel failed: errno 0 (Success)
Sep 25 08:36:23 shekkers rpc.statd[5523]: Version 1.0.11 Starting
Sep 25 08:36:24 shekkers hcid[5553]: Bluetooth HCI daemon
Sep 25 08:36:24 shekkers hcid[5553]: Starting SDP server
Sep 25 08:36:24 shekkers NetworkManager: <debug info>^I[1190723784.565179] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Sep 25 08:36:44 shekkers hald: mounted /dev/sda1 on behalf of uid 1000
Sep 25 08:36:47 shekkers NetworkManager: <information>^IUpdating allowed wireless network lists. 
Sep 25 08:36:47 shekkers NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Sep 25 13:34:23 shekkers ntpd[21246]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Sep 25 13:34:23 shekkers ntpd[21247]: precision = 1.000 usec
Sep 25 13:34:23 shekkers ntpd[21247]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Sep 25 13:34:23 shekkers ntpd[21247]: Listening on interface wildcard, ::#123 Disabled
Sep 25 13:34:23 shekkers ntpd[21247]: Listening on interface lo, ::1#123 Enabled
Sep 25 13:34:23 shekkers ntpd[21247]: Listening on interface eth0, fe80::20b:6aff:fece:96fd#123 Enabled
Sep 25 13:34:23 shekkers ntpd[21247]: Listening on interface lo, 127.0.0.1#123 Enabled
Sep 25 13:34:23 shekkers ntpd[21247]: Listening on interface eth0, 192.168.1.11#123 Enabled
Sep 25 13:34:23 shekkers ntpd[21247]: kernel time sync status 0040
Sep 25 13:34:23 shekkers ntpd[21247]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift

This is actually the output when I open it in gedit, because the output from grep couldn't be copied for some reason!  Thanks for any insight you may have.

-Mark

---

### Post by gareththered on 2007-09-25
The ntpd service seems to exit after about 4-5 minutes with signal 15 (TERM). To check if  you can see any servers, at the command prompt type```
ntpq -p
```This will display statistics about the servers (if they connect).  Mine (in the UK) returns```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*maverick.mcc.ac 193.62.22.98     2 u   51   64  377   26.874   32.366  43.182
+ntp0.cis.strath 193.62.22.90     2 u   47   64  377   34.559   32.274  50.053
```Note the name of the server and it's status.  Post your results here.  Also (even though officially you do not know what time it is  :) ) it's quite late over here according to my time servers, so I won't respond until the morning!!  In the meantime a google of 'ntpq' will explain what the results mean.

---

### Post by mjpatey on 2007-09-25
Hmm... here's what I get:

>  10.10.10.10     .INIT.          16 u    - 1024    0    0.000    0.000   0.000


Doesn't look like an actual server...  I'll Google it, too.  Thanks!

-Mark

---

### Post by gareththered on 2007-09-26
I've just typed```
ping ntp.cmr.gov
```and it returned```
PING ntp.cmr.gov (10.10.10.10) 56(84) bytes of data.

--- ntp.cmr.gov ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2022ms
```This IP address is in the 10.x.x.x range and is not routable!  This suggests that the ntp server in ntp.conf is not valid.  You said you edited ntp.conf and placed many   US and Eastern Canada servers in there.  Did you restart ntp```
sudo /etc/init.d/ntp restart
```after these changes?

If you want to test the serviceability of a server before entering it in ntp.conf then use the ntptrace command as follows```
ntptrace ntp.cmr.gov
ntp.cmr.gov: timed out, nothing received
***Request timed out
```vs```
ntptrace maverick.mcc.ac.uk
maverick.mcc.ac.uk: stratum 2, offset -0.001157, synch distance 0.044682
ntp2.ja.net: stratum 1, offset -0.000062, synch distance 0.001671, refid 'MSF'
```The result doesn't need to mean anything to us as long as it's valid!!!

I've just googled your original ntp server, and a Microsoft article lists it as > Arlington, VA: Center for Seismic Studies
140.162.1.3: ntp.cmr.gov
Service Area: NSFNET and SURA regionThat's definately not the IP address either of us got!

Good luck.

---

### Post by mjpatey on 2007-09-26
Wow, thanks for doing all that!  I wish I understood all this stuff as thoroughly as you do.

Before I go any further with details on my end, you should know that now, I'm synced!  I was 4 minutes and creeping further behind yesterday, but after an update-required reboot (which I assume performed the required ntp restart!) I am synchronized to within a second of my cable box and cell phone.

The other details are that I have never touched ntpd.conf (or whatever the name was), but rather added servers using the GUI.

There are two things, then, that I hope are fixed in Gutsy regarding this:

<rant>
1.  The "synchronize now" button just shouldn't be there if it doesn't really mean "sync up with the best available servers".  I think what the button really means is "apply my manual change now", as it's only ever available in the "manual adjust" mode.  In "sync with servers" mode, its greyed out.

2.  When the user makes and applies a change that requires ntp to be restarted, the routine should restart it automatically, or ask the user to log out/in or reboot to apply their changes.  I would think most people (like me) after telling it to sync with my servers, assume it didn't work if the time is still wrong.  Call me crazy!
</rant>

So it seems, from this experience, that all I needed to do was restart ntp to let Ubuntu re-sync with an ntp server.  Does that seem correct to you at this point?

-Mark

---

### Post by gareththered on 2007-09-26
The 'Synchronize Now' button is only available when Configuration is set to Manual.  i.e. you manually sync with the time servers by pressing the button.  If Configuration is set to 'Keep synchronised with Internet servers' then it will periodically sync with the time servers.
Like you, what I do find odd is that when you change the server selection that it doesn't restart the ntpd service to pick up the new configuration and you had to do it manually!

Happy timekeeping!

---

### Post by mjpatey on 2007-09-27
Right.  Everyone I know would be stumped by that.  For folks coming over from Windows (or Mac, for that matter), it's inconceivable that after you tell the computer to do something in a GUI, you then have to post in a forum or search Google to find out how to "apply" the action.  If you're going to make something accessible by a GUI, it should just work, or at least telll you the necessary command to type yourself.

I can't imagine it would be hard to implement, but of course, I'm not a programmer.  I wonder if anyone has tried a recent Gutsy beta?  Maybe it'll be fixed by the final.  :-)

gareththered, thanks for all your help!!!

-Mark

---

