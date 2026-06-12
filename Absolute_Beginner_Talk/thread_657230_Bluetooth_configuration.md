---
title: "Bluetooth configuration"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by budweiser on 2008-01-03
hi all!
this is my first post on the forums, it took a wjile getting acquainted with it.
i'm glad shipIT sent me the ubuntu cd within 6weeks! i installed ubuntu on my hp pavilion dv2401tu notebook and i was amazed how most of the things seemed to work, best part beibg audio!!!!! (m an audiphile)
ok now coming straight to the point, i m having problems with the Bluetooth configuration. my notebook does see my BT handset but when i try to connec it, it says "obex/104thgkh&*^*%" is not correctly named or something like tht??
can anyone plz guide me on how i can fix this issue?!
many thanks in advance

---

### Post by fiddledd on 2008-01-03
I couldn't use Bluetooth in Ubuntu until I installed gnome-vfs-obexftp with Synaptic. i got a feeling there was something else I installed as well, but try that first.

---

### Post by NilsE on 2008-01-03
You are getting the OBEX message because the headset is not a OBEX (File transfer) device. So, that is not the correct place to connect it.

You will need to make sure gnome-bluetooth and bluez-gnome and bluez-utils are installed. Should be.

To get addr of device in a terminal do:  

sudo hidd --search  
(you may need to do this a few times until it finds it)

Then in a terminal do:
  
sudo hidd --connect 00:07:61:89:32:b9 
(change the address to the one you found)

Once it finds it then mark it as trusted in the Bluetooth Preferences (right click on notification icon). Also make the Mode of Operation Visible and connectible.

---

### Post by budweiser on 2008-01-04
> **NilsE said:**
> You are get
ting the OBEX message because the headset is not a OBEX (File transfer) device. So, that is not the correct place to connect it.

You will need to make sure gnome-bluetooth and bluez-gnome and bluez-utils are installed. Should be.

To get addr of device in a terminal do:  

sudo hidd --search  
(you may need to do this a few times until it finds it)

Then in a terminal do:
  
sudo hidd --connect 00:07:61:89:32:b9 
(change the address to the one you found)

Once it finds it then mark it as trusted in the Bluetooth Preferences (right click on notification icon). Also make the Mode of Operation Visible and connectible.

here are a few things i tried:
-- turned on the Bluetooth and made it connectable to other devices
-- turned on all 4 ports, audio, serial, network and the other one i forgot
-- next i tried to search for my nokia N73 with BT on
-- it found it in first place! but cudnt pair with it :(
-- so i decided to pair my handset with my laptop!
--voila! it was a success
-- then i gave it an approved mark (soryy i seem to forgot what it was, its the same as we have on our mobiles, auto-pair and authorized
-- next when i search for BT devices it show N73 with a lock and a blue (authorization) icon alongside
-- but if i try to connect it, it says "OBEX/1212^(*&^#&#^^#%ll" not named correctly?

Also mercy, i mistakenly removed the "show desktop icon from the taskbar" how do i get it back???:confused:

---

### Post by budweiser on 2008-01-04
okay guys, so finallyfigured out, Terminal=Dos Promt
basically i want to use the PAN and Wireless Network on my notebook.
i do it in vista by clicking on Bluetooth devices and then double clicking on the installed modem.
how can i access internet in ubuntu installed on my notebook (hp pavlion dv2*** series)via my gprs enable mobile phone?!
please help
anyways, here are a few things i treid, but still i'm unable to connect to my mobile phone.
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

---

