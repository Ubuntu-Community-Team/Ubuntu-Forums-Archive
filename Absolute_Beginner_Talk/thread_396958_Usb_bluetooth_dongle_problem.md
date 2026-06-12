---
title: "Usb bluetooth dongle problem"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by yoodaa on 2007-03-30
hy ... I could use home help in this problem please. I'm a newbie to Kubuntu. I installed Kubuntu 6.10 Edgy on my laptop ( a Dell Inspiron 6400 ) and now I am trying to connect my phone to the laptop using a Canyon CN-BTU4 Bluetooth Dongle.
   hciconfig finds my bluetooth adapter and hcitool scan find my phone. but I can't pair them. 
  besides that from time to time i get the message USB adapter unplugged and after that USB adapter found several times.
  tail -f /var/log/syslog returns 

[17183754.008000] hub 3-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Mar 30 00:24:19 laptop kernel: [17183754.008000] usb 3-1: USB disconnect, address 22
Mar 30 00:24:19 laptop kernel: [17183754.368000] usb 3-1: new full speed USB device using uhci_hcd and address 23
Mar 30 00:24:20 laptop kernel: [17183755.032000] usb 3-1: configuration #1 chosen from 1 choice
Mar 30 00:24:20 laptop kernel: [17183755.276000] hci_cmd_task: hci0 command tx timeout



Mar 30 00:20:52 laptop kernel: [17183547.228000] usb 3-1: new full speed USB device using uhci_hcd and address 21
Mar 30 00:20:52 laptop kernel: [17183547.728000] usb 3-1: configuration #1 chosen from 1 choice
Mar 30 00:20:52 laptop hcid[17605]: HCI dev 0 registered
Mar 30 00:20:52 laptop hcid[17605]: Register path:/org/bluez/hci0 fallback:0
Mar 30 00:20:52 laptop hcid[17605]: HCI dev 0 up
Mar 30 00:20:52 laptop hcid[17605]: Device hci0 has been added
Mar 30 00:20:52 laptop hcid[17605]: Starting security manager 0
Mar 30 00:20:52 laptop kernel: [17183547.872000] hub 3-0:1.0: port 1 disabled by hub  (EMI?),re-enabling...
Mar 30 00:20:52 laptop kernel: [17183547.872000] usb 3-1: USB disconnect, address 21
Mar 30 00:20:52 laptop hcid[17687]: Can't set scan mode on hci0: No such device (19)
Mar 30 00:20:53 laptop kernel: [17183548.252000] usb 3-1: new full speed USB device using uhci_hcd and address 22
Mar 30 00:20:53 laptop kernel: [17183548.752000] usb 3-1: configuration #1 chosen from 1 choice
Mar 30 00:20:54 laptop hcid[17605]: Can't read version info for hci0: Connection timed out (110)
Mar 30 00:20:54 laptop kernel: [17183549.132000] hci_cmd_task: hci0 command tx timeout
Mar 30 00:20:55 laptop hcid[17605]: Sending read scan enable command failed: Connection timed out (110)
Mar 30 00:20:55 laptop hcid[17605]: HCI dev 0 down 
Mar 30 00:20:55 laptop hcid[17605]: Stopping security manager 0
Mar 30 00:20:55 laptop hcid[17605]: Device hci0 has been disabled
Mar 30 00:20:55 laptop hcid[17605]: HCI dev 0 unregistered
Mar 30 00:20:55 laptop hcid[17605]: Unregister path:/org/bluez/hci0

Sometimes hciconfig return address of dongle 00:00:00:00:00

And when i get the dongle to work hcid -n returns
hcid[2188]: Bluetooth HCI daemon
hcid[2188]: Enabling debug information
hcid[2188]: Could not become the primary owner
hcid[2188]: Unable to get on D-Bus

I search for the answer on several forums but none of them solved this.

Can someone please tell me what is the problem and what can I do to fix this?

---

### Post by Chadarius on 2007-04-06
I am having essentially the same problem. However I'm using Feisty 7.04 beta right now. I'm connected just fine with Bluetooth between my phone and the Dell built in bluetooth. But the system keeps disconnecting and connecting the bluetooth adaptor. Here is my /var/log/messages

```
Apr  6 14:47:58 suttonca-laptop kernel: [11513.152000] usb 5-1.4: USB disconnect, address 31
Apr  6 14:47:58 suttonca-laptop pppd[11105]: Hangup (SIGHUP)
Apr  6 14:47:58 suttonca-laptop pppd[11105]: Modem hangup
Apr  6 14:47:58 suttonca-laptop pppd[11105]: Connect time 1.9 minutes.
Apr  6 14:47:58 suttonca-laptop pppd[11105]: Sent 53872 bytes, received 184760 bytes.
Apr  6 14:47:58 suttonca-laptop pppd[11105]: Connection terminated.
Apr  6 14:47:59 suttonca-laptop pppd[11105]: Exit.
Apr  6 14:47:59 suttonca-laptop kernel: [11513.624000] usb 5-1.4: new full speed USB device using ehci_hcd and address 32
Apr  6 14:47:59 suttonca-laptop kernel: [11513.744000] usb 5-1.4: configuration #1 chosen from 1 choice
Apr  6 14:48:54 suttonca-laptop pppd[11196]: pppd 2.4.4 started by suttonca, uid 1000                  
```

---

### Post by Chadarius on 2007-04-26
I created a bug for this disconnect issue.

[https://bugs.launchpad.net/ubuntu/+bug/110402](https://bugs.launchpad.net/ubuntu/+bug/110402)

I just got another Dell laptop and I'm having the same issue on that as I was on my other Dell laptop. So I know I'm not going crazy.

---

### Post by Chadarius on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/110402](https://bugs.launchpad.net/ubuntu/+bug/110402) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/110402](https://bugs.launchpad.net/ubuntu/+bug/110402) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I created a bug for this disconnect issue.

[https://bugs.launchpad.net/ubuntu/+bug/110402](https://bugs.launchpad.net/ubuntu/+bug/110402)

I just got another Dell laptop and I'm having the same issue on that as I was on my other Dell laptop. So I know I'm not going crazy.

---

