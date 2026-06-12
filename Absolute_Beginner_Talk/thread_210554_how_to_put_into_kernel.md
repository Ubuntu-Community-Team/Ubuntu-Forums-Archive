---
title: "how to put into kernel"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by eilker1917 on 2006-07-07
Anyone could  tell me , how to do things below?? how will i put those things into kernel??? two days trying with a modem ](*,) 

***********
You MUST include these options (“*” stands for “in the kernel”, “M” stands for “module”):

USB support —>
<M> Support for USB
[ ] USB verbose debug messages
— Miscellaneous USB options[*] Preliminary USB device filesystem
[ ] Enforce USB bandwidth allocation (EXPERIMENTAL)
[ ] Long timeout for slow-responding devices (some MGE Ellipse UPSes)
— USB Host Controller Drivers
< > EHCI HCD (USB 2.0) support (EXPERIMENTAL)
<M> UHCI (Intel PIIX4, VIA, ...) support
<M> UHCI Alternate Driver (JE) support
<M> OHCI (Compaq, iMacs, OPTi, SiS, ALi, ...) support
..
— USB Multimedia devices
..
< > DABUSB driver
..

Character devices —>
..[*] Non-standard serial port support
<M> HDLC line discipline support
..

Network device support —>
..
<M> PPP (point-to-point protocol) support
[ ] PPP multilink support (EXPERIMENTAL)
[ ] PPP filtering
<M> PPP support for async serial ports
<M> PPP support for sync tty ports
<M> PPP Deflate compression
<M> PPP BSD-Compress compression
< > PPP over Ethernet (EXPERIMENTAL)
< > PPP over ATM (EXPERIMENTAL)

*******************
what i must do :(
[http://www.ubuntuforums.org/showpost.php?p=1221741&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1221741&postcount=3)

---

### Post by eilker1917 on 2006-07-07
very very thank you to moderators, i am sure that , it will be answered at "Absolute Begineer Forum " !!! ](*,)  ](*,)  
](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

