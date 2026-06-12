---
title: "USB not connecting for digital camcorder"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by The Dragon Master on 2007-06-04
A friend has a EuroCyber DDV-777X digital video camcorder and we are trying to download photos and mpegs to Ubuntu.  I had never heard of  EuroCyber  and it seems no one else has either,  Googling the camcorder name with "Linux" or "Ubuntu" came up with no hits. The USB does not seem to connect. :-({|=  e.g.

dave@daves-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 06b9:4061 Alcatel Telecom SpeedTouch ISDN or ADSL Modem
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

dave@daves-desktop:~$ man  /var/log/messages
Reformatting messages, please wait...
dave@daves-desktop:~$ dmesg | tail
[17180966.784000] hub 4-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[17180966.896000] usb 4-6: new high speed USB device using ehci_hcd and address 35
[17180967.928000] usb 4-6: new high speed USB device using ehci_hcd and address 36
[17180968.808000] hub 4-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[17180968.920000] usb 4-6: new high speed USB device using ehci_hcd and address 37
[17180969.792000] hub 4-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[17180969.904000] usb 4-6: new high speed USB device using ehci_hcd and address 38
[17180970.312000] usb 4-6: device not accepting address 38, error -71
[17180970.424000] usb 4-6: new high speed USB device using ehci_hcd and address 39
[17180970.832000] usb 4-6: device not accepting address 39, error -71

dave@daves-desktop:~$ sudo tail -f /var/log/messages
Jun  4 23:30:09 daves-desktop kernel: [17180538.724000] usb 4-6: new high speed USB device using ehci_hcd and address 30
Jun  4 23:30:10 daves-desktop kernel: [17180539.244000] usb 4-6: new high speed USB device using ehci_hcd and address 31
Jun  4 23:37:15 daves-desktop kernel: [17180964.400000] usb 4-6: new high speed USB device using ehci_hcd and address 32
Jun  4 23:37:16 daves-desktop kernel: [17180965.384000] usb 4-6: new high speed USB device using ehci_hcd and address 33
Jun  4 23:37:16 daves-desktop kernel: [17180965.912000] usb 4-6: new high speed USB device using ehci_hcd and address 34
Jun  4 23:37:17 daves-desktop kernel: [17180966.896000] usb 4-6: new high speed USB device using ehci_hcd and address 35
Jun  4 23:37:18 daves-desktop kernel: [17180967.928000] usb 4-6: new high speed USB device using ehci_hcd and address 36
Jun  4 23:37:19 daves-desktop kernel: [17180968.920000] usb 4-6: new high speed USB device using ehci_hcd and address 37
Jun  4 23:37:20 daves-desktop kernel: [17180969.904000] usb 4-6: new high speed USB device using ehci_hcd and address 38
Jun  4 23:37:21 daves-desktop kernel: [17180970.424000] usb 4-6: new high speed USB device using ehci_hcd and address 39

Any suggestions welcome.
TDM 	](*,)

---

### Post by pkarjala on 2007-06-04
Do you happen to know the manufactor's website?

---

### Post by Atomic Dog on 2007-06-04
If your camera setup mode will allow you to select the USB mode setting make sure you set it to "PTP." Ubuntu will suddenly see the camera and will start gthumb to pull down the photos.

---

