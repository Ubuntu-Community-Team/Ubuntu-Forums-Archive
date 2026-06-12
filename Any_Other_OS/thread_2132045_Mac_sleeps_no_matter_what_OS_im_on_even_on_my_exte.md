---
title: "Mac sleeps no matter what OS im on even on my external with ubuntu"
date: 2013-04-03
forum: Any Other OS
---

### Post by snowlizard31 on 2013-04-03
I don't know why but my mac goes to sleep on OSX while watching a video on youtube or anyother site some times even after running multiple applications; Does the same thing on my Windows 7 partition within the internal drive but it only does it when I'm running games or watching videos for a longer period of time than OSX. It even does this on Ubuntu on my external drive but it does it randomly and with more frequency. Its not a power savings problem as I've done all I can to save power and my HDD S.M.A.R.T status is ok  according to disk utility. Is there any way of figuring whats causing this problem?

Here is what some of the system log says on my mac partition
```

Apr  3 13:09:23 eulalio-gonzalezs-imac ntpd[19]: sendto(17.151.16.23) (fd=24): Network is unreachable
Apr  3 13:09:24 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:09:24 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:09:24 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:09:24 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:09:24 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:09:33 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:09:33 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:09:33 eulalio-gonzalezs-imac configd[13]: PMConnection AirPort configd plug-in com.apple.powermanagement.applicationresponse.slowresponse 133 ms
Apr  3 13:09:33 eulalio-gonzalezs-imac configd[13]: PMConnection mDNSResponder com.apple.powermanagement.applicationresponse.slowresponse 133 ms
Apr  3 13:09:33 eulalio-gonzalezs-imac configd[13]: PMConnection IPConfiguration com.apple.powermanagement.applicationresponse.slowresponse 134 ms
Apr  3 13:09:48 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:09:48.002 PM - Waketime:4/3/2013 1:09:48.000 PM = Deltatime:0.002311051
Apr  3 13:09:48 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:09:48 eulalio-gonzalezs-imac ntpd[19]: sendto(17.151.16.23) (fd=26): Can't assign requested address
Apr  3 13:09:50 eulalio-gonzalezs-imac ntpd[19]: sendto(17.151.16.23) (fd=24): No route to host
Apr  3 13:09:52 eulalio-gonzalezs-imac ntpd[19]: sendto(17.151.16.23) (fd=24): Network is unreachable
Apr  3 13:09:52 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:09:52 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:09:55 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:09:55 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:09:55 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:09:55 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:10:18 eulalio-gonzalezs-imac loginwindow[30]: no spins reported for this wake
Apr  3 13:10:18 eulalio-gonzalezs-imac [0x0-0x2f02f].backupd-helper[646]: Not starting Time Machine backup after wake - failed to resolve alias to backup volume
Apr  3 13:11:17 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:11:22 eulalio-go
Apr  3 13:11:27 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:11:27 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:11:27 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:11:27 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:11:27 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:11:27 eulalio-gonzalezs-imac configd[13]: PMConnection mDNSResponder com.apple.powermanagement.applicationresponse.slowresponse 209 ms
Apr  3 13:11:27 eulalio-gonzalezs-imac configd[13]: PMConnection IPConfiguration com.apple.powermanagement.applicationresponse.slowresponse 353 ms
Apr  3 13:11:27 eulalio-gonzalezs-imac configd[13]: PMConnection AirPort configd plug-in com.apple.powermanagement.applicationresponse.slowresponse 358 ms
Apr  3 13:11:34 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:11:34.002 PM - Waketime:4/3/2013 1:11:34.000 PM = Deltatime:0.002341092
Apr  3 13:11:34 eulalio-gonzalezs-imac configd[13]: PMConnection IPConfiguration com.apple.powermanagement.applicationresponse.slowresponse 116 ms
Apr  3 13:11:34 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:11:35 eulalio-gonzalezs-imac ntpd[19]: sendto(17.151.16.23) (fd=26): Can't assign requested address
Apr  3 13:11:38 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:11:38 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:11:39 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:11:39 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:11:39 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:11:39 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:11:46 eulalio-gonzalezs-imac ntpd[19]: time reset +0.761757 s
Apr  3 13:12:05 eulalio-gonzalezs-imac loginwindow[30]: no spins reported for this wake
Apr  3 13:12:05 eulalio-gonzalezs-imac [0x0-0x33033].backupd-helper[666]: Not starting Time Machine backup after wake - failed to resolve alias to backup volume
Apr  3 13:12:13 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:12:13 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:12:22 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:12:22.002 PM - Waketime:4/3/2013 1:12:22.000 PM = Deltatime:0.002253890
Apr  3 13:12:22 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:12:22 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:12:26 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:12:26 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:12:26 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:12:28 eulalio-gonzalezs-imac ntpd[19]: time reset +0.689790 s
Apr  3 13:12:29 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:12:29 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:12:29 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:12:29 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:12:53 eulalio-gonzalezs-imac loginwindow[30]: no spins reported for this wake
Apr  3 13:12:53 eulalio-gonzalezs-imac [0x0-0x35035].backupd-helper[679]: Not starting Time Machine backup after wake - failed to resolve alias to backup volume
Apr  3 13:13:15 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:13:15 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:13:19 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:13:19.002 PM - Waketime:4/3/2013 1:13:19.000 PM = Deltatime:0.001748085
Apr  3 13:13:19 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:13:19 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:13:23 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:13:23 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:13:23 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:13:23 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:13:23 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:13:23 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:13:23 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:13:24 eulalio-gonzalezs-imac configd[13]: PMConnection mDNSResponder com.apple.powermanagement.applicationresponse.slowresponse 139 ms
Apr  3 13:13:24 eulalio-gonzalezs-imac configd[13]: PMConnection IPConfiguration com.apple.powermanagement.applicationresponse.slowresponse 140 ms
Apr  3 13:13:24 eulalio-gonzalezs-imac configd[13]: PMConnection AirPort configd plug-in com.apple.powermanagement.applicationresponse.slowresponse 147 ms
Apr  3 13:13:43 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:13:43.002 PM - Waketime:4/3/2013 1:13:43.000 PM = Deltatime:0.001747906
Apr  3 13:13:43 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:13:47 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:13:47 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:13:50 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:13:50 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:13:50 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:13:50 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:14:13 eulalio-gonzalezs-imac loginwindow[30]: no spins reported for this wake
Apr  3 13:14:13 eulalio-gonzalezs-imac [0x0-0x39039].backupd-helper[700]: Not starting Time Machine backup after wake - failed to resolve alias to backup volume
Apr  3 13:15:40 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:15:53 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:15:53.002 PM - Waketime:4/3/2013 1:15:53.000 PM = Deltatime:0.001650095
Apr  3 13:15:53 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:16:00 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:16:00 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:16:00 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:16:00 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:16:05 eulalio-gonzalezs-imac ntpd[19]: time reset +0.415349 s
Apr  3 13:16:24 eulalio-gonzalezs-imac loginwindow[30]: no spins reported for this wake
Apr  3 13:16:24 eulalio-gonzalezs-imac [0x0-0x3c03c].backupd-helper[720]: Not starting Time Machine backup after wake - failed to resolve alias to backup volume
Apr  3 13:16:49 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:16:49 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:16:54 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:16:54.002 PM - Waketime:4/3/2013 1:16:54.000 PM = Deltatime:0.002317905
Apr  3 13:16:54 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:16:54 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:16:58 eulalio-gonzalezs-imac ntpd[19]: sendto(17.151.16.23) (fd=24): Network is unreachable
Apr  3 13:16:58 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:16:59 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:16:59 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:16:59 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:16:59 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:16:59 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:16:59 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:16:59 eulalio-gonzalezs-imac configd[13]: PMConnection mDNSResponder com.apple.powermanagement.applicationresponse.slowresponse 459 ms
Apr  3 13:16:59 eulalio-gonzalezs-imac configd[13]: PMConnection IPConfiguration com.apple.powermanagement.applicationresponse.slowresponse 621 ms
Apr  3 13:16:59 eulalio-gonzalezs-imac configd[13]: PMConnection AirPort configd plug-in com.apple.powermanagement.applicationresponse.slowresponse 624 ms
Apr  3 13:17:01 eulalio-gonzalezs-imac ntpd[19]: sendto(17.151.16.23) (fd=26): Network is down
Apr  3 13:17:05 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:17:05.002 PM - Waketime:4/3/2013 1:17:05.000 PM = Deltatime:0.002451062
Apr  3 13:17:05 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:17:06 eulalio-gonzalezs-imac ntpd[19]: sendto(17.151.16.23) (fd=26): Can't assign requested address
Apr  3 13:17:09 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:17:09 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:17:10 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:17:10 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:17:10 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:17:10 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:17:10 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:17:10 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:17:10 eulalio-gonzalezs-imac configd[13]: PMConnection mDNSResponder com.apple.powermanagement.applicationresponse.slowresponse 301 ms
Apr  3 13:17:10 eulalio-gonzalezs-imac configd[13]: PMConnection IPConfiguration com.apple.powermanagement.applicationresponse.slowresponse 459 ms
Apr  3 13:17:10 eulalio-gonzalezs-imac configd[13]: PMConnection AirPort configd plug-in com.apple.powermanagement.applicationresponse.slowresponse 620 ms
Apr  3 13:17:15 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:17:15.002 PM - Waketime:4/3/2013 1:17:15.000 PM = Deltatime:0.002210081
Apr  3 13:17:15 eulalio-gonzalezs-imac ntpd[19]: sendto(17.151.16.23) (fd=26): Can't assign requested address
Apr  3 13:17:17 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:17:19 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:17:19 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:17:19 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:17:19 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:17:22: --- last message repeated 1 time ---
Apr  3 13:17:22 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:17:22 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:17:22 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:17:31 eulalio-gonzalezs-imac ntpd[19]: time reset +0.245630 s
Apr  3 13:17:46 eulalio-gonzalezs-imac loginwindow[30]: no spins reported for this wake
Apr  3 13:17:49 eulalio-gonzalezs-imac [0x0-0x44044].backupd-helper[753]: Not starting Time Machine backup after wake - failed to resolve alias to backup volume
Apr  3 13:17:54 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:17:54 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:18:01 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:18:01.002 PM - Waketime:4/3/2013 1:18:01.000 PM = Deltatime:0.001767099
Apr  3 13:18:01 eulalio-gonzalezs-imac configd[13]: PMConnection mDNSResponder com.apple.powermanagement.applicationresponse.slowresponse 127 ms
Apr  3 13:18:01 eulalio-gonzalezs-imac configd[13]: PMConnection AirPort configd plug-in com.apple.powermanagement.applicationresponse.slowresponse 133 ms
Apr  3 13:18:01 eulalio-gonzalezs-imac configd[13]: PMConnection IPConfiguration com.apple.powermanagement.applicationresponse.slowresponse 135 ms
Apr  3 13:18:01 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:18:01 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:18:05 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:18:05 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:18:05 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:18:06 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:18:06 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:18:06 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:18:06 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:18:29 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:18:29 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:18:29 eulalio-gonzalezs-imac configd[13]: PMConnection AirPort configd plug-in com.apple.powermanagement.applicationresponse.slowresponse 141 ms
Apr  3 13:18:29 eulalio-gonzalezs-imac configd[13]: PMConnection mDNSResponder com.apple.powermanagement.applicationresponse.slowresponse 141 ms
Apr  3 13:18:29 eulalio-gonzalezs-imac configd[13]: PMConnection IPConfiguration com.apple.powermanagement.applicationresponse.slowresponse 142 ms
Apr  3 13:18:33 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:18:33.001 PM - Waketime:4/3/2013 1:18:33.000 PM = Deltatime:0.001452088
Apr  3 13:18:33 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:18:33 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:18:34 eulalio-gonzalezs-imac ntpd[19]: sendto(17.151.16.23) (fd=26): Can't assign requested address
Apr  3 13:18:37 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:18:37 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:18:37 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:18:37 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:18:37 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:18:37 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:18:37 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:19:02 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:19:02 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:19:02 eulalio-gonzalezs-imac configd[13]: PMConnection AirPort configd plug-in com.apple.powermanagement.applicationresponse.slowresponse 137 ms
Apr  3 13:19:02 eulalio-gonzalezs-imac configd[13]: PMConnection mDNSResponder com.apple.powermanagement.applicationresponse.slowresponse 137 ms
Apr  3 13:19:02 eulalio-gonzalezs-imac configd[13]: PMConnection IPConfiguration com.apple.powermanagement.applicationresponse.slowresponse 138 ms
Apr  3 13:19:06 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:19:06.002 PM - Waketime:4/3/2013 1:19:06.000 PM = Deltatime:0.002309084
Apr  3 13:19:06 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:19:06 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:19:10 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:19:10 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:19:10 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:19:10 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:19:10 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - PWRB
Apr  3 13:19:10 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:19:10 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:19:10 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback WILL sleep
Apr  3 13:19:10 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:19:11 eulalio-gonzalezs-imac configd[13]: PMConnection AirPort configd plug-in com.apple.powermanagement.applicationresponse.slowresponse 135 ms
Apr  3 13:19:11 eulalio-gonzalezs-imac configd[13]: PMConnection mDNSResponder com.apple.powermanagement.applicationresponse.slowresponse 135 ms
Apr  3 13:19:11 eulalio-gonzalezs-imac configd[13]: PMConnection IPConfiguration com.apple.powermanagement.applicationresponse.slowresponse 136 ms
Apr  3 13:19:14 eulalio-gonzalezs-imac loginwindow[30]: loginwindow SleepWakeCallback will power on, Currenttime:4/3/2013 1:19:14.004 PM - Waketime:4/3/2013 1:19:14.000 PM = Deltatime:0.003748000
Apr  3 13:19:14 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:19:14 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:19:14 eulalio-gonzalezs-imac configd[13]: Sleep: Success - AC - Low Power Sleep
Apr  3 13:19:14 eulalio-gonzalezs-imac configd[13]: Wake: Success - AC - EHC2
Apr  3 13:19:14 eulalio-gonzalezs-imac configd[13]: Hibernate Statistics
Apr  3 13:19:17 eulalio-gonzalezs-imac configd[13]: network configuration changed.
Apr  3 13:19:17 eulalio-gonzalezs-imac mDNSResponder[29]: DeregisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:19:17 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (FE80:0000:0000:0000:021E:C2FF:FEC2:D4F3)
Apr  3 13:19:17 eulalio-gonzalezs-imac mDNSResponder[29]: RegisterInterface: Frequent transitions for interface en1 (192.168.1.100)
Apr  3 13:19:25 eulalio-gonzalezs-imac ntpd[19]: time reset +0.455079 s
Apr  3 13:19:45 eulalio-gonzalezs-imac loginwindow[30]: no spins reported for this wake
Apr  3 13:19:45 eulalio-gonzalezs-imac [0x0-0x4c04c].backupd-helper[796]: Not starting Time Machine backup after wake - failed to resolve alias to backup volume
 

```

