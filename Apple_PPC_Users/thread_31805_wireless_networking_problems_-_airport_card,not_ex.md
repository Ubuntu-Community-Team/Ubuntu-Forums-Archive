---
title: "wireless networking problems - airport card,not extreme"
date: 2005-05-04
forum: Apple PPC Users
---

### Post by MIZREE on 2005-05-04
I posted this into wrong thread earlier, so hopefully this is better.
first let me say that i couldnt care less whether osx or nix is better on powerpc arch. this is a learning tool for me, since it is a spare computer. I chose umbutu distribution because i heard it was easy to learn and upgrade packages etc.

I have installed umbutu 5.04-ppc on a 12inch dual usb g3 ibook 800, with 650mb ram.
the install went great, and seems to work ok so far except for wireless connectivity.
I have the old airport internal b card, and it looks configured correctly to me, but i get 0% signal. I have tried to connect with two different routers at my house and one at a friends house. I have netgear 634 -wep secured, and old airport graphite -open system. niether shows signal on my ibook wireless. I have setup using dhcp and static ip, with no signal shows up. ibook also hangs on resume from standby with an airport error:
eth1 unknown information frame received (type f202)
I then must reboot to get it to come back up.

did a search for this error and saw other nix users had same error on similar hardware, and they thought it was a recent firmware upgrade to their router was the problem. I have not done upgrades to router since first installed it. and had no problems connecting wirelessly when using osx.

still seems it should be able to connect to the airport router with no issues, but it doesnt see it either. My winblows machines can connect to both routers with no problems at all.
could this be related to the ipv6 is installed? aside from the wep info, all my settings are same when wired and I can connect fine then. wireless says connected but idle... and 0% signal strength while sitting next to my superg router and my b only router..

any help resolving this would be much appreciated.

I also want to addon packages and codecs etc, to make this dist a bit more useful for me, but when tried an addon cd from umbutuguide.org, realized it and its instructions were for x86 only. oops. I couldn't find much info for extending ppc version with more packages and stuff.

---

### Post by MIZREE on 2005-05-04
also I am unable to ping my router from terminal when using wireless ethernet.
everything seems to work when using hardwire.

---

### Post by slux on 2005-05-05
Firts of all, I'd switch the encryption off from the AP since it might be complicating things.

Do you see anything related in the logs, the directory /var/log contains the system log files readable as text. You need root access or relevant group membership and you can read them with whatever you want. Files such as dmesg, syslog, kernel.log, debug.log are worth checking out (not all of them might be there, I don't have a debian/ubuntu currently here and don't remember which ones it does by default). Search for "airport" and post the related lines beginning with "ethX" (where X is some number).

---

### Post by MIZREE on 2005-05-05
Hello slux, thanks for your time and attention. I would like to get this working, and expected some hassles when switching from an outta the box osx to nix.

I'm not sure which log i should be looking at, but here is the entire system log. it does show the error I spoke of when resuming from sleep, and maybe other needed info. I'm too new to nix to know what i'm looking for here though. My suspicion is that it has something to do with ipv6, but dunno enough. eth1 is my airport, and it gets errors. I have tried to remove security from the netgear wgt634 with no difference. also it will not get signal from graphite airport either -which has no security. also I noticed in the device manager that most devices are listed as unknown, only hard drive and video card show correct information. I was incorrect earlier in quoting my specs, this 12 inch dualusb ibook2 is 600mhz with 632mb ram and 850mb swap.

---

### Post by MIZREE on 2005-05-05
/var/log/syslog: part1

