---
title: "eth0 drops connection = reboot"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by s1102879 on 2006-11-30
Obviously I'm new to linux and I've been learning a ton on these forums. (finally got my canon printer to print!)  I have one issue that I can't find an answer for.  My machine will randomly "die" and need rebooted. At least once a day.  I don't know what's happening but I did (after looking through the forums) find my logs. Here they are:

Nov 30 00:18:05 localhost -- MARK --
Nov 30 00:38:06 localhost -- MARK --
Nov 30 00:58:06 localhost -- MARK --
Nov 30 01:18:06 localhost -- MARK --
Nov 30 01:38:06 localhost -- MARK --
Nov 30 01:58:07 localhost -- MARK --
Nov 30 02:18:07 localhost -- MARK --
Nov 30 02:38:07 localhost -- MARK --
Nov 30 02:58:07 localhost -- MARK --
Nov 30 03:18:07 localhost -- MARK --
Nov 30 03:38:08 localhost -- MARK --
Nov 30 03:58:08 localhost -- MARK --
Nov 30 04:18:08 localhost -- MARK --
Nov 30 04:38:08 localhost -- MARK --
Nov 30 04:58:09 localhost -- MARK --
Nov 30 05:18:09 localhost -- MARK --
Nov 30 05:38:09 localhost -- MARK --
Nov 30 05:58:09 localhost -- MARK --
Nov 30 06:18:10 localhost -- MARK --
Nov 30 06:38:10 localhost -- MARK --
Nov 30 06:58:10 localhost -- MARK --
Nov 30 07:18:10 localhost -- MARK --
Nov 30 07:18:30 localhost kernel: [17315154.396000] e100: eth0: e100_watchdog: link down
Nov 30 07:18:30 localhost dhcdbd:  dhclient 9114 down (9) but si_code == 0 and releasing==0 !
Nov 30 07:18:36 localhost kernel: [17315160.396000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Nov 30 07:18:36 localhost kernel: [17315160.396000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 30 07:18:40 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Nov 30 07:18:40 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Nov 30 07:18:40 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Nov 30 07:18:40 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Nov 30 07:37:37 localhost exiting on signal 15
Nov 30 07:37:38 localhost syslogd 1.4.1#17ubuntu7: restart.
Nov 30 07:57:38 localhost -- MARK --
Nov 30 08:17:38 localhost -- MARK --
Nov 30 08:37:39 localhost -- MARK --
Nov 30 08:57:39 localhost -- MARK --
Nov 30 09:17:39 localhost -- MARK --
Nov 30 09:37:39 localhost -- MARK --
Nov 30 09:57:40 localhost -- MARK --
Nov 30 10:17:40 localhost -- MARK --
Nov 30 10:37:40 localhost -- MARK --
Nov 30 10:57:40 localhost -- MARK --
Nov 30 17:52:06 localhost syslogd 1.4.1#17ubuntu7: restart.
Nov 30 17:52:06 localhost kernel: Inspecting /boot/System.map-2.6.15-27-386
Nov 30 17:52:06 localhost kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Nov 30 17:52:06 localhost kernel: Symbols match kernel version 2.6.15.
Nov 30 17:52:06 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Nov 30 17:52:07 localhost kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
Nov 30 17:52:07 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Nov 30 17:52:07 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
Nov 30 17:52:07 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009bc00 - 000000000009c000 (reserved)
Nov 30 17:52:07 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Nov 30 17:52:07 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
Nov 30 17:52:07 localhost kernel: [17179569.184000]  BIOS-e820: 000000003ffc0000 - 000000003fff8000 (ACPI data)
Nov 30 17:52:07 localhost kernel: [17179569.184000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
Nov 30 17:52:07 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Nov 30 17:52:07 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 30 17:52:07 localhost kernel: [17179569.184000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Nov 30 17:52:07 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Nov 30 17:52:07 localhost kernel: [17179569.184000] 127MB HIGHMEM available.
Nov 30 17:52:07 localhost kernel: [17179569.184000] 896MB LOWMEM available.
Nov 30 17:52:07 localhost kernel: [17179569.184000] DMI 2.3 present.
Nov 30 17:52:07 localhost kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x408

I'm not sure if this gives anyone and ideas but you can see where the system has to be restarted.  If you need more info I apologize, but I will hunt it down whatever it is.  

Many thanks.

---

### Post by DWright on 2006-11-30
Off hand, it looks like a hardware fault. I would say that the fact that your eth0 interface dies just before a reboot is a "symptom" rather then the cause.
Try booting from another LiveCD (knoppix, INSERT, BartPE, etc) just see if the PC is still rebooting. This will tell you if it is a hardware or a software fault.

---

### Post by s1102879 on 2006-11-30
Okay.  I'll give that a try.  I have a knoppix disc here somewhere.  I'll just start it up and leave it overnight and check in the morning.  Thanks for the suggestion.

---

### Post by s1102879 on 2006-12-01
Doesn't seem to be it.  I let it sit all night (it usually needs a restart because it's locked up in the morning or no eth0 connection) and it was fine this morning. I moved the mouse and the knoppix cd roared to life. 

Anyone have any other experience with this sort of issue.

---