---

### Post by UltimateCat on 2013-04-03
Hi:

I don't have a Mac but I do have a few ideas.;-)

If there is something like a 'Power Management' settings Manager go into that and un-check 'hibernate'
If you know where your configuration file for hibernation is maybe in the file you can disable it. (or) comment out one of the lines.

```

     To remove the sleep image file: sudo rm -rf /var/vm/sleepimage
      To disable safe sleep mode: sudo pmset hibernatemode 0

```
Found these cmd's half way down this page-
[http://www.tuaw.com/2011/08/22/why-hibernate-or-safe-sleep-mode-is-no-longer-necessary-in-os/](http://www.tuaw.com/2011/08/22/why-hibernate-or-safe-sleep-mode-is-no-longer-necessary-in-os/)

These Mac articles may help:
[http://news.metaparadigma.de/osx86-enable-and-disable-hibernation-57/](http://news.metaparadigma.de/osx86-enable-and-disable-hibernation-57/)
[https://discussions.apple.com/thread/4168865?start=0&tstart=0](https://discussions.apple.com/thread/4168865?start=0&tstart=0)
[http://wingedboar.net/2012/02/20/disable-safesleep-hibernation-mac-os-x/](http://wingedboar.net/2012/02/20/disable-safesleep-hibernation-mac-os-x/)


Which Mac do you have?   Mac Book Pro?  For the OS; Snow Leoppard?  X Lion?

---

### Post by snowlizard31 on 2013-04-04
I have an iMac 8,1 with snow leopard 10.6.8 and windows 7 ultimate on the internal drive. I'm pretty sure this has nothing to do with hibernation or sleep mode because I've disabled it in preferences and it does it no matter what OS I'm running not just OSX.

---

