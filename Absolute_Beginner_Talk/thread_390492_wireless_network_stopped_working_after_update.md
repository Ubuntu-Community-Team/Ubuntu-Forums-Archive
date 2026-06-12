---
title: "wireless network stopped working after update"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Slapyo on 2007-03-22
before i ran the updates i had no problem.  as soon as i turned on the computer it picked up my wireless connection and everything was good.  after i updated the wireless would not work unless i do the following.

- double click network monitor (only lo is in connection name, not eth1)
- click configure
- use the drop down for essid (it picks up the wireless networks and signal stengths just fine)
- click ok
- double click network monitor again (only lo is in connection name, not eth1)
- click configure
- get error "The interface does not exist."
- double click network monitor again (now lo and eth1:avahi in connection name)
- removed the ":avahi" part soonly eth1 is left
- click configure
- put correct essid
- click ok
- now i have internet

:/

i didn't make any changes, just ran the updates and now it doesn't work like it did before.  i'd like it to just connect like it did before without having me go through all these hoops to get it to work.

---

### Post by Slapyo on 2007-03-22
anyone know?

---

### Post by mrfuzzemz on 2007-03-22
Are you using Edgy? What kind of wireless card do you have?  Are you using ndiswrapper or Ubuntu's included drivers?

You could try:
```
sudo dpkg-reconfigure network-manger
```

and

```
sudo dpkg-reconfigure network-manager-gnome
```

Try this out and if you don't get anything going reply answering the above questions.

---

### Post by Slapyo on 2007-03-22
I'm using Feisty, not sure exactly on the network card I can find out when I get home.  I have a Dell Insipiron 9300.  As for drivers, it worked out of the box so I assume the included drivers.  Still works, I just have to a little work every time to get it to work.

---

### Post by mrfuzzemz on 2007-03-22
Did you try the commands in my previous post?

Make sure you now have all the latest updates and then go to System>>Administration>>Restricted Drivers Manager.

That may tell you what you've got for a wireless card.

---

### Post by Slapyo on 2007-03-23
have not tried the commands yet.

for restricted drivers i have:

Lucent/Agere linmodem controller driver (enabled, NOT in use)
NVIDIA accelerated graphics driver (enabled, in use)

I am unable to even click In Use for the Lucent/Agere linmodem controller driver, it won't let me.

---

### Post by Slapyo on 2007-03-23
after running the first command, i lost internet.  i ran the second command no problem.  but since i lost internet, i had to go back through my whole process again just to establish a connection.

---

### Post by mrfuzzemz on 2007-03-23
The lucent modem is your modem for Dial-up internet.  It shouldn't say "in use" unless you dial up.

You have to go through that whole process each time?

Type:

```
lspci | grep Ethernet

```

That should tell us what kind of wireless card you have.

---

### Post by Slapyo on 2007-03-23
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

---

### Post by mrfuzzemz on 2007-03-23
You may want to check this out [http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4401-B0](http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4401-B0)


Or try this:

```
sudo modprobe bcm43xx
```

---

### Post by Slapyo on 2007-03-23
here is my syslog if that helps.  i'm away from my laptop right now so i can't do anything with it till later.

