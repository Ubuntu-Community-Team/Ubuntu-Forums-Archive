---
title: "bluetooth difficulty with 6.10"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by jrsoft on 2007-03-27
I am having some problems with a blue tooth mouse and keyboard with 6.10. With system as installed neither blue tooth keyboard or mouse work. I can see the keyboard during boot. If I change one line in /etc/default/bluetooth, I can see the Apple bluetooth mouse. I change the line with the following 

BLUETOOTH_ENABLE=0

 to the following

BLUETOOTH_ENABLE=1

Is there a way to leave it enabled and not disconnect the keyboard from boot.

I can scan and see both mouse and keyboard but neither will connect. Both fail giving me a BAD ADDRESS error message. 

Thanks in advance. I am using an Apple Wireless Keboard and Wireless MightMouse with a G5 dual booting from a external FW Seagate.

I left a response to a Apple PPC thread on Mighty Mouse problem with my problem.
 
Thanks in advance

---

### Post by jrsoft on 2007-03-27
Went back to wired mouse and keyboard to try again with bluetooth. Modified 
/etc/default/bluetooth

Put back 
BLUETOOTH_ENABLE=1

Added
HIDD_ENABLED=1
HIDD_OPTIONS=" -i xx:xx:xx:xx:xx:xx --server"

used address of both devices in HIDD_OPTIONS lines.

result in daemon.log is the following

Mar 27 21:28:17 jack-desktop hcid[4694]: Bluetooth HCI daemon
Mar 27 21:28:17 jack-desktop hcid[4694]: Unknown option 'auth' line 60
Mar 27 21:28:17 jack-desktop hcid[4694]: Register path:/org/bluez fallback:1
Mar 27 21:28:17 jack-desktop sdpd[4698]: Bluetooth SDP daemon 
Mar 27 21:28:17 jack-desktop hidd[4718]: Bluetooth HID daemon (00:0A:95:3B:56:75)
Mar 27 21:28:18 jack-desktop hcid[4694]: HCI dev 0 registered
Mar 27 21:28:18 jack-desktop hcid[4694]: Register path:/org/bluez/hci0 fallback:0
Mar 27 21:28:18 jack-desktop hcid[4694]: HCI dev 0 up
Mar 27 21:28:18 jack-desktop hcid[4694]: Device hci0 has been added
Mar 27 21:28:18 jack-desktop hcid[4694]: Starting security manager 0
Mar 27 21:28:18 jack-desktop hcid[4694]: Device hci0 has been activated
Mar 27 21:28:18 jack-desktop hcid[4694]: return_link_keys (sba=00:0D:93:0D:0F:B4, dba=00:A0:96:20:E4:8A)
Mar 27 21:28:18 jack-desktop hcid[4694]: return_link_keys (sba=00:0D:93:0D:0F:B4, dba=00:14:51:C9:F5:66)
Mar 27 21:28:18 jack-desktop hcid[4694]: return_link_keys (sba=00:0D:93:0D:0F:B4, dba=00:0A:95:3B:56:75)
Mar 27 21:28:18 jack-desktop hcid[4694]: return_link_keys (sba=00:0D:93:0D:0F:B4, dba=00:0A:95:02:78:2F)
Mar 27 21:28:28 jack-desktop hcid[4860]: Can't set scan mode on hci0: Connection timed out (110)


I need to make both Bluetooth Mouse and Keyboard to work.

---

