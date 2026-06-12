---
title: "Standby/Hibernate doesn't work in Feisty on Dell X1"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by w1zard on 2007-04-19
I've got Feisty installed on a Dell Latitude X1. All great so far, but the laptop hangs when going into standby. The screen blackens but it never goes into standby, and I can't get back to the desktop once this happens. I can only get out of it by powering off and rebooting.

Help!

---

### Post by Seisen on 2007-04-19
I have the same problem with my desktop and I built it myself.

---

### Post by w1zard on 2007-04-19
Is it something that can be fixed, or is it a bug?

---

### Post by x64Jimbo on 2007-04-19
Sleep and Hibernate are not the same thing. Is it just sleep, or both that give you problems?

---

### Post by w1zard on 2007-04-19
Hi
    Both are giving me problems - the symptoms are the same for both, neither seem to be able to cleanly shut down all the services as it never gets to the suspend/standby/sleep mode.

---

### Post by x64Jimbo on 2007-04-19
Sounds like it's an ACPI problem, but my experience fixing these kinds of problems is limited. 
Have a look around on google for X1 ACPI support if this thread runs out of steam for you.

---

### Post by faust99 on 2007-04-20
I've got the same problem on my Dell Inspiron 710m laptop as well; both with suspend and hibernate...

---

### Post by odelay on 2007-04-21
Same problem with a Dell e1505.  Worked fine in Edgy. :/

---

### Post by rich.bradshaw on 2007-04-24
Me too on a Dell inspiron 8100.

---

### Post by saultpastor on 2007-04-24
I think it is a kernel problem,

My HP dv2000 went to sleep and restored fine in Edgy, but I had to go to the Fiesty kernel to fix a conflict between Nvidia and Ndiswrapper.

After the upgrade it broke suspend and resume (I never checked hibernate before the upgrade)

---

### Post by Xander06 on 2007-04-25
Same problem here, it's working on edgy but not on feisty with a Dell Inspiron 630m :(

The log is not really helping, Wifi is activated :
```

Apr 24 03:55:26 ganymede gnome-power-manager: (alex) Hibernation de l'ordinateur car La méthode DBUS Hibernate() a été appelée
Apr 24 03:55:27 ganymede NetworkManager: <information>^IGoing to sleep.
Apr 24 03:55:28 ganymede dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5568
Apr 24 03:55:28 ganymede dhclient: killed old client process, removed PID file
Apr 24 03:55:28 ganymede dhclient: receive_packet failed on eth0: Network is down
Apr 24 03:55:28 ganymede avahi-daemon[4853]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 24 03:55:28 ganymede avahi-daemon[4853]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.4.
Apr 24 03:55:28 ganymede avahi-autoipd(eth0)[5342]: SIOCSIFFLAGS failed: Permission denied
Apr 24 03:55:28 ganymede avahi-autoipd(eth0)[5342]: Callout STOP, address 169.254.6.11 on interface eth0
Apr 24 03:55:28 ganymede avahi-daemon[4853]: Withdrawing address record for fe80::213:ceff:feee:7c40 on eth1.
Apr 24 03:55:28 ganymede avahi-daemon[4853]: Withdrawing address record for 192.168.0.4 on eth1.
Apr 24 03:55:28 ganymede avahi-daemon[4853]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 24 03:55:28 ganymede avahi-daemon[4853]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.6.11.
Apr 24 03:55:28 ganymede avahi-daemon[4853]: Withdrawing address record for 169.254.6.11 on eth0.
Apr 24 03:55:28 ganymede dhclient: DHCPRELEASE on eth1 to 192.168.0.254 port 67
Apr 24 03:55:28 ganymede dhclient: send_packet: Network is unreachable
Apr 24 03:55:28 ganymede dhclient: send_packet: please consult README file regarding broadcast address.
Apr 24 03:55:28 ganymede avahi-autoipd(eth0)[5343]: client: RTNETLINK answers: No such process
Apr 24 03:55:28 ganymede avahi-autoipd(eth1)[1266]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Apr 24 03:55:28 ganymede avahi-autoipd(eth1)[1266]: Successfully called chroot().
Apr 24 03:55:28 ganymede avahi-autoipd(eth1)[1266]: Successfully dropped root privileges.
Apr 24 03:55:28 ganymede kernel: [53598.144000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 24 03:55:28 ganymede avahi-autoipd(eth1)[1266]: fopen() failed: Permission denied
Apr 24 03:55:28 ganymede avahi-autoipd(eth1)[1266]: Starting with address 169.254.7.170
Apr 24 03:55:28 ganymede dhcdbd:  dhclient 5568 down (9) but si_code == 0 and releasing==0 !
Apr 24 03:55:28 ganymede dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Apr 24 03:55:28 ganymede dhclient: Internet Systems Consortium DHCP Client V3.0.4
Apr 24 03:55:28 ganymede dhclient: Copyright 2004-2006 Internet Systems Consortium.
Apr 24 03:55:28 ganymede dhclient: All rights reserved.
Apr 24 03:55:28 ganymede dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 24 03:55:28 ganymede dhclient:
Apr 24 03:55:28 ganymede dhclient: Listening on LPF/eth1/00:13:ce:ee:7c:40
Apr 24 03:55:28 ganymede dhclient: Sending on   LPF/eth1/00:13:ce:ee:7c:40
Apr 24 03:55:28 ganymede dhclient: Sending on   Socket/fallback
Apr 24 03:55:28 ganymede dhclient: DHCPRELEASE on eth1 to 192.168.0.254 port 67
Apr 24 03:55:28 ganymede dhclient: send_packet: Network is unreachable
Apr 24 03:55:28 ganymede dhclient: send_packet: please consult README file regarding broadcast address.
Apr 24 03:55:28 ganymede avahi-autoipd(eth1)[1266]: SIOCSIFFLAGS failed: Permission denied
Apr 24 03:55:29 ganymede NetworkManager: <debug info>^I[1177379729.747101] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_14_22_92_6e_74').
Apr 24 03:55:29 ganymede NetworkManager: <information>^IDeactivating device eth1.
Apr 24 03:55:30 ganymede NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_mode (): error getting card mode on eth1: No such device
Apr 24 03:55:30 ganymede kernel: [53599.756000] ACPI: PCI interrupt for device 0000:02:03.0 disabled
Apr 24 03:56:49 ganymede syslogd 1.4.1#20ubuntu4: restart.

```