```
Mar 23 07:28:45 ubuntu syslogd 1.4.1#20ubuntu4: restart.
Mar 23 07:28:45 ubuntu anacron[5019]: Job `cron.daily' terminated
Mar 23 07:30:01 ubuntu /USR/SBIN/CRON[6162]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Mar 23 07:30:32 ubuntu NetworkManager: <WARNING>^I nm_signal_handler (): Caught signal 15, shutting down normally. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^ICaught terminiation signal 
Mar 23 07:30:32 ubuntu NetworkManager: <debug info>^I[1174660232.787308] nm_print_open_socks (): Open Sockets List: 
Mar 23 07:30:32 ubuntu NetworkManager: <debug info>^I[1174660232.787333] nm_print_open_socks (): Open Sockets List Done. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^IDeactivating device eth1. 
Mar 23 07:30:32 ubuntu avahi-daemon[4542]: Withdrawing address record for 192.168.0.118 on eth1.
Mar 23 07:30:32 ubuntu avahi-daemon[4542]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.118.
Mar 23 07:30:32 ubuntu avahi-daemon[4542]: Interface eth1.IPv4 no longer relevant for mDNS.
Mar 23 07:30:32 ubuntu avahi-daemon[4542]: Withdrawing address record for fe80::213:ceff:fea3:8164 on eth1.
Mar 23 07:30:32 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Istarting... 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Ieth1: Device is fully-supported using driver 'ipw2200'. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^INow managing wireless (802.11) device 'eth1'. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^IDeactivating device eth1. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'b44'. 
Mar 23 07:30:32 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Mar 23 07:30:33 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Mar 23 07:30:33 ubuntu NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Mar 23 07:30:33 ubuntu NetworkManager: <information>^IDeactivating device eth0. 
Mar 23 07:30:33 ubuntu NetworkManager: <information>^IUpdating allowed wireless network lists. 
Mar 23 07:30:33 ubuntu NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Mar 23 07:30:52 ubuntu gconfd (root-6326): starting (version 2.18.0.1), pid 6326 user 'root'
Mar 23 07:30:52 ubuntu gconfd (root-6326): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 23 07:30:52 ubuntu gconfd (root-6326): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 23 07:30:52 ubuntu gconfd (root-6326): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 23 07:30:52 ubuntu gconfd (root-6326): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 23 07:30:52 ubuntu gconfd (root-6326): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 23 07:31:06 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5660
Mar 23 07:31:06 ubuntu dhclient: killed old client process, removed PID file
Mar 23 07:31:06 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 23 07:31:06 ubuntu dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 23 07:31:06 ubuntu dhclient: All rights reserved.
Mar 23 07:31:06 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 23 07:31:06 ubuntu dhclient: 
Mar 23 07:31:06 ubuntu dhclient: Listening on LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:31:06 ubuntu dhclient: Sending on   LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:31:06 ubuntu dhclient: Sending on   Socket/fallback
Mar 23 07:31:06 ubuntu dhclient: DHCPRELEASE on eth1 to 192.168.0.1 port 67
Mar 23 07:31:06 ubuntu dhclient: send_packet: Network is unreachable
Mar 23 07:31:06 ubuntu dhclient: send_packet: please consult README file regarding broadcast address.
Mar 23 07:31:06 ubuntu avahi-autoipd(eth1)[6393]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 108).
Mar 23 07:31:06 ubuntu avahi-autoipd(eth1)[6393]: Successfully called chroot().
Mar 23 07:31:06 ubuntu avahi-autoipd(eth1)[6393]: Successfully dropped root privileges.
Mar 23 07:31:06 ubuntu avahi-autoipd(eth1)[6393]: fopen() failed: Permission denied
Mar 23 07:31:06 ubuntu avahi-autoipd(eth1)[6393]: Starting with address 169.254.7.145
Mar 23 07:31:11 ubuntu avahi-autoipd(eth1)[6393]: Callout BIND, address 169.254.7.145 on interface eth1
Mar 23 07:31:11 ubuntu avahi-daemon[4542]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.7.145.
Mar 23 07:31:11 ubuntu avahi-daemon[4542]: New relevant interface eth1.IPv4 for mDNS.
Mar 23 07:31:11 ubuntu avahi-daemon[4542]: Registering new address record for 169.254.7.145 on eth1.IPv4.
Mar 23 07:31:15 ubuntu avahi-autoipd(eth1)[6393]: Successfully claimed IP address 169.254.7.145
Mar 23 07:31:15 ubuntu avahi-autoipd(eth1)[6393]: fopen() failed: Permission denied
Mar 23 07:31:15 ubuntu avahi-daemon[4542]: Interface eth1.IPv4 no longer relevant for mDNS.
Mar 23 07:31:15 ubuntu avahi-daemon[4542]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.7.145.
Mar 23 07:31:15 ubuntu avahi-autoipd(eth1)[6393]: SIOCSIFFLAGS failed: Permission denied
Mar 23 07:31:15 ubuntu avahi-autoipd(eth1)[6393]: Callout STOP, address 169.254.7.145 on interface eth1
Mar 23 07:31:15 ubuntu avahi-daemon[4542]: Withdrawing address record for 169.254.7.145 on eth1.
Mar 23 07:31:15 ubuntu avahi-autoipd(eth1)[6394]: client: RTNETLINK answers: No such process
Mar 23 07:31:15 ubuntu kernel: [  583.120000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 23 07:31:15 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Mar 23 07:31:15 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 23 07:31:15 ubuntu dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 23 07:31:15 ubuntu dhclient: All rights reserved.
Mar 23 07:31:15 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 23 07:31:15 ubuntu dhclient: 
Mar 23 07:31:16 ubuntu dhclient: Listening on LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:31:16 ubuntu dhclient: Sending on   LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:31:16 ubuntu dhclient: Sending on   Socket/fallback
Mar 23 07:31:17 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar 23 07:31:24 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Mar 23 07:31:33 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Mar 23 07:31:48 ubuntu dhclient: No DHCPOFFERS received.
Mar 23 07:31:48 ubuntu dhclient: No working leases in persistent database - sleeping.
Mar 23 07:31:48 ubuntu avahi-autoipd(eth1)[6465]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 108).
Mar 23 07:31:48 ubuntu avahi-autoipd(eth1)[6465]: Successfully called chroot().
Mar 23 07:31:48 ubuntu avahi-autoipd(eth1)[6465]: Successfully dropped root privileges.
Mar 23 07:31:48 ubuntu avahi-autoipd(eth1)[6465]: fopen() failed: Permission denied
Mar 23 07:31:48 ubuntu avahi-autoipd(eth1)[6465]: Starting with address 169.254.7.145
Mar 23 07:31:53 ubuntu avahi-autoipd(eth1)[6465]: Callout BIND, address 169.254.7.145 on interface eth1
Mar 23 07:31:53 ubuntu avahi-daemon[4542]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.7.145.
Mar 23 07:31:53 ubuntu avahi-daemon[4542]: New relevant interface eth1.IPv4 for mDNS.
Mar 23 07:31:53 ubuntu avahi-daemon[4542]: Registering new address record for 169.254.7.145 on eth1.IPv4.
Mar 23 07:31:57 ubuntu avahi-autoipd(eth1)[6465]: Successfully claimed IP address 169.254.7.145
Mar 23 07:31:57 ubuntu avahi-autoipd(eth1)[6465]: fopen() failed: Permission denied
Mar 23 07:32:11 ubuntu anacron[5019]: Job `cron.weekly' started
Mar 23 07:32:11 ubuntu anacron[6518]: Updated timestamp for job `cron.weekly' to 2007-03-23
Mar 23 07:32:13 ubuntu syslogd 1.4.1#20ubuntu4: restart.
Mar 23 07:32:13 ubuntu anacron[5019]: Job `cron.weekly' terminated
Mar 23 07:32:13 ubuntu anacron[5019]: Normal exit (2 jobs run)
Mar 23 07:32:15 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6474
Mar 23 07:32:15 ubuntu dhclient: killed old client process, removed PID file
Mar 23 07:32:15 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 23 07:32:15 ubuntu dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 23 07:32:15 ubuntu dhclient: All rights reserved.
Mar 23 07:32:15 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 23 07:32:15 ubuntu dhclient: 
Mar 23 07:32:15 ubuntu dhclient: Listening on LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:32:15 ubuntu dhclient: Sending on   LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:32:15 ubuntu dhclient: Sending on   Socket/fallback
Mar 23 07:32:15 ubuntu dhclient: DHCPRELEASE on eth1 to 192.168.0.1 port 67
Mar 23 07:32:16 ubuntu avahi-daemon[4542]: Interface eth1.IPv4 no longer relevant for mDNS.
Mar 23 07:32:16 ubuntu avahi-daemon[4542]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.7.145.
Mar 23 07:32:16 ubuntu avahi-autoipd(eth1)[6465]: SIOCSIFFLAGS failed: Permission denied
Mar 23 07:32:16 ubuntu avahi-autoipd(eth1)[6465]: Callout STOP, address 169.254.7.145 on interface eth1
Mar 23 07:32:16 ubuntu avahi-daemon[4542]: Withdrawing address record for 169.254.7.145 on eth1.
Mar 23 07:32:16 ubuntu avahi-autoipd(eth1)[6466]: client: RTNETLINK answers: No such process
Mar 23 07:32:16 ubuntu kernel: [  643.468000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 23 07:32:16 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Mar 23 07:32:16 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 23 07:32:16 ubuntu dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 23 07:32:16 ubuntu dhclient: All rights reserved.
Mar 23 07:32:16 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 23 07:32:16 ubuntu dhclient: 
Mar 23 07:32:17 ubuntu dhclient: Listening on LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:32:17 ubuntu dhclient: Sending on   LPF/eth1/00:13:ce:a3:81:64
Mar 23 07:32:17 ubuntu dhclient: Sending on   Socket/fallback
Mar 23 07:32:17 ubuntu ntpdate[6500]: can't find host ntp.ubuntu.com 
Mar 23 07:32:17 ubuntu ntpdate[6500]: no servers can be used, exiting
Mar 23 07:32:17 ubuntu kernel: [  645.248000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Mar 23 07:32:18 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Mar 23 07:32:18 ubuntu dhclient: DHCPOFFER from 192.168.0.1
Mar 23 07:32:18 ubuntu dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Mar 23 07:32:18 ubuntu dhclient: DHCPACK from 192.168.0.1
Mar 23 07:32:18 ubuntu avahi-daemon[4542]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.118.
Mar 23 07:32:18 ubuntu avahi-daemon[4542]: New relevant interface eth1.IPv4 for mDNS.
Mar 23 07:32:18 ubuntu avahi-daemon[4542]: Registering new address record for 192.168.0.118 on eth1.IPv4.
Mar 23 07:32:18 ubuntu dhclient: bound to 192.168.0.118 -- renewal in 34690 seconds.
Mar 23 07:32:19 ubuntu ntpdate[6778]: adjust time server 82.211.81.145 offset -0.027663 sec
Mar 23 07:32:19 ubuntu avahi-daemon[4542]: Registering new address record for fe80::213:ceff:fea3:8164 on eth1.*.
Mar 23 07:32:22 ubuntu gconfd (root-6326): GConf server is not in use, shutting down.
Mar 23 07:32:22 ubuntu gconfd (root-6326): Exiting
Mar 23 07:32:28 ubuntu kernel: [  656.100000] eth1: no IPv6 routers present
Mar 23 07:34:01 ubuntu gconfd (root-6834): starting (version 2.18.0.1), pid 6834 user 'root'
Mar 23 07:34:01 ubuntu gconfd (root-6834): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 23 07:34:01 ubuntu gconfd (root-6834): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 23 07:34:01 ubuntu gconfd (root-6834): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 23 07:34:01 ubuntu gconfd (root-6834): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 23 07:34:01 ubuntu gconfd (root-6834): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 23 07:37:01 ubuntu gconfd (root-6834): GConf server is not in use, shutting down.
Mar 23 07:37:01 ubuntu gconfd (root-6834): Exiting
Mar 23 07:39:01 ubuntu /USR/SBIN/CRON[7026]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
```

