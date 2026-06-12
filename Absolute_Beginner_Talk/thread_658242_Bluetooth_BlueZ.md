---
title: "Bluetooth BlueZ"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by budweiser on 2008-01-04
I am absolute beginner of linux and i'm eager to learn more of it.
first off, i wanted to connect to the internet thru my mobile phone's gprs via bluetooth, but unfortunately i'm unable to connect to bluetooth device.
i have the latest Ubuntu 7.10 gusty cd and it has amzingly detected almost all hardware on my laptop! 
i tried these steps
budweiser@budweiser-laptop:~$ hciconfig --all 
hci0:   Type: USB 
        BD Address: 00:1A:6B:BD:23:33 ACL MTU: 1017:8 SCO MTU: 64:8 
        UP RUNNING PSCAN ISCAN INQUIRY 
        RX bytes:7490 acl:26 sco:0 events:339 errors:0 
        TX bytes:1317 acl:23 sco:0 commands:64 errors:0 
        Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80 
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'budweiser-ubuntu' 
        Class: 0x0a010c 
        Service Classes: Networking, Capturing 
        Device Class: Computer, Laptop 
        HCI Ver: 2.0 (0x3) HCI Rev: 0x2129 LMP Ver: 2.0 (0x3) LMP Subver: 0x41cf 
        Manufacturer: Broadcom Corporation (15) 

budweiser@budweiser-laptop:~$ pand --search 
budweiser@budweiser-laptop:~$ dund --search 
budweiser@budweiser-laptop:~$ pand --connect -c<00:1B:EE:94:D6:F6> 
bash: syntax error near unexpected token `newline' 
budweiser@budweiser-laptop:~$ pand --connect -c<00:1A:6B:23:33> 
bash: syntax error near unexpected token `newline' 
budweiser@budweiser-laptop:~$
but still i'm unable to connect to any device, any clues:confused:

---

### Post by Cariro on 2008-02-06
I don't know if this is what you need but have a look:
[http://www.3eportal.com/index.php?option=com_content&task=view&id=13&Itemid=9]("http://www.3eportal.com/index.php?option=com_content&task=view&id=13&Itemid=9")

---