Restart is done after switching off and on the laptop

---

### Post by shouravv on 2007-04-25
Using Dell Inspiron 1150. Standby works fine for me, but when I try to hibernate, the machine almost goes into hibernation (closes services) and immediately wakes up from hibernation.

---

### Post by richardh on 2007-04-27
Same problem with Dell Lattitude D810

Initiate Hibernate. Script appears to work, then computer immediately wakes again. No alternative but to shutdown.

Hibernate worked with Edgy and with first Beta release of Feisty, but stopped working mid April. Not quite sure after which update.

Tried changing /etc/default/acpi-support [line POST_VIDEO=true to read POST_VIDEO=]

Also set line in /etc/default/acpi-support [ENABLE_LAPTOP_MODE=true]

No result.

After returning from Hibernation, I get the error:
Hibernate Problem
HAL failed to hibernate ....

Richard

---

### Post by x64Jimbo on 2007-04-27
I suggest you guys have a look in the bugtracker to see if someone has already filed a bug for this - it seems like you might have a legit one on your hands.

---

### Post by mikej_96 on 2007-04-27
I have the same problem with my Dell Inspiron 6400. Suspend never worked for me in edgy either, but hibernate did. I was happy to see that suspend worked when i upgraded to fiesty, however, at that time I had not been able to use the desktop effects with my Nvidia graphics card. I ended up doing a fresh install, to find that now the desktop effects worked, but suspend didn't.

---

### Post by jovial on 2007-05-02
Hi

Same problem to standbye or hibernate with motherboard Asrock K8NF6G-VSTA  Nvidia6100 fiesty kernel 2.6.20-15-generic

Bug fixed for this MB on  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/81137](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/81137)

bye

---

### Post by w1zard on 2007-05-02
I have an open bug for this if anyone else is having the same problem:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107986](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107986)

---

### Post by Marcos.Rufino on 2007-05-05
Standby has never worked for me under Ubuntu. I've already tried it in 5 different machines!! It's really ludicrous something so basic as this would not work out of the box. I even tried to compile a new kernel, following some threads, but it didn't help.

---

### Post by H.E. Pennypacker on 2007-05-06
When I try to hibernate or suspend, the screen turns on my screensaver, and if I move the mouse, the password dialog shows up.  As I said, it goes to the screensaver, but never actually suspends or hibernates.

Even worse, after this, wireless is gone.

---