---

### Post by mrfuzzemz on 2007-03-23
That looks to say that you have an Intel card rather than a broadcom card as it is trying to load the intel driver.

So try this out when you can:

```
sudo modprobe ipw2200 
```

---

### Post by Slapyo on 2007-03-23
yeah, if i look at my devices i see this: Intel Corporation PRO/Wireless 2915ABG Network

---

### Post by mrfuzzemz on 2007-03-23
Yep.  Okay.  Try the command above.  If all else fails we can manually reinstall the driver for it.

---

### Post by Slapyo on 2007-03-23
i'll have to wait till i can get back home later on today and try it.

---

### Post by Slapyo on 2007-03-23
Just curious.  If the driver was the problem, wouldn't that mean it wouldn't work at all?  It does work, with a bunch of steps.

---

### Post by mrfuzzemz on 2007-03-23
That's what I don't fully understand and why I suggested possibly reinstalling the driver.

---

### Post by Slapyo on 2007-03-23
i ran the command and nothing happened in the terminal.  just gave me another prompt right below it.  gonna reboot now.

---

### Post by mrfuzzemz on 2007-03-23
> **Slapyo said:**
> i ran the command and nothing happened in the terminal.  just gave me another prompt right below it.  gonna reboot now.

Unless something goes wrong, that is exactly what should happen.  Let me know what happens when you reboot.

