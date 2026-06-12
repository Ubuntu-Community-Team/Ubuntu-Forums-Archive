---
title: "Dial-Up &amp; Internet Connection SLOW"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-10-26
Please see the posts below this one. The modem's speed is down to 12 kilobaud per second. Yikes.

---

### Post by nickpaton on 2006-10-26
If you are using Firefox as your browser, have a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=87798]("http://www.ubuntuforums.org/showthread.php?t=87798")

---

### Post by Mark_in_Hollywood on 2006-10-26
I followed the thread, but now my surfing is down to 12 kilobaud. Yikes!

I'm now at a public terminal.

Below is a paste of the /var/log/messages relevant to pppd and serial:

From:

/var/log/messages


[COLOR="DarkOrange"]Oct 26 09:04:13 localhost kernel: No module symbols loaded - kernel modules not enabled. [/COLOR] 

What does the foregoing mean?

Oct 26 09:04:13 localhost kernel: [17179571.476000][COLOR="darkorange"] PCI quirk[/COLOR]: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Oct 26 09:04:13 localhost kernel: [17179571.476000][COLOR="darkorange"] PCI quirk[/COLOR]: region 0500-053f claimed by ICH4 GPIO

are quirks a problem? What tests them? What repairs quirks?



Oct 26 09:04:13 localhost kernel: [17179571.500000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

Oct 26 09:04:13 localhost kernel: [17179571.904000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled

Oct 26 09:04:13 localhost kernel: [17179571.904000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

Oct 26 09:04:13 localhost kernel: [17179571.908000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

Oct 26 09:04:13 localhost kernel: [17179571.908000] **** SET: [COLOR="darkorange"]Misaligned resource pointer[/COLOR]: cfeff122 Type 07 Len 0

What is "Misaligned" with what? How do I fix this, if necessary?

Oct 26 09:04:13 localhost kernel: [17179571.908000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 3

Oct 26 09:04:13 localhost kernel: [17179571.908000] PCI: setting IRQ 3 as level-triggered

Oct 26 09:04:13 localhost kernel: [17179571.908000] ACPI: PCI Interrupt 0000:01:0d.0[A] -> Link [LNKF] -> GSI 3 (level, low) -> IRQ 3

Oct 26 09:04:13 localhost kernel: [17179571.908000] 0000:01:0d.0: [COLOR="darkorange"]ttyS4 at I/O 0xc800 (irq = 3)[/COLOR] is a 16550A

this is where Linux/Ubuntu have the modem


Oct 26 09:04:13 localhost kernel: [17179577.456000] **** SET: Misaligned resource pointer: cea05d02 Type 07 Len 0

Oct 26 09:04:13 localhost kernel: [17179591.364000] **** SET: Misaligned resource pointer: cd3f02a2 Type 07 Len 0

Oct 26 09:04:13 localhost kernel: [17179607.424000] PPP generic driver version 2.4.2

Oct 26 09:04:22 localhost kernel: [17179620.448000] **** SET: Misaligned resource pointer: cb406e22 Type 07 Len 0

Oct 26 09:08:59 localhost pppd[3519]: Exit.
Oct 26 09:10:47 localhost exiting on signal 15
Oct 26 09:10:48 localhost syslogd 1.4.1#17ubuntu7: restart.
Oct 26 09:23:48 localhost pppd[5598]: pppd 2.4.4b1 started by mark, uid 0
Oct 26 09:23:51 localhost pppd[5598]: Exit.
Oct 26 09:23:51 localhost pppd[5600]: pppd 2.4.4b1 started by mark, uid 0
Oct 26 09:23:52 localhost pppd[5600]: Serial connection established.
Oct 26 09:23:52 localhost pppd[5600]: Using interface ppp0
Oct 26 09:23:52 localhost pppd[5600]: Connect: ppp0 <--> /dev/ttyS4
Oct 26 09:23:53 localhost pppd[5600]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Oct 26 09:24:23 localhost pppd[5600]: LCP: timeout sending Config-Requests 
Oct 26 09:24:23 localhost pppd[5600]: Connection terminated.
Oct 26 09:24:24 localhost pppd[5600]: Modem hangup
Oct 26 09:24:24 localhost pppd[5600]: Exit.

Oct 26 09:27:42 localhost pppd[5758]: pppd 2.4.4b1 started by root, uid 0
Oct 26 09:27:43 localhost chat[5759]: abort on (BUSY)
Oct 26 09:27:43 localhost chat[5759]: abort on (NO CARRIER)
Oct 26 09:27:43 localhost chat[5759]: abort on (VOICE)
Oct 26 09:27:43 localhost chat[5759]: abort on (NO DIALTONE)
Oct 26 09:27:43 localhost chat[5759]: abort on (NO DIAL TONE)
Oct 26 09:27:43 localhost chat[5759]: abort on (NO ANSWER)
Oct 26 09:27:43 localhost chat[5759]: abort on (DELAYED)
Oct 26 09:27:43 localhost chat[5759]: send (ATZ ^M)
Oct 26 09:27:43 localhost chat[5759]: expect (OK)
Oct 26 09:27:43 localhost chat[5759]: ATZ ^M^M
Oct 26 09:27:43 localhost chat[5759]: OK
Oct 26 09:27:43 localhost chat[5759]:  -- got it 
Oct 26 09:27:43 localhost chat[5759]: send (5555555555^M)
Oct 26 09:27:44 localhost chat[5759]: expect (CONNECT)
Oct 26 09:27:44 localhost chat[5759]: ^M
Oct 26 09:28:29 localhost chat[5759]: alarm
Oct 26 09:28:29 localhost chat[5759]: Failed
Oct 26 09:28:59 localhost pppd[5758]: Terminating on signal 15
Oct 26 09:28:59 localhost pppd[5758]: Exit.

Oct 26 09:32:13 localhost shutdown[4259]: shutting down for system reboot

Oct 26 09:33:38 localhost kernel: [17179575.504000] **** SET: Misaligned resource pointer: cfefe122 Type 07 Len 0

Oct 26 09:33:45 localhost kernel: [17179618.780000] **** SET: Misaligned resource pointer: cb8eae22 Type 07 Len 0

Oct 26 09:35:30 localhost pppd[4938]: pppd 2.4.4b1 started by root, uid 0
Oct 26 09:35:30 localhost pppd[4938]: Using interface ppp0
Oct 26 09:35:30 localhost pppd[4938]: [COLOR="darkorange"]Connect: ppp0 <--> /dev/ttyS4[/COLOR]
Oct 26 09:35:43 localhost kernel: [17179735.812000] PPP BSD Compression module registered
Oct 26 09:35:43 localhost kernel: [17179735.944000] PPP Deflate Compression module registered
Oct 26 09:35:43 localhost pppd[4938]: local  IP address 66.81.xx.xxx
Oct 26 09:35:43 localhost pppd[4938]: remote IP address 69.19.xxx.xx
Oct 26 09:35:43 localhost pppd[4938]: primary   DNS address 69.19.xxx.xxx
Oct 26 09:35:43 localhost pppd[4938]: secondary DNS address 66.81.xx.xxx
Oct 26 09:38:24 localhost pppd[3519]: Exit.

Oct 26 10:28:35 localhost pppd[4938]: Terminating on signal 15
Oct 26 10:28:35 localhost pppd[4938]: Connect time 52.9 minutes.
Oct 26 10:28:35 localhost pppd[4938]: Sent 887384 bytes, received 3794089 bytes.
Oct 26 10:28:46 localhost gconfd (mark-4540): Exiting

Oct 26 10:30:20 localhost kernel: [17179572.776000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Oct 26 10:30:20 localhost kernel: [17179572.776000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 26 10:30:20 localhost kernel: [17179572.780000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 26 10:30:20 localhost kernel: [17179572.780000] **** SET: Misaligned resource pointer: cfeff122 Type 07 Len 0

Oct 26 10:30:20 localhost kernel: [17179578.336000] **** SET: Misaligned resource pointer: cfbebd02 Type 07 Len 0

Oct 26 11:46:47 localhost pppd[4943]: pppd 2.4.4b1 started by root, uid 0
Oct 26 11:46:47 localhost pppd[4943]: Using interface ppp0
Oct 26 11:46:47 localhost pppd[4943]: Connect: ppp0 <--> /dev/ttyS4
Oct 26 11:46:56 localhost kernel: [17179758.704000] PPP BSD Compression module registered
Oct 26 11:46:56 localhost kernel: [17179759.316000] PPP Deflate Compression module registered
Oct 26 11:47:08 localhost pppd[4943]: local  IP address 66.81.22.69
Oct 26 11:47:08 localhost pppd[4943]: remote IP address 69.19.219.54
Oct 26 11:47:08 localhost pppd[4943]: primary   DNS address 69.19.190.116
Oct 26 11:47:08 localhost pppd[4943]: secondary DNS address 66.81.1.252
Oct 26 11:49:16 localhost pppd[3518]: Exit.
Oct 26 11:59:40 localhost pppd[4943]: Terminating on signal 15
Oct 26 11:59:40 localhost pppd[4943]: Connect time 12.6 minutes.

---

### Post by seijuro on 2006-10-26
try setting your modem speed to 576...baud in the config for your dialer sometimes if it is set too high the system will load a much lower speed.

---