May  5 00:43:02 pirate syslogd 1.4.1#16ubuntu6: restart.
May  5 00:43:03 pirate anacron[11765]: Job `cron.daily' terminated (mailing output)
May  5 00:43:06 pirate postfix/cleanup[15978]: 044869851C: message-id=<20050505044304.044869851C@pirate>
May  5 00:43:07 pirate postfix/local[15982]: 044869851C: to=<alix@pirate>, orig_to=<root>, relay=local, delay=2, status=sent (delivered to mailbox)
May  5 00:43:56 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 00:44:07 pirate gconfd (root-16538): starting (version 2.10.0), pid 16538 user 'root'
May  5 00:44:07 pirate gconfd (root-16538): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  5 00:44:07 pirate gconfd (root-16538): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May  5 00:44:07 pirate gconfd (root-16538): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  5 00:44:13 pirate gconfd (root-16538): Exiting
May  5 00:44:19 pirate gconfd (root-16594): starting (version 2.10.0), pid 16594 user 'root'
May  5 00:44:19 pirate gconfd (root-16594): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  5 00:44:19 pirate gconfd (root-16594): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May  5 00:44:19 pirate gconfd (root-16594): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  5 00:44:31 pirate gconfd (root-16594): Exiting
May  5 00:44:35 pirate kernel: NET: Registered protocol family 10
May  5 00:44:35 pirate kernel: Disabled Privacy Extensions on device c025bf5c(lo)
May  5 00:44:35 pirate kernel: IPv6 over IPv4 tunneling driver
May  5 00:44:35 pirate kernel: divert: not allocating divert_blk for non-ethernet device sit0
May  5 00:44:39 pirate gconfd (root-16689): starting (version 2.10.0), pid 16689 user 'root'
May  5 00:44:39 pirate gconfd (root-16689): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  5 00:44:39 pirate gconfd (root-16689): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May  5 00:44:39 pirate gconfd (root-16689): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  5 00:44:43 pirate gconfd (root-16689): Exiting
May  5 00:44:46 pirate kernel: eth1: no IPv6 routers present
May  5 00:44:48 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 00:45:29 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 00:46:32 pirate anacron[11765]: Job `cron.weekly' started
May  5 00:46:32 pirate anacron[17509]: Updated timestamp for job `cron.weekly' to 2005-05-05
May  5 00:47:19 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 00:47:29 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 00:48:33 pirate gconfd (root-19007): starting (version 2.10.0), pid 19007 user 'root'
May  5 00:48:33 pirate gconfd (root-19007): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  5 00:48:33 pirate gconfd (root-19007): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May  5 00:48:33 pirate gconfd (root-19007): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  5 00:49:20 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 00:50:01 pirate last message repeated 3 times
May  5 00:51:14 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 00:52:16 pirate last message repeated 5 times
May  5 00:52:29 pirate exiting on signal 15
May  5 00:52:31 pirate syslogd 1.4.1#16ubuntu6: restart.
May  5 00:52:31 pirate anacron[11765]: Job `cron.weekly' terminated
May  5 00:52:31 pirate anacron[11765]: Job `cron.monthly' started
May  5 00:52:31 pirate anacron[23365]: Updated timestamp for job `cron.monthly' to 2005-05-05
May  5 00:54:07 pirate postfix/cleanup[24263]: 5BE7797FBE: message-id=<20050505045407.5BE7797FBE@pirate>
May  5 00:54:07 pirate postfix/local[24266]: 5BE7797FBE: to=<alix@pirate>, orig_to=<root>, relay=local, delay=0, status=sent (delivered to mailbox)
May  5 00:54:09 pirate udev[24309]: creating device node '/dev/vcs4'
May  5 00:54:09 pirate udev[24311]: creating device node '/dev/vcsa4'
May  5 00:54:09 pirate udev[24313]: creating device node '/dev/vcs5'
May  5 00:54:09 pirate udev[24315]: creating device node '/dev/vcsa5'
May  5 00:54:09 pirate udev[24321]: creating device node '/dev/vcs7'
May  5 00:54:09 pirate udev[24323]: creating device node '/dev/vcsa7'
May  5 00:54:09 pirate udev[24361]: removing device node '/dev/vcsa6'
May  5 00:54:09 pirate udev[24380]: removing device node '/dev/vcs6'
May  5 00:54:09 pirate udev[24391]: removing device node '/dev/vcsa5'
May  5 00:54:09 pirate udev[24405]: removing device node '/dev/vcs5'
May  5 00:54:09 pirate udev[24414]: removing device node '/dev/vcs4'
May  5 00:54:09 pirate udev[24425]: removing device node '/dev/vcs7'
May  5 00:54:09 pirate udev[24427]: removing device node '/dev/vcsa7'
May  5 00:54:10 pirate udev[24444]: removing device node '/dev/vcsa4'
May  5 00:54:10 pirate udev[24453]: creating device node '/dev/vcs7'
May  5 00:54:10 pirate udev[24455]: creating device node '/dev/vcsa7'
May  5 00:54:13 pirate init: Re-reading inittab
May  5 00:54:13 pirate udev[24502]: creating device node '/dev/vcs5'
May  5 00:54:13 pirate udev[24505]: creating device node '/dev/vcs6'
May  5 00:54:13 pirate udev[24507]: creating device node '/dev/vcs4'
May  5 00:54:13 pirate udev[24509]: creating device node '/dev/vcsa5'
May  5 00:54:13 pirate udev[24511]: creating device node '/dev/vcsa4'
May  5 00:54:13 pirate udev[24513]: creating device node '/dev/vcsa6'
May  5 00:54:33 pirate gconfd (root-19007): SIGHUP received, reloading all databases
May  5 00:54:33 pirate gconfd (root-19007): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  5 00:54:33 pirate gconfd (root-19007): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May  5 00:54:33 pirate gconfd (root-19007): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  5 00:58:13 pirate gconfd (alix-25839): starting (version 2.10.0), pid 25839 user 'alix'
May  5 00:58:13 pirate gconfd (alix-25839): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  5 00:58:13 pirate gconfd (alix-25839): Resolved address "xml:readwrite:/home/alix/.gconf" to a writable configuration source at position 1
May  5 00:58:13 pirate gconfd (alix-25839): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  5 00:58:27 pirate gconfd (alix-25839): Resolved address "xml:readwrite:/home/alix/.gconf" to a writable configuration source at position 0
May  5 00:59:44 pirate anacron[11765]: Job `cron.monthly' terminated
May  5 00:59:44 pirate anacron[11765]: Normal exit (3 jobs run)
May  5 01:12:31 pirate -- MARK --
May  5 01:17:02 pirate /USR/SBIN/CRON[26588]: (root) CMD (   run-parts --report /etc/cron.hourly)
May  5 01:17:43 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 01:18:14 pirate last message repeated 2 times
May  5 01:19:16 pirate last message repeated 5 times
May  5 01:20:19 pirate last message repeated 6 times
May  5 01:21:21 pirate last message repeated 6 times
May  5 01:22:14 pirate last message repeated 4 times
May  5 01:23:16 pirate last message repeated 4 times
May  5 01:24:29 pirate last message repeated 6 times
May  5 01:25:31 pirate last message repeated 6 times
May  5 01:26:24 pirate last message repeated 5 times
May  5 01:27:26 pirate last message repeated 6 times
May  5 01:28:28 pirate last message repeated 4 times
May  5 01:29:31 pirate last message repeated 5 times
May  5 01:30:23 pirate last message repeated 5 times
May  5 01:31:26 pirate last message repeated 6 times
May  5 01:32:28 pirate last message repeated 5 times
May  5 01:33:20 pirate last message repeated 4 times
May  5 01:34:22 pirate last message repeated 4 times
May  5 01:35:25 pirate last message repeated 6 times
May  5 01:36:28 pirate last message repeated 6 times
May  5 01:37:30 pirate last message repeated 6 times
May  5 01:38:22 pirate last message repeated 4 times
May  5 01:39:25 pirate last message repeated 5 times
May  5 01:40:28 pirate last message repeated 6 times
May  5 01:41:30 pirate last message repeated 6 times
May  5 01:42:23 pirate last message repeated 5 times
May  5 01:43:25 pirate last message repeated 4 times
May  5 01:44:27 pirate last message repeated 5 times
May  5 01:45:19 pirate last message repeated 4 times
May  5 01:45:51 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 01:50:13 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 01:50:55 pirate last message repeated 3 times
May  5 02:01:47 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 02:02:39 pirate last message repeated 2 times
May  5 02:03:31 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 02:08:17 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 02:09:20 pirate last message repeated 6 times
May  5 02:10:23 pirate last message repeated 6 times
May  5 02:11:25 pirate last message repeated 5 times
May  5 02:12:28 pirate last message repeated 4 times
May  5 02:13:30 pirate last message repeated 6 times
May  5 02:14:22 pirate last message repeated 5 times
May  5 02:15:25 pirate last message repeated 6 times
May  5 02:16:28 pirate last message repeated 5 times
May  5 02:16:48 pirate last message repeated 2 times
May  5 02:17:01 pirate /USR/SBIN/CRON[27312]: (root) CMD (   run-parts --report /etc/cron.hourly)
May  5 02:17:09 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 02:17:40 pirate last message repeated 2 times
May  5 02:18:43 pirate last message repeated 6 times
May  5 02:19:46 pirate last message repeated 6 times
May  5 02:20:48 pirate last message repeated 6 times
May  5 02:21:51 pirate last message repeated 6 times
May  5 02:22:53 pirate last message repeated 5 times
May  5 02:23:56 pirate last message repeated 6 times
May  5 02:24:59 pirate last message repeated 6 times
May  5 02:26:01 pirate last message repeated 6 times
May  5 02:26:53 pirate last message repeated 3 times
May  5 02:27:55 pirate last message repeated 4 times
May  5 02:28:58 pirate last message repeated 6 times
May  5 02:30:01 pirate last message repeated 6 times
May  5 02:30:53 pirate last message repeated 5 times
May  5 02:31:55 pirate last message repeated 5 times
May  5 02:32:58 pirate last message repeated 5 times
May  5 02:34:00 pirate last message repeated 5 times
May  5 02:34:52 pirate last message repeated 5 times
May  5 02:35:55 pirate last message repeated 6 times
May  5 02:36:58 pirate last message repeated 6 times
May  5 02:37:50 pirate last message repeated 4 times
May  5 02:38:52 pirate last message repeated 5 times
May  5 02:39:55 pirate last message repeated 6 times
May  5 02:40:58 pirate last message repeated 6 times
May  5 02:42:00 pirate last message repeated 6 times
May  5 02:42:52 pirate last message repeated 3 times
May  5 02:43:54 pirate last message repeated 5 times
May  5 02:44:57 pirate last message repeated 6 times
May  5 02:46:00 pirate last message repeated 6 times
May  5 02:46:52 pirate last message repeated 5 times
May  5 02:47:54 pirate last message repeated 4 times
May  5 02:48:57 pirate last message repeated 5 times
May  5 02:49:59 pirate last message repeated 6 times
May  5 02:50:52 pirate last message repeated 5 times
May  5 02:51:44 pirate last message repeated 5 times
May  5 02:52:57 pirate last message repeated 5 times
May  5 02:53:48 pirate last message repeated 3 times
May  5 02:55:01 pirate last message repeated 3 times
May  5 02:55:53 pirate last message repeated 5 times
May  5 02:56:56 pirate last message repeated 6 times
May  5 02:57:48 pirate last message repeated 5 times
May  5 02:59:00 pirate last message repeated 4 times
May  5 02:59:52 pirate last message repeated 4 times
May  5 03:00:45 pirate last message repeated 4 times
May  5 03:01:57 pirate last message repeated 4 times
May  5 03:03:00 pirate last message repeated 6 times
May  5 03:03:42 pirate last message repeated 4 times
May  5 03:04:02 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 03:05:59 pirate last message repeated 5 times
May  5 03:07:01 pirate last message repeated 5 times
May  5 03:07:43 pirate last message repeated 2 times
May  5 03:08:55 pirate last message repeated 5 times
May  5 03:09:48 pirate last message repeated 4 times
May  5 03:11:00 pirate last message repeated 5 times
May  5 03:11:53 pirate last message repeated 5 times
May  5 03:12:55 pirate last message repeated 6 times
May  5 03:13:58 pirate last message repeated 5 times
May  5 03:15:00 pirate last message repeated 4 times
May  5 03:15:52 pirate last message repeated 5 times
May  5 03:16:55 pirate last message repeated 6 times
May  5 03:17:01 pirate /USR/SBIN/CRON[28034]: (root) CMD (   run-parts --report /etc/cron.hourly)
May  5 03:17:05 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 03:17:37 pirate last message repeated 3 times
May  5 03:18:39 pirate last message repeated 5 times
May  5 03:19:41 pirate last message repeated 4 times
May  5 03:20:44 pirate last message repeated 6 times
May  5 03:21:47 pirate last message repeated 6 times
May  5 03:22:49 pirate last message repeated 6 times
May  5 03:23:52 pirate last message repeated 5 times
May  5 03:24:54 pirate last message repeated 4 times
May  5 03:25:56 pirate last message repeated 5 times
May  5 03:26:59 pirate last message repeated 6 times
May  5 03:27:51 pirate last message repeated 5 times
May  5 03:28:54 pirate last message repeated 6 times
May  5 03:29:56 pirate last message repeated 4 times
May  5 03:30:58 pirate last message repeated 4 times
May  5 03:32:01 pirate last message repeated 6 times
May  5 03:32:53 pirate last message repeated 5 times
May  5 03:33:56 pirate last message repeated 6 times
May  5 03:34:58 pirate last message repeated 5 times
May  5 03:36:00 pirate last message repeated 4 times
May  5 03:36:52 pirate last message repeated 5 times
May  5 03:37:55 pirate last message repeated 6 times
May  5 03:38:58 pirate last message repeated 5 times
May  5 03:40:00 pirate last message repeated 5 times
May  5 03:41:02 pirate last message repeated 4 times
May  5 03:41:54 pirate last message repeated 4 times
May  5 03:42:56 pirate last message repeated 6 times
May  5 03:43:59 pirate last message repeated 6 times
May  5 03:45:01 pirate last message repeated 5 times
May  5 03:45:53 pirate last message repeated 4 times
May  5 03:46:56 pirate last message repeated 4 times
May  5 03:47:59 pirate last message repeated 6 times
May  5 03:49:01 pirate last message repeated 6 times
May  5 03:49:53 pirate last message repeated 5 times
May  5 03:50:45 pirate last message repeated 4 times
May  5 03:51:58 pirate last message repeated 5 times
May  5 03:53:01 pirate last message repeated 6 times
May  5 03:53:53 pirate last message repeated 5 times
May  5 03:54:55 pirate last message repeated 4 times
May  5 03:55:58 pirate last message repeated 5 times
May  5 03:57:00 pirate last message repeated 6 times
May  5 03:57:53 pirate last message repeated 5 times
May  5 03:58:55 pirate last message repeated 6 times
May  5 03:59:58 pirate last message repeated 5 times
May  5 04:01:00 pirate last message repeated 5 times
May  5 04:01:52 pirate last message repeated 5 times
May  5 04:02:55 pirate last message repeated 6 times
May  5 04:03:57 pirate last message repeated 6 times
May  5 04:05:00 pirate last message repeated 6 times
May  5 04:06:03 pirate last message repeated 6 times
May  5 04:06:55 pirate last message repeated 4 times
May  5 04:07:57 pirate last message repeated 5 times
May  5 04:09:00 pirate last message repeated 6 times
May  5 04:10:02 pirate last message repeated 6 times
May  5 04:10:55 pirate last message repeated 5 times
May  5 04:11:57 pirate last message repeated 6 times
May  5 04:13:00 pirate last message repeated 6 times
May  5 04:14:03 pirate last message repeated 6 times
May  5 04:14:55 pirate last message repeated 5 times
May  5 04:15:57 pirate last message repeated 6 times
May  5 04:17:00 pirate last message repeated 6 times
May  5 04:17:01 pirate /USR/SBIN/CRON[28760]: (root) CMD (   run-parts --report /etc/cron.hourly)
May  5 04:17:11 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 04:17:42 pirate last message repeated 3 times
May  5 04:18:45 pirate last message repeated 6 times
May  5 04:19:47 pirate last message repeated 5 times
May  5 04:20:49 pirate last message repeated 5 times
May  5 04:21:52 pirate last message repeated 6 times
May  5 04:22:54 pirate last message repeated 5 times
May  5 04:23:57 pirate last message repeated 6 times
May  5 04:24:49 pirate last message repeated 5 times
May  5 04:26:02 pirate last message repeated 6 times
May  5 04:26:43 pirate last message repeated 3 times
May  5 04:27:56 pirate last message repeated 6 times
May  5 04:28:59 pirate last message repeated 5 times
May  5 04:30:01 pirate last message repeated 6 times
May  5 04:31:04 pirate last message repeated 6 times
May  5 04:31:56 pirate last message repeated 5 times
May  5 04:32:58 pirate last message repeated 6 times
May  5 04:34:01 pirate last message repeated 6 times
May  5 04:35:04 pirate last message repeated 6 times
May  5 04:35:56 pirate last message repeated 5 times
May  5 04:36:58 pirate last message repeated 5 times
May  5 04:38:01 pirate last message repeated 5 times
May  5 04:39:03 pirate last message repeated 6 times
May  5 04:39:56 pirate last message repeated 5 times
May  5 04:40:58 pirate last message repeated 6 times
May  5 04:42:01 pirate last message repeated 6 times
May  5 04:43:03 pirate last message repeated 4 times
May  5 04:43:55 pirate last message repeated 5 times
May  5 04:44:58 pirate last message repeated 6 times
May  5 04:46:01 pirate last message repeated 5 times
May  5 04:47:04 pirate last message repeated 6 times
May  5 04:48:06 pirate last message repeated 6 times
May  5 04:48:58 pirate last message repeated 5 times
May  5 04:50:01 pirate last message repeated 6 times
May  5 04:51:03 pirate last message repeated 6 times
May  5 04:52:06 pirate last message repeated 6 times
May  5 04:52:58 pirate last message repeated 4 times
May  5 04:54:00 pirate last message repeated 6 times
May  5 04:55:03 pirate last message repeated 6 times
May  5 04:56:06 pirate last message repeated 6 times
May  5 04:56:58 pirate last message repeated 5 times
May  5 04:58:01 pirate last message repeated 6 times
May  5 04:59:03 pirate last message repeated 4 times
May  5 05:00:05 pirate last message repeated 5 times
May  5 05:00:58 pirate last message repeated 5 times
May  5 05:02:00 pirate last message repeated 6 times
May  5 05:03:03 pirate last message repeated 5 times
May  5 05:04:05 pirate last message repeated 6 times
May  5 05:04:58 pirate last message repeated 5 times
May  5 05:06:00 pirate last message repeated 6 times
May  5 05:07:03 pirate last message repeated 5 times
May  5 05:08:05 pirate last message repeated 5 times
May  5 05:08:58 pirate last message repeated 5 times
May  5 05:10:00 pirate last message repeated 6 times
May  5 05:11:03 pirate last message repeated 6 times
May  5 05:11:55 pirate last message repeated 5 times
May  5 05:12:47 pirate last message repeated 4 times
May  5 05:14:00 pirate last message repeated 6 times
May  5 05:15:03 pirate last message repeated 6 times
May  5 05:16:05 pirate last message repeated 6 times
May  5 05:16:58 pirate last message repeated 5 times
May  5 05:17:01 pirate /USR/SBIN/CRON[29484]: (root) CMD (   run-parts --report /etc/cron.hourly)
May  5 05:17:08 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 05:17:39 pirate last message repeated 3 times
May  5 05:18:42 pirate last message repeated 6 times
May  5 05:19:55 pirate last message repeated 6 times
May  5 05:20:58 pirate last message repeated 6 times
May  5 05:22:00 pirate last message repeated 6 times
May  5 05:22:52 pirate last message repeated 5 times
May  5 05:24:05 pirate last message repeated 5 times
May  5 05:24:57 pirate last message repeated 4 times
May  5 05:26:00 pirate last message repeated 5 times
May  5 05:27:02 pirate last message repeated 6 times
May  5 05:28:05 pirate last message repeated 6 times
May  5 05:28:57 pirate last message repeated 5 times
May  5 05:29:49 pirate last message repeated 5 times
May  5 05:31:02 pirate last message repeated 5 times
May  5 05:32:04 pirate last message repeated 4 times
May  5 05:32:56 pirate last message repeated 5 times
May  5 05:33:59 pirate last message repeated 5 times
May  5 05:35:01 pirate last message repeated 5 times
May  5 05:36:04 pirate last message repeated 6 times
May  5 05:37:07 pirate last message repeated 6 times
May  5 05:37:59 pirate last message repeated 5 times
May  5 05:39:02 pirate last message repeated 6 times
May  5 05:40:04 pirate last message repeated 6 times
May  5 05:40:56 pirate last message repeated 5 times
May  5 05:41:59 pirate last message repeated 5 times
May  5 05:43:02 pirate last message repeated 5 times
May  5 05:44:04 pirate last message repeated 6 times
May  5 05:45:06 pirate last message repeated 5 times
May  5 05:45:48 pirate last message repeated 3 times
May  5 05:47:01 pirate last message repeated 5 times
May  5 05:48:03 pirate last message repeated 5 times
May  5 05:49:06 pirate last message repeated 6 times
May  5 05:49:58 pirate last message repeated 5 times
May  5 05:51:01 pirate last message repeated 6 times
May  5 05:52:03 pirate last message repeated 5 times
May  5 05:53:06 pirate last message repeated 6 times
May  5 05:53:58 pirate last message repeated 4 times
May  5 05:55:00 pirate last message repeated 5 times
May  5 05:56:03 pirate last message repeated 6 times
May  5 05:57:06 pirate last message repeated 6 times
May  5 05:57:58 pirate last message repeated 5 times
May  5 05:59:00 pirate last message repeated 5 times
May  5 06:00:03 pirate last message repeated 6 times
May  5 06:01:06 pirate last message repeated 6 times
May  5 06:01:58 pirate last message repeated 4 times
May  5 06:03:00 pirate last message repeated 5 times
May  5 06:04:03 pirate last message repeated 5 times
May  5 06:05:05 pirate last message repeated 5 times
May  5 06:05:57 pirate last message repeated 5 times
May  5 06:07:00 pirate last message repeated 6 times
May  5 06:08:02 pirate last message repeated 5 times
May  5 06:09:05 pirate last message repeated 6 times
May  5 06:09:57 pirate last message repeated 5 times
May  5 06:11:00 pirate last message repeated 5 times
May  5 06:12:02 pirate last message repeated 6 times
May  5 06:13:05 pirate last message repeated 6 times
May  5 06:13:57 pirate last message repeated 5 times
May  5 06:15:00 pirate last message repeated 6 times
May  5 06:16:02 pirate last message repeated 5 times
May  5 06:16:55 pirate last message repeated 5 times

---

### Post by MIZREE on 2005-05-05
/var/log/syslog:  part2


May  5 06:17:01 pirate /USR/SBIN/CRON[30207]: (root) CMD (   run-parts --report /etc/cron.hourly)
May  5 06:17:05 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 06:17:26 pirate last message repeated 2 times
May  5 06:18:28 pirate last message repeated 5 times
May  5 06:19:31 pirate last message repeated 6 times
May  5 06:20:34 pirate last message repeated 6 times
May  5 06:21:36 pirate last message repeated 5 times
May  5 06:22:28 pirate last message repeated 5 times
May  5 06:23:31 pirate last message repeated 6 times
May  5 06:24:33 pirate last message repeated 5 times
May  5 06:24:54 pirate last message repeated 2 times
May  5 06:25:02 pirate /USR/SBIN/CRON[30305]: (root) CMD (test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily)
May  5 06:25:05 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 06:25:36 pirate last message repeated 2 times
May  5 06:26:28 pirate last message repeated 5 times
May  5 06:27:31 pirate last message repeated 6 times
May  5 06:28:33 pirate last message repeated 6 times
May  5 06:29:35 pirate last message repeated 4 times
May  5 06:30:27 pirate last message repeated 4 times
May  5 06:31:29 pirate last message repeated 5 times
May  5 06:32:32 pirate last message repeated 5 times
May  5 06:33:34 pirate last message repeated 6 times
May  5 06:34:37 pirate last message repeated 5 times
May  5 06:35:28 pirate last message repeated 3 times
May  5 06:36:31 pirate last message repeated 6 times
May  5 06:37:34 pirate last message repeated 6 times
May  5 06:38:36 pirate last message repeated 6 times
May  5 06:39:29 pirate last message repeated 5 times
May  5 06:40:31 pirate last message repeated 6 times
May  5 06:41:34 pirate last message repeated 5 times
May  5 06:42:36 pirate last message repeated 6 times
May  5 06:43:29 pirate last message repeated 5 times
May  5 06:44:31 pirate last message repeated 6 times
May  5 06:45:34 pirate last message repeated 4 times
May  5 06:46:36 pirate last message repeated 5 times
May  5 06:47:18 pirate last message repeated 4 times
May  5 06:48:30 pirate last message repeated 5 times
May  5 06:49:33 pirate last message repeated 5 times
May  5 06:50:36 pirate last message repeated 6 times
May  5 06:51:28 pirate last message repeated 4 times
May  5 06:52:30 pirate last message repeated 6 times
May  5 06:53:33 pirate last message repeated 5 times
May  5 06:54:35 pirate last message repeated 4 times
May  5 06:55:27 pirate last message repeated 5 times
May  5 06:56:19 pirate last message repeated 5 times
May  5 06:57:32 pirate last message repeated 5 times
May  5 06:58:35 pirate last message repeated 6 times
May  5 06:59:27 pirate last message repeated 5 times
May  5 07:00:30 pirate last message repeated 6 times
May  5 07:01:32 pirate last message repeated 6 times
May  5 07:02:35 pirate last message repeated 5 times
May  5 07:03:27 pirate last message repeated 5 times
May  5 07:04:30 pirate last message repeated 6 times
May  5 07:05:32 pirate last message repeated 6 times
May  5 07:06:35 pirate last message repeated 6 times
May  5 07:07:27 pirate last message repeated 5 times
May  5 07:08:30 pirate last message repeated 6 times
May  5 07:09:33 pirate last message repeated 6 times
May  5 07:10:35 pirate last message repeated 6 times
May  5 07:11:27 pirate last message repeated 5 times
May  5 07:12:30 pirate last message repeated 5 times
May  5 07:13:32 pirate last message repeated 6 times
May  5 07:14:35 pirate last message repeated 6 times
May  5 07:15:27 pirate last message repeated 4 times
May  5 07:16:30 pirate last message repeated 6 times
May  5 07:16:51 pirate last message repeated 2 times
May  5 07:17:01 pirate /USR/SBIN/CRON[30932]: (root) CMD (   run-parts --report /etc/cron.hourly)
May  5 07:17:01 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:17:32 pirate last message repeated 3 times
May  5 07:18:35 pirate last message repeated 6 times
May  5 07:19:27 pirate last message repeated 5 times
May  5 07:20:30 pirate last message repeated 6 times
May  5 07:21:33 pirate last message repeated 6 times
May  5 07:22:35 pirate last message repeated 6 times
May  5 07:23:28 pirate last message repeated 5 times
May  5 07:24:30 pirate last message repeated 6 times
May  5 07:25:33 pirate last message repeated 5 times
May  5 07:26:35 pirate last message repeated 6 times
May  5 07:27:17 pirate last message repeated 4 times
May  5 07:27:28 pirate kernel: usb 2-1: new low speed USB device using ohci_hcd and address 2
May  5 07:27:29 pirate kernel: usbcore: registered new driver hiddev
May  5 07:27:30 pirate hal.hotplug[31145]: DEVPATH is not set
May  5 07:27:30 pirate usb.agent[31073]:      usbhid: loaded successfully
May  5 07:27:30 pirate udev[31161]: configured rule in '/etc/udev/rules.d/udev.rules' at line 62 applied, 'ts2' becomes 'input/%k'
May  5 07:27:30 pirate udev[31161]: creating device node '/dev/input/ts2'
May  5 07:27:30 pirate udev[31158]: configured rule in '/etc/udev/rules.d/udev.rules' at line 58 applied, 'mouse2' becomes 'input/%k'
May  5 07:27:30 pirate udev[31158]: creating device node '/dev/input/mouse2'
May  5 07:27:30 pirate kernel: input: USB HID v1.10 Mouse [Fujitsu Takamisawa Component Apple Optical USB Mouse] on usb-0001:10:19.0-1
May  5 07:27:30 pirate kernel: usbcore: registered new driver usbhid
May  5 07:27:30 pirate kernel: drivers/usb/input/hid-core.c: v2.0:USB HID core driver
May  5 07:27:30 pirate udev[31159]: configured rule in '/etc/udev/rules.d/udev.rules' at line 60 applied, 'event5' becomes 'input/%k'
May  5 07:27:30 pirate udev[31159]: creating device node '/dev/input/event5'
May  5 07:27:30 pirate input.agent[31191]:      evdev: already loaded
May  5 07:27:30 pirate input.agent[31191]:      evbug: blacklisted
May  5 07:27:30 pirate input.agent[31165]:      evdev: already loaded
May  5 07:27:30 pirate input.agent[31165]:      evbug: blacklisted
May  5 07:27:30 pirate input.agent[31169]:      evdev: already loaded
May  5 07:27:30 pirate input.agent[31169]:      evbug: blacklisted
May  5 07:27:30 pirate input.agent[31146]:      tsdev: already loaded
May  5 07:27:30 pirate input.agent[31146]:      evdev: already loaded
May  5 07:27:30 pirate input.agent[31146]:      evbug: blacklisted
May  5 07:27:37 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:28:06 pirate last message repeated 2 times
May  5 07:28:54 pirate last message repeated 7 times
May  5 07:28:54 pirate postfix/master[3420]: reload configuration
May  5 07:28:57 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:29:00 pirate kernel: eth1: no IPv6 routers present
May  5 07:29:01 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:29:30 pirate last message repeated 3 times
May  5 07:30:00 pirate last message repeated 3 times
May  5 07:30:01 pirate /USR/SBIN/CRON[31425]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
May  5 07:30:01 pirate anacron[31446]: Anacron 2.3 started on 2005-05-05
May  5 07:30:01 pirate anacron[31446]: Normal exit (0 jobs run)
May  5 07:30:11 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:30:42 pirate last message repeated 3 times
May  5 07:31:22 pirate last message repeated 4 times
May  5 07:31:23 pirate kernel: usb 2-1: USB disconnect, address 2
May  5 07:31:24 pirate udev[31471]: removing device node '/dev/input/mouse2'
May  5 07:31:24 pirate udev[31480]: removing device node '/dev/input/event5'
May  5 07:31:24 pirate udev[31488]: removing device node '/dev/input/ts2'
May  5 07:31:24 pirate hal.hotplug[31496]: DEVPATH is not set
May  5 07:31:32 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:32:03 pirate last message repeated 3 times
May  5 07:33:06 pirate last message repeated 6 times
May  5 07:33:58 pirate last message repeated 4 times
May  5 07:35:01 pirate last message repeated 6 times
May  5 07:36:03 pirate last message repeated 6 times
May  5 07:37:06 pirate last message repeated 6 times
May  5 07:37:48 pirate last message repeated 3 times
May  5 07:39:00 pirate last message repeated 6 times
May  5 07:40:03 pirate last message repeated 6 times
May  5 07:40:33 pirate last message repeated 3 times
May  5 07:40:39 pirate dhclient: Internet Systems Consortium DHCP Client V3.0.1
May  5 07:40:39 pirate dhclient: Copyright 2004 Internet Systems Consortium.
May  5 07:40:39 pirate dhclient: All rights reserved.
May  5 07:40:39 pirate dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
May  5 07:40:39 pirate dhclient: 
May  5 07:40:39 pirate dhclient: sit0: unknown hardware address type 776
May  5 07:40:39 pirate kernel: PHY ID: 4061e4, addr: 0
May  5 07:40:40 pirate dhclient: sit0: unknown hardware address type 776
May  5 07:40:40 pirate kernel: NET: Registered protocol family 17
May  5 07:40:40 pirate dhclient: Listening on LPF/eth0/00:03:93:58:42:2e
May  5 07:40:40 pirate dhclient: Sending on   LPF/eth0/00:03:93:58:42:2e
May  5 07:40:40 pirate dhclient: Sending on   Socket/fallback
May  5 07:40:41 pirate kernel: eth0: Link is up at 100 Mbps, half-duplex.
May  5 07:40:41 pirate kernel: eth0: Pause is disabled
May  5 07:40:44 pirate dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  5 07:40:44 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:40:45 pirate dhclient: DHCPOFFER from 192.168.1.1
May  5 07:40:45 pirate dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
May  5 07:40:45 pirate dhclient: DHCPACK from 192.168.1.1
May  5 07:40:45 pirate dhclient: bound to 192.168.1.5 -- renewal in 281968 seconds.
May  5 07:40:49 pirate kernel: eth0: no IPv6 routers present
May  5 07:40:54 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:40:55 pirate kernel: usb 1-1: new low speed USB device using ohci_hcd and address 2
May  5 07:40:56 pirate hal.hotplug[31738]: DEVPATH is not set
May  5 07:40:56 pirate input.agent[31739]:      tsdev: already loaded
May  5 07:40:56 pirate input.agent[31739]:      evdev: already loaded
May  5 07:40:56 pirate input.agent[31739]:      evbug: blacklisted
May  5 07:40:56 pirate kernel: input: USB HID v1.10 Mouse [Fujitsu Takamisawa Component Apple Optical USB Mouse] on usb-0001:10:18.0-1
May  5 07:40:56 pirate usb.agent[31793]:      usbhid: already loaded
May  5 07:40:57 pirate udev[31826]: configured rule in '/etc/udev/rules.d/udev.rules' at line 58 applied, 'mouse2' becomes 'input/%k'
May  5 07:40:57 pirate udev[31826]: creating device node '/dev/input/mouse2'
May  5 07:40:57 pirate udev[31845]: configured rule in '/etc/udev/rules.d/udev.rules' at line 62 applied, 'ts2' becomes 'input/%k'
May  5 07:40:57 pirate udev[31845]: creating device node '/dev/input/ts2'
May  5 07:40:57 pirate udev[31827]: configured rule in '/etc/udev/rules.d/udev.rules' at line 60 applied, 'event5' becomes 'input/%k'
May  5 07:40:57 pirate udev[31827]: creating device node '/dev/input/event5'
May  5 07:40:57 pirate input.agent[31831]:      evdev: already loaded
May  5 07:40:57 pirate input.agent[31850]:      evdev: already loaded
May  5 07:40:57 pirate input.agent[31850]:      evbug: blacklisted
May  5 07:40:57 pirate input.agent[31869]:      evdev: already loaded
May  5 07:40:57 pirate input.agent[31831]:      evbug: blacklisted
May  5 07:40:57 pirate input.agent[31869]:      evbug: blacklisted
May  5 07:41:04 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:41:07 pirate postfix/master[3420]: reload configuration
May  5 07:41:07 pirate postfix/master[3420]: reload configuration
May  5 07:41:07 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:41:07 pirate dhclient: Internet Systems Consortium DHCP Client V3.0.1
May  5 07:41:07 pirate dhclient: Copyright 2004 Internet Systems Consortium.
May  5 07:41:07 pirate dhclient: All rights reserved.
May  5 07:41:07 pirate dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
May  5 07:41:07 pirate dhclient: 
May  5 07:41:07 pirate dhclient: sit0: unknown hardware address type 776
May  5 07:41:08 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:41:08 pirate dhclient: sit0: unknown hardware address type 776
May  5 07:41:08 pirate dhclient: Listening on LPF/eth0/00:03:93:58:42:2e
May  5 07:41:08 pirate dhclient: Sending on   LPF/eth0/00:03:93:58:42:2e
May  5 07:41:08 pirate dhclient: Sending on   Socket/fallback
May  5 07:41:10 pirate dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  5 07:41:10 pirate dhclient: DHCPOFFER from 192.168.1.1
May  5 07:41:10 pirate dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
May  5 07:41:10 pirate dhclient: DHCPACK from 192.168.1.1
May  5 07:41:10 pirate dhclient: bound to 192.168.1.5 -- renewal in 263460 seconds.
May  5 07:41:10 pirate postfix/master[3420]: reload configuration
May  5 07:41:10 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:41:14 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:41:18 pirate kernel: eth1: no IPv6 routers present
May  5 07:41:23 pirate kernel: eth1: Unknown information frame received (type f202).
May  5 07:42:02 pirate last message repeated 3 times
May  5 07:42:43 pirate last message repeated 4 times
May  5 07:42:52 pirate postfix/master[3420]: reload configuration
May  5 07:44:59 pirate gconfd (alix-25839): Resolved address "xml::/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
May  5 07:44:59 pirate gconfd (alix-25839): None of the resolved addresses are writable; saving configuration settings will not be possible
May  5 07:44:59 pirate gconfd (alix-25839): Resolved address "xml::/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  5 07:44:59 pirate gconfd (alix-25839): None of the resolved addresses are writable; saving configuration settings will not be possible
May  5 08:12:41 pirate -- MARK --
May  5 08:17:02 pirate /USR/SBIN/CRON[1628]: (root) CMD (   run-parts --report /etc/cron.hourly)
May  5 08:32:43 pirate -- MARK --
May  5 08:52:44 pirate -- MARK --
May  5 09:12:44 pirate -- MARK --
May  5 09:17:02 pirate /USR/SBIN/CRON[2428]: (root) CMD (   run-parts --report /etc/cron.hourly)
May  5 09:32:44 pirate -- MARK --
May  5 09:52:44 pirate -- MARK --
May  5 10:12:45 pirate -- MARK --
May  5 10:17:02 pirate /USR/SBIN/CRON[3187]: (root) CMD (   run-parts --report /etc/cron.hourly)
May  5 10:32:45 pirate -- MARK --
May  5 10:52:46 pirate -- MARK --
May  5 11:12:46 pirate -- MARK --

---

### Post by MIZREE on 2005-05-05
May 5 07:29:00 pirate kernel: eth1: no IPv6 routers present
May 5 07:29:01 pirate kernel: eth1: Unknown information frame received (type f202).
May 5 07:29:30 pirate last message repeated 3 times

i suspect this issue is with using ipv6, and hosts list the following which may be an issue: host ff02::2  alias ip6-allrouters

seems too coincidental that same numbers/letters used in error and host listing. may be unrelated, but that is my suspicion.

I dont see anything in router configuration that will enable ipv6.
please let me know if barking up wrong tree, as it does work hardwired im confused.

---

### Post by ssam on 2005-05-05
are you familiar with the ifconfig and iwconfig tools?

they are pretty helpful for diagnosing a connection.

---

### Post by Bug on 2005-05-06
Im using an original Lucent WaveLan Silver card in my wallstreet, which the airport card was based on originally, and it works no problems. Plug and play (after I rebooted). I'd suggest the same things as the post a couple above this. Turn off all security, MAC address filtering, and any other 'special' featuers your router has. Make it as plain jane unsecured 802.11b as you can. Then work your way up to your current conigureation to see whats blocking you out and how to fix. Let us know how it works out,

Adam

---

### Post by poofyhairguy on 2005-05-07
[QUOTE=MIZREE]
I also want to addon packages and codecs etc, to make this dist a bit more useful for me, but when tried an addon cd from umbutuguide.org, realized it and its instructions were for x86 only. oops. I couldn't find much info for extending ppc version with more packages and stuff.[/QUOTE]

I have an Airport. It needs the newest firmware to work well. I don't know how to upgrade firmware outside OSX> Maybe put OSX on, upgrade firmware then put Ubuntu back on...

Here is stuff for media:

[http://ubuntuppc.info/](http://ubuntuppc.info/)

---

