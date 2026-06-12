---
title: "ubuntu 11.04 not recognising mobile in usb port"
date: 2011-07-13
forum: Australia Team
---

### Post by paul_harris on 2011-07-13
i plug my samsung preston mobile phone into my laptop and it does not get recognised by 11.04, where can i get some drivers.
appreciate some feedback.:)

---

### Post by ikt on 2011-07-13
> **paul_harris said:**
> i plug my samsung preston mobile phone into my laptop and it does not get recognised by 11.04,

It doesn't get recognised at all? If you plug another device in to the same port does it work fine?

---

### Post by hatemii on 2011-07-22
me too .. except that i have Samsung Wave S8500 ..
When I connect it , On unity nothing happens at all ,, but on KDE it gets recognised as a camera ,, but the files won't open ! weird !
:D

---

### Post by ikt on 2011-07-26
> **hatemii said:**
> me too .. except that i have Samsung Wave S8500 ..
When I connect it , On unity nothing happens at all ,, but on KDE it gets recognised as a camera ,, but the files won't open ! weird !
:D

With my android, when I plug it in ubuntu doesn't recognise it straight away, but I get a pop up on my phone that says

"USB connected"
"Turn on USB Storage"

And if I click on the Turn on USB storage button then it shows up in ubuntu as a drive.

---

### Post by Dy1anW on 2011-10-23
This thread is a bit old, so I'm not sure if I should even be resurrecting it, but nevertheless...

I have the same problem as well. I have a HTC, and on a previous version of Ubuntu (think I was using 9.04 or 9.10 the last time I connected my phone to my laptop) the phone recognised it was connected to a comp, and I was able to mount the phone as a removable drive.

Ignore what the version number says in the side, I'm actually on 11.04 (User CP won't let me update), and for some reason my phone doesn't even show the option to connect to PC. The computer recognises the phone though:
```
Bus 001 Device 022: ID 0bb4:0ff9 High Tech Computer Corp.
```And in case you're wondering why it took so long for me to notice, I used to run Windows on my desktop, and the phone used to connect to that most of the time.

Edit: *facepalm*
This is what dmesg shows when I connect my phone:
```
[70097.012091] usb 1-7: new high speed USB device using ehci_hcd and address 25
[70097.163603] scsi28 : usb-storage 1-7:1.0
[70098.168647] scsi 28:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[70098.170073] sd 28:0:0:0: Attached scsi generic sg2 type 0
[70098.202362] sd 28:0:0:0: [sdb] Attached SCSI removable disk
```

---

### Post by ikt on 2011-10-23
> **Dy1anW said:**
> This thread is a bit old, so I'm not sure if I should even be resurrecting it, but nevertheless...

I have the same problem as well. I have a HTC, and on a previous version of Ubuntu (think I was using 9.04 or 9.10 the last time I connected my phone to my laptop) the phone recognised it was connected to a comp, and I was able to mount the phone as a removable drive.

Ignore what the version number says in the side, I'm actually on 11.04 (User CP won't let me update), and for some reason my phone doesn't even show the option to connect to PC. The computer recognises the phone though:
```
Bus 001 Device 022: ID 0bb4:0ff9 High Tech Computer Corp.
```And in case you're wondering why it took so long for me to notice, I used to run Windows on my desktop, and the phone used to connect to that most of the time.

Edit: *facepalm*
This is what dmesg shows when I connect my phone:
```
[70097.012091] usb 1-7: new high speed USB device using ehci_hcd and address 25
[70097.163603] scsi28 : usb-storage 1-7:1.0
[70098.168647] scsi 28:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[70098.170073] sd 28:0:0:0: Attached scsi generic sg2 type 0
[70098.202362] sd 28:0:0:0: [sdb] Attached SCSI removable disk
```

You got it working?

What type of HTC phone do you have?

---

### Post by afrodeity on 2011-12-03
no luck with my Samsung E2220 on Oneiric

---