---

### Post by Slapyo on 2007-03-23
nothin, same issue.  have to go through the same process to actually connect.

what i don't get is it's not connected, but if i click the drop down for essid i see all of the available wireless networks and they signal strength changes.  obviously it's seeing these.

---

### Post by mrfuzzemz on 2007-03-23
Have you got any kind of switch or anything for the wireless card?

Try connecting through the command line and post your results every step of the way:

To check status of wireless card:

```
iwconfig
```

To scan networks:

```
iwlist eth1 scan
``` where eth1 is the wireless adapter as listed from iwconfig

To connect (assuming no security):
```
sudo iwconfig eth1 essid 'Name of the access point'
```  again, eth1 is as above

now to get an IP:

```
sudo dhclient eth1
``` again, eth1 as above.



Let me know how that works and what it says.

---

### Post by mrfuzzemz on 2007-03-23
You may also want to try reinstalling network-manager.

In synaptic find 'network-manager-gnome,' right click, and then click reinstall.  If that doesn't work try completely installing it and then installing it again.

---

### Post by deathbyswiftwind on 2007-03-23
Uninstall network-manager and give that a go. For some reason netowkr-manager killed alot of peoples network connections. I could see all essids but couldnt connect to any. you could make a script to run at startup that restarts the network and use it thatway. Or you could just uninstall network-manager and be done with it. Your choice.

