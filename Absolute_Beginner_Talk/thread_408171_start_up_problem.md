---
title: "start up problem"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Benifited on 2007-04-13
when i start up my ubuntu it tells me that the log screen is crashing and then it shows me a generic log in is there anyway that i can fix this

---

### Post by deadgobby on 2007-04-13
at that prompt type in 
sudo fsck
 <enter passwork>
 See if good old fsck will repair it.
Gobby

---

### Post by amohanty on 2007-04-13
Can you be a bit more explicit?
What message do you get?
When?
WHat does the generic login look like?

AM

---

### Post by Benifited on 2007-04-13
> **amohanty said:**
> Can you be a bit more explicit?
What message do you get?
When?
WHat does the generic login look like?

AM


i get it after the ubuntu loader its a message  it says: the greeter is crashing  attempt to log in. thats not it word for word thats what it  tells me. then it takes me to the gnime log screen.

---

### Post by Benifited on 2007-04-13
bump

---

### Post by justleen on 2007-04-13
did you install any graphics drivers before it started crashign by any chance?

after the crash, are you still able to get into a terminal (you might need to press CTRL-ALT-2)?
see if you can login there..

---

### Post by Benifited on 2007-04-13
> **justleen said:**
> did you install any graphics drivers before it started crashign by any chance?

after the crash, are you still able to get into a terminal (you might need to press CTRL-ALT-2)?
see if you can login there..

i can login but  the thing is that after the ubuntu loader it gives me that message then it just takes me to another  login screen instead of the default 1

---

### Post by amohanty on 2007-04-13
After logging in can you post the outputs of:
**dmesg | tail -n 100**
**cat /var/log/Xorg.0.log | grep EE**


AM

---

### Post by Benifited on 2007-04-14
> **amohanty said:**
> After logging in can you post the outputs of:
**dmesg | tail -n 100**
**cat /var/log/Xorg.0.log | grep EE**


AM


oh man im sry but im a noob so i don't know wat that means

---

### Post by Benifited on 2007-04-14
> **Benifited said:**
> oh man im sry but im a noob so i don't know wat that means


ok nvm i got what u where saying this is what i get:

