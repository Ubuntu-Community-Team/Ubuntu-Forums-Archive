---
title: "USB Ports on Macmini"
date: 2010-05-12
forum: Apple Hardware Users
---

### Post by kmand on 2010-05-12
I want to do copy's from 1 external usb disk to another. I'm trying to decide if there is any advantage to which usb port each is plugged into. I'm not concerned about power, these are externally powered disks. I'm wondering if its possible or advantageous to get them on different usb busses for independent bandwidth.

lsusb (shown below) seems to show 5 usb busses. The Vimtron and JMicron are the external drive controllers. Even when I swap usb plugs between ports, the device numbers change but not the bus number. Is the distinction between busses artificial and they share a total of 480mbits? This is a Mac Mini 2,1 (August 2007)


Bus 005 Device 004: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 003: ID 05ac:8240 Apple, Inc. IR Receiver [build-in]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0430:0005 Sun Microsystems, Inc. Type 6 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0430:0100 Sun Microsystems, Inc. 3-button Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 152d:2509 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 002: ID 1376:3010 Vimtron Electronics Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by kmand on 2010-05-15
Well I did some more experimentation. The bottom line is that this model of the Macmini has only 1 high speed USB bus, and thats what you get for a high speed device no matter where it is plugged in.

Beyond that, for low speed devices, the 2 ports near the DVI connector share a low speed bus, and the 2 outer ports get separate low speed busses.

---

