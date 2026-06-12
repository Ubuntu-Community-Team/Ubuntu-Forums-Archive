---
title: "USB not working"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by kg00005 on 2006-11-21
Hello All,

My system is not recognizing USB devices, altough I use USB mouse, and keyboard.
There is nothing in /var/log/messages and /var/log/syslog when I plug in USB devices.

A few things about my system - DELL GX-280.

# uname -a
Linux PC100790 2.6.12-10-686 #1 Fri Apr 28 13:21:56 UTC 2006 i686 GNU/Linux

# lspci -v|grep HCI
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])

# dmesg|grep HCI
[4294673.477000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294673.567000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294673.581000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294703.012000] Bluetooth: HCI device and connection manager initialized
[4294703.012000] Bluetooth: HCI socket layer initialized

?????

Regards,
G

---

### Post by michas_u on 2006-11-21
Hello,

Sorry, but I cann't help you, but I have a similar problem. If I boot form the Live CD, i can with my USB-keyboard chose the boot options, but after the boot screen my keyboard dooesn't work.

I think we have the similar problem, if i have a answer to this problem i write it.

I hope we have betimes an answer.

---