santanastown@SantanasTown:~$ dmesg | tail -n 100
[17179579.668000] usb usb2: configuration #1 chosen from 1 choice
[17179579.668000] hub 2-0:1.0: USB hub found
[17179579.668000] hub 2-0:1.0: 2 ports detected
[17179579.844000] Attempting manual resume
[17179579.892000] kjournald starting.  Commit interval 5 seconds
[17179579.892000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.912000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[17179580.100000] usb 1-2: configuration #1 chosen from 1 choice
[17179592.564000] FDC 0 is a post-1991 82077
[17179592.744000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.748000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.880000] input: PC Speaker as /class/input/input1
[17179592.884000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.888000] agpgart: Detected an Intel i845 Chipset.
[17179592.904000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179593.048000] hw_random: RNG not detected
[17179593.084000] logips2pp: Detected unknown logitech mouse model 62
[17179593.128000] parport: PnPBIOS parport detected.
[17179593.128000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[17179593.568000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[17179593.680000] ts: Compaq touchscreen protocol output
[17179593.828000] gameport: EMU10K1 is pci0000:02:08.1/gameport0, io 0xdcd8, speed 932kHz
[17179594.040000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1716
[17179594.040000] usbcore: registered new driver usblp
[17179594.040000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179594.040000] usbcore: registered new driver libusual
[17179594.092000] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[17179594.092000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179594.116000] eth0: Davicom DM9102 at pci0000:02:0a.0, 00:80:ad:20:8c:de, irq 169.
[17179594.228000] SCSI subsystem initialized
[17179594.248000] Initializing USB Mass Storage driver...
[17179594.248000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179594.248000] usbcore: registered new driver usb-storage
[17179594.248000] USB Mass Storage support registered.
[17179594.248000] usb-storage: device found at 2
[17179594.248000] usb-storage: waiting for device to settle before scanning
[17179594.528000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179595.056000] lp0: using parport0 (interrupt-driven).
[17179595.116000] fuse init (API version 7.6)
[17179595.184000] Adding 1124508k swap on /dev/disk/by-uuid/9a7287f5-d61d-4cd4-8a91-ee5cb30bb23c.  Priority:-1 extents:1 across:1124508k
[17179595.260000] EXT3 FS on hda1, internal journal
[17179595.728000] NET: Registered protocol family 17
[17179599.252000] usb-storage: device scan complete
[17179599.256000]   Vendor: Canon     Model: MP460Storage      Rev: 0103
[17179599.256000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179599.340000] sd 0:0:0:0: Attached scsi removable disk sda
[17179599.360000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179600.148000] NET: Registered protocol family 10
[17179600.148000] lo: Disabled Privacy Extensions
[17179600.148000] IPv6 over IPv4 tunneling driver
[17179602.568000] ACPI: Power Button (FF) [PWRF]
[17179602.568000] ACPI: Power Button (CM) [VBTN]
[17179602.772000] ibm_acpi: ec object not found
[17179602.820000] pcc_acpi: loading...
[17179606.844000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179606.848000] [fglrx] Maximum main memory to use for locked dma buffers: 314 MBytes.
[17179606.848000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179607.136000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179610.456000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179610.456000] apm: overridden by ACPI.
[17179611.092000] eth0: no IPv6 routers present
[17179616.676000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179620.916000] Bluetooth: Core ver 2.8
[17179620.916000] NET: Registered protocol family 31
[17179620.916000] Bluetooth: HCI device and connection manager initialized
[17179620.916000] Bluetooth: HCI socket layer initialized
[17179620.992000] Bluetooth: L2CAP ver 2.8
[17179620.992000] Bluetooth: L2CAP socket layer initialized
[17179620.996000] Bluetooth: RFCOMM socket layer initialized
[17179620.996000] Bluetooth: RFCOMM TTY layer initialized
[17179620.996000] Bluetooth: RFCOMM ver 1.7
[17180945.004000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17180945.172000] usb 2-1: configuration #1 chosen from 1 choice
[17180968.908000] /dev/vmmon[5800]: Module vmmon: registered with major=10 minor=165
[17180968.908000] /dev/vmmon[5800]: Module vmmon: initialized
[17180969.164000] /dev/vmnet: open called by PID 5823 (vmnet-bridge)
[17180969.164000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17180969.164000] /dev/vmnet: port on hub 0 successfully opened
[17180969.164000] bridge-eth0: enabling the bridge
[17180969.164000] bridge-eth0: up
[17180969.164000] bridge-eth0: already up
[17180969.164000] bridge-eth0: attached
[17180969.236000] /dev/vmnet: open called by PID 5835 (vmnet-natd)
[17180969.236000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17180969.236000] /dev/vmnet: port on hub 8 successfully opened
[17180979.220000] /dev/vmnet: open called by PID 5864 (vmnet-netifup)
[17180979.220000] /dev/vmnet: port on hub 8 successfully opened
[17180979.228000] /dev/vmnet: open called by PID 5863 (vmnet-netifup)
[17180979.228000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17180979.228000] /dev/vmnet: port on hub 1 successfully opened
[17180981.000000] /dev/vmnet: open called by PID 5890 (vmnet-dhcpd)
[17180981.000000] /dev/vmnet: port on hub 1 successfully opened
[17180981.352000] /dev/vmnet: open called by PID 5889 (vmnet-dhcpd)
[17180981.352000] /dev/vmnet: port on hub 8 successfully opened
[17180989.344000] vmnet1: no IPv6 routers present
[17180990.772000] vmnet8: no IPv6 routers present
[17189196.640000] usb 2-1: USB disconnect, address 2
[17257156.912000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[17257157.112000] usb 2-1: configuration #1 chosen from 1 choice
[17261363.508000] usb 2-1: USB disconnect, address 3
santanastown@SantanasTown:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

---

### Post by amohanty on 2007-04-14
Damn wacom tablet crap. I dont understand why that's installed by default. Oh well. ok in a terminal try the following:

cd /etc/X11
sudo -s
cp xorg.conf xorg.conf.org
gedit xorg.conf

Now an editor will pop up that will have the file in it, Look for and comment (ie prefix with the has char: # ) the following:

> Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


and the following:

>  InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"


Save the file. Quit the editor

Then in the still open terminal type: <Ctrl>D

Keep in mind that **sudo -s** gives you a root shell, so be very very very careful as to what you do in there.

HTH
AM

---

### Post by ubromtoo on 2007-04-14
Had the same problem with 6.06 Dapper : I was told to try 

System > Administration > Login Window > Accessibility  

 and then to UNcheck the " Enable accessible login " option 

       It worked for me ....hope this helps   :)

---

### Post by amohanty on 2007-04-14
I thought that was disabled by default

---

### Post by Benifited on 2007-04-14
> **amohanty said:**
> Damn wacom tablet crap. I dont understand why that's installed by default. Oh well. ok in a terminal try the following:

cd /etc/X11
sudo -s
cp xorg.conf xorg.conf.org
gedit xorg.conf

Now an editor will pop up that will have the file in it, Look for and comment (ie prefix with the has char: # ) the following:

sry im lost here do u want me to look for that or to copy that into it?


and the following:



Save the file. Quit the editor

Then in the still open terminal type: <Ctrl>D

Keep in mind that **sudo -s** gives you a root shell, so be very very very careful as to what you do in there.

HTH
AM


sry im lost here do u want me to look for that or to copy that into it

---

### Post by amohanty on 2007-04-14
What you want to try is to 
- backup your xserver config file
- edit it (comment out the sections I mentioned above)
- save the changes
- restart xserver using <ctrl><alt><backspace>

HTH
AM

---

### Post by Benifited on 2007-04-14
> **ubromtoo said:**
> Had the same problem with 6.06 Dapper : I was told to try 

System > Administration > Login Window > Accessibility  

 and then to UNcheck the " Enable accessible login " option 

       It worked for me ....hope this helps   :)

oh man thx bro that worked thx!!!!!!!!!!!

---

