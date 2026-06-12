---
title: "boot-eth0 not running when ntpd tries"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by movrshakr on 2007-12-17
[SIZE="2"]I have a new installation of Gutsy desktop up and running, but am seeing some problems I am not geek enough to figure out.

I have ntp installed.  During boot, though, ntpd starts before eth0 is working.  As a result, it ends up loaded and running but is not associated with any of the specified servers in ntp.conf.  So I have to manually restart it from a prompt after login.  Not handy at all.

This seems to be because eth0 has problems getting up, but eventually it always does. It tries eight times, getting only to stage 3, before finally getting stages 4-5 done

Is there any way to make sure the ntp daemon does not try to start until eth0 is fully up? Or solve why eth0 makes so many reattempts?

Here is the parts of a syslog that show eth0 and ntp attempts.
[/SIZE]
------------------- BEGIN SYSLOG ----------

Dec 17 08:15:31 maximus kernel: [   20.868958] eth0: VIA Rhine II at 0x1c000, 00:e0:4c:a0:51:0a, IRQ 20.
Dec 17 08:15:31 maximus kernel: [   20.869674] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
.
.
Dec 17 08:15:32 maximus kernel: [   36.079563] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Dec 17 08:15:32 maximus NetworkManager: <info>  eth0: Device is fully-supported using driver 'via-rhine'. 
Dec 17 08:15:32 maximus NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Dec 17 08:15:32 maximus NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 17 08:15:32 maximus NetworkManager: <debug> [1197897332.608187] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3059_oss_pcm_1'). 
Dec 17 08:15:32 maximus NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
.
Dec 17 08:15:32 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 17 08:15:32 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 17 08:15:32 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 17 08:15:32 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. .
.
Dec 17 08:15:32 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 17 08:15:32 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 17 08:15:32 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 17 08:15:32 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 17 08:15:32 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 17 08:15:32 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 17 08:15:33 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 17 08:15:33 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 17 08:15:33 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 17 08:15:33 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 17 08:15:33 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 17 08:15:33 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 17 08:15:33 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 17 08:15:33 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 17 08:15:33 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 17 08:15:33 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 17 08:15:33 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 17 08:15:33 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 17 08:15:33 maximus ntpd[4937]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Dec 17 08:15:33 maximus ntpd[4938]: precision = 1.000 usec
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 17 08:15:33 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 17 08:15:33 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 17 08:15:33 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 17 08:15:33 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 17 08:15:33 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 17 08:15:33 maximus kernel: [   37.491155] NET: Registered protocol family 10
Dec 17 08:15:33 maximus kernel: [   37.491339] lo: Disabled Privacy Extensions
Dec 17 08:15:33 maximus ntpd[4938]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Dec 17 08:15:33 maximus ntpd[4938]: Listening on interface #1 wildcard, ::#123 Disabled
Dec 17 08:15:33 maximus ntpd[4938]: bind() fd 18, family 10, port 123, scope 2, addr fe80::2e0:4cff:fea0:510a, in6_is_addr_multicast=0 flags=17 fails: Cannot assign requested address
Dec 17 08:15:33 maximus ntpd[4938]: unable to create socket on eth0 (2) for fe80::2e0:4cff:fea0:510a#123
Dec 17 08:15:33 maximus ntpd[4938]: failed to initialize interface for address fe80::2e0:4cff:fea0:510a
Dec 17 08:15:33 maximus ntpd[4938]: Listening on interface #3 lo, ::1#123 Enabled
Dec 17 08:15:33 maximus ntpd[4938]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Dec 17 08:15:33 maximus ntpd[4938]: kernel time sync status 0040
Dec 17 08:15:34 maximus kernel: [   37.546947] Failure registering capabilities with primary security module.
Dec 17 08:15:34 maximus avahi-daemon[4986]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Dec 17 08:15:34 maximus avahi-daemon[4986]: Successfully dropped root privileges.
Dec 17 08:15:34 maximus avahi-daemon[4986]: avahi-daemon 0.6.20 starting up.
Dec 17 08:15:34 maximus avahi-daemon[4986]: Successfully called chroot().
Dec 17 08:15:34 maximus avahi-daemon[4986]: Successfully dropped remaining capabilities.
Dec 17 08:15:34 maximus avahi-daemon[4986]: No service file found in /etc/avahi/services.
Dec 17 08:15:34 maximus avahi-daemon[4986]: Network interface enumeration completed.
Dec 17 08:15:34 maximus avahi-daemon[4986]: Registering new address record for fe80::2e0:4cff:fea0:510a on eth0.*.
Dec 17 08:15:34 maximus avahi-daemon[4986]: Server startup complete. Host name is maximus.local. Local service cookie is 2984269540.
Dec 17 08:15:34 maximus avahi-daemon[4986]: Registering HINFO record with values 'I686'/'LINUX'.
Dec 17 08:15:34 maximus ntpd[4938]: frequency initialized 109.581 PPM from /var/lib/ntp/ntp.drift
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 17 08:15:34 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 17 08:15:34 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 17 08:15:34 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 17 08:15:34 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 17 08:15:34 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 17 08:15:34 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 17 08:15:34 maximus avahi-daemon[4986]: Withdrawing address record for fe80::2e0:4cff:fea0:510a on eth0.
Dec 17 08:15:34 maximus dhcdbd: Started up.
Dec 17 08:15:34 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 17 08:15:34 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 17 08:15:34 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 17 08:15:35 maximus kernel: [   38.744888] [drm] Initialized drm 1.1.0 20060810
Dec 17 08:15:35 maximus kernel: [   38.760846] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 22
Dec 17 08:15:35 maximus kernel: [   38.764065] [drm] Initialized radeon 1.27.0 20060524 on minor 0
Dec 17 08:15:35 maximus anacron[5099]: Anacron 2.3 started on 2007-12-17
Dec 17 08:15:35 maximus anacron[5099]: Will run job `cron.daily' in 5 min.
Dec 17 08:15:35 maximus anacron[5099]: Jobs will be executed sequentially
Dec 17 08:15:35 maximus /usr/sbin/cron[5126]: (CRON) INFO (pidfile fd = 3)
Dec 17 08:15:35 maximus /usr/sbin/cron[5127]: (CRON) STARTUP (fork ok)
Dec 17 08:15:35 maximus /usr/sbin/cron[5127]: (CRON) INFO (Running @reboot jobs)
Dec 17 08:15:36 maximus ntpd_initres[5001]: host name not found: 0.pool.ntp.org
Dec 17 08:15:36 maximus ntpd_initres[5001]: couldn't resolve `0.pool.ntp.org', giving up on it
Dec 17 08:15:36 maximus ntpd_initres[5001]: host name not found: 1.pool.ntp.org
Dec 17 08:15:36 maximus ntpd_initres[5001]: couldn't resolve `1.pool.ntp.org', giving up on it
Dec 17 08:15:36 maximus ntpd_initres[5001]: host name not found: 2.pool.ntp.org
Dec 17 08:15:36 maximus ntpd_initres[5001]: couldn't resolve `2.pool.ntp.org', giving up on it
Dec 17 08:15:36 maximus ntpd_initres[5001]: host name not found: pool.ntp.org
Dec 17 08:15:36 maximus ntpd_initres[5001]: couldn't resolve `pool.ntp.org', giving up on it.
...
Dec 17 08:15:36 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 17 08:15:36 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 17 08:15:36 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 17 08:15:36 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 17 08:15:36 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 17 08:15:36 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 17 08:15:36 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 17 08:15:36 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 17 08:15:36 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 17 08:15:36 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 17 08:15:36 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 17 08:15:36 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 17 08:15:36 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 17 08:15:36 maximus kernel: [   40.349516] [drm] Setting GART location based on new memory map
Dec 17 08:15:36 maximus kernel: [   40.349563] [drm] writeback test succeeded in 1 usecs
Dec 17 08:15:37 maximus NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Dec 17 08:15:37 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 17 08:15:37 maximus NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Dec 17 08:15:38 maximus NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Dec 17 08:15:38 maximus kernel: [   42.316068] NET: Registered protocol family 17
Dec 17 08:15:40 maximus dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Dec 17 08:15:41 maximus dhclient: DHCPACK from 192.168.1.1
Dec 17 08:15:41 maximus avahi-daemon[4986]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.201.
Dec 17 08:15:41 maximus avahi-daemon[4986]: New relevant interface eth0.IPv4 for mDNS.
Dec 17 08:15:41 maximus avahi-daemon[4986]: Registering new address record for 192.168.1.201 on eth0.IPv4.
Dec 17 08:15:43 maximus dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Dec 17 08:15:43 maximus dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1 
Dec 17 08:15:43 maximus dhcdbd: dhco_input_option: Value -644245096 cannot be converted to type L 
Dec 17 08:15:43 maximus dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_rebinding_time = -644245096 
Dec 17 08:15:43 maximus NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Dec 17 08:15:43 maximus NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec 17 08:15:43 maximus NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Dec 17 08:15:43 maximus dhclient: bound to 192.168.1.201 -- renewal in 949586304 seconds.
Dec 17 08:15:43 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Dec 17 08:15:43 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Dec 17 08:15:43 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec 17 08:15:43 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Dec 17 08:15:43 maximus NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Dec 17 08:15:43 maximus NetworkManager: <info>    address 
Dec 17 08:15:43 maximus NetworkManager: <info>    netmask  
Dec 17 08:15:43 maximus NetworkManager: <info>    broadcast 
Dec 17 08:15:43 maximus NetworkManager: <info>    gateway  
Dec 17 08:15:43 maximus NetworkManager: <info>    nameserver  
Dec 17 08:15:43 maximus NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec 17 08:15:43 maximus NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Dec 17 08:15:43 maximus NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Dec 17 08:15:43 maximus avahi-daemon[4986]: Withdrawing address record for 192.168.1.201 on eth0.
Dec 17 08:15:43 maximus avahi-daemon[4986]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.201.
Dec 17 08:15:43 maximus avahi-daemon[4986]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 17 08:15:43 maximus avahi-daemon[4986]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.201.
Dec 17 08:15:43 maximus avahi-daemon[4986]: New relevant interface eth0.IPv4 for mDNS.
Dec 17 08:15:43 maximus avahi-daemon[4986]: Registering new address record for 192.168.1.201 on eth0.IPv4.
Dec 17 08:15:44 maximus NetworkManager: <info>  Clearing nscd hosts cache. 
Dec 17 08:15:44 maximus NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Dec 17 08:15:44 maximus NetworkManager: <info>  Activation (eth0) successful, device activated. 
Dec 17 08:15:44 maximus NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Dec 17 08:15:44 maximus NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Dec 17 08:15:44 maximus ntpdate[5294]: the NTP socket is in use, exiting
Dec 17 08:15:45 maximus avahi-daemon[4986]: Registering new address record for fe80::2e0:4cff:fea0:510a on eth0.*.
Dec 17 08:15:54 maximus kernel: [   57.786128] eth0: no IPv6 routers present
----------------- END SYSLOG --------------------------------

---

