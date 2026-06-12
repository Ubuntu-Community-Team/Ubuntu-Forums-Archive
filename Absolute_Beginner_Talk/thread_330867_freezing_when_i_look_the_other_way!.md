---
title: "freezing when i look the other way!"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Dmole on 2007-01-03
I and having a problem where i leave my computer Running (XUbuntu 6.06, seeding with Azureus, VSFTPD used, RSSH running but not used). It runs fine for a few days then i find it frozen (black screen, mouse and numlock are not working). I reboot and rememberd the years i ran M$ Server without a crash freeze, or BSOD. I Googled around but did not find any solutions. I also experience system freeze randomly and more frequently on my laptop (running Ubuntu 6.10) but that's for anther time. 


**I am looking for a link to a Tutorial for diagnosing UBUNTU system freezes.**















I found some logs in:
/var/log/syslog.0
/var/log/vsftpd.log.1
/var/log/messages
/var/log/kern.log/home/[me]/.azureus/logs/save/1167866327981_thread_2.log
/home/[me]/.azureus/logs/save/1167866327981_debug_1.log

from witch i find the following respectively:

(...
Dec 31 14:17:01 [me] /USR/SBIN/CRON[5839]: (root) CMD (   run-parts --report /etc/cron.hourly)
Dec 31 14:36:24 [me] -- MARK --
Dec 31 14:56:25 [me] -- MARK --
Jan  3 18:13:43 [me] syslogd 1.4.1#17ubuntu7: restart.
...)


(...
Wed Dec 27 16:41:48 2006 [pid 2214] [ftp] OK DOWNLOAD: Client "
...)

(...
Dec 31 14:56:25 [me] -- MARK --
Jan  3 18:13:43 [me] syslogd 1.4.1#17ubuntu7: restart.
...)

(...
Dec 27 15:04:17 [me] kernel: [17621742.204000] input,hiddev96: USB HID v1.00 Mouse [Gyration GyroPoint RF Technology Receiver] on usb-0000:00:04.2-2
Dec 31 07:35:08 [me] kernel: [17940374.004000] ibm_acpi: ec object not found
Jan  3 18:13:44 [me] kernel: Inspecting /boot/System.map-2.6.15-27-386
...)

(...
[3112 13:19:38] Thread state: elapsed = 10001, cpu = 2050, max = WriteController:WriteSelector (50/0%), mem=130112:29032:1697
[3112 13:19:48] Thread state: elapsed = 10001, cpu = 1120, max = MCGroup:CtrlListener (30/0%), mem=130112:29032:1056
...)


(...
[2911 05:39:16]  
...
[0312 01:03:49] 
...)

from which i gain the knowledge that from 
Dec 31 14:56:25 to Jan  3 18:13:44
my computer was BSOD (black screen of death)
i assume it is black because that's what the screen saver looks like

Thanks in advance




[EDIT]
is there a crash dump somewhere?
should i post this somewhere else or let a moderator move it?
[/EDIT]

---

### Post by Dmole on 2008-04-20
SOLVED: [http://ubuntuforums.org/showthread.php?t=331603&page=2](http://ubuntuforums.org/showthread.php?t=331603&page=2)

---