---

### Post by Slapyo on 2007-03-23
hm, i liked network-manager because it made it easy for me to change wireless networks when traveling and connecting at hotels.  plus it showed the signal strength.  :(  will give this stuff a shot later on tonight and see what happens.

sucks because everything worked perfect before.

---

### Post by deathbyswiftwind on 2007-03-23
Try running this 

```

sudo /etc/init.d/networking restart

```

It worked for me but its rather annoying having to do it everytime I restarted. I could have made a script to do it but Im lazy :)

---

### Post by Slapyo on 2007-03-23
i tried reinstalling network-manager and network-manager-gnome ... didn't do anything.

---

### Post by Slapyo on 2007-03-23
> **deathbyswiftwind said:**
> Try running this 

```

sudo /etc/init.d/networking restart

```

It worked for me but its rather annoying having to do it everytime I restarted. I could have made a script to do it but Im lazy :)
using that worked for me, soon as i ran it i was online.  how would i write a script to do this on start up for me?

here was the output:
```
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 4462
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:a3:81:64
Sending on   LPF/eth1/00:13:ce:a3:81:64
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:a3:81:64
Sending on   LPF/eth1/00:13:ce:a3:81:64
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.118 -- renewal in 33879 seconds.
                                                                         [ OK ]
```

---

### Post by mrfuzzemz on 2007-03-24
There is a slew of new updates for feisty including kernel, and restricted driver packages.  Maybe things will go smoother after the update?

Let me know.

---

### Post by Slapyo on 2007-03-24
ran the updates, no change.

i saw that feisty was released as beta.  obviously i would get those changes as they come through right, using the update manager?

---

### Post by mrfuzzemz on 2007-03-24
That is correct.  Normal updates bring you to Beta and beyond.  I don't know what may have caused this change in your system.  I suppose you could see if booting the beta livecd gives you the functionality you want and if so possibly reinstalling Ubuntu.

---

### Post by Slapyo on 2007-03-25
hrm, well i suppose if i can make a start up script outta that line above i will be ok.  i'll just keep waiting it out and hoping it gets fixed in a release.

---

### Post by Slapyo on 2007-03-25
btw, thanks to every one that has helped me out so far.  i appreciate it.

---

### Post by Slapyo on 2007-03-26
kernel update to 2.6.20-13-386 ... had an nvidia driver update as well.  no problems there.  but network problem still exists.

---

