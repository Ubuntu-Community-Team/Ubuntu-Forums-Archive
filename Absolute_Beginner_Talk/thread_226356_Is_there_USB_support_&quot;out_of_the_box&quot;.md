---
title: "Is there USB support &quot;out of the box&quot;?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by esayex on 2006-07-31
Hey all, I was wondering if USB support comes with Ubuntu. None of my USB stuff works, even though I go to Device manager and it recognizes I have it. >_< Any help is appreciated.

Computer specs:
Gateway MX6421 (15.4 in screen laptop)
AMD Turion 64 processor, 1.8 GHz
512 MB RAM
4 USB 2.0 ports.

---

### Post by taurus on 2006-07-31
What kind of USB stuff are you talking here?  My USB thumb drive & digital camera work just fine...

---

### Post by esayex on 2006-07-31
My USB Optical mouse (Labtech) and my USD hard drive (Western Digital) dont work. 

I dont have a flash drive to test with. I'll dig up my digital camera after work today... :P

---

### Post by Denis on 2006-07-31
You should get a list of all the connected USB  devices with "lsusb".

---

### Post by esayex on 2006-07-31
Ok, I booted in "recovery mode" (Linux equivalent of Windows' safe mode?) And I saw a few wierd things in the first all screen black terminal window-thingy

first i had my labtech mouse plugged in and did lsusb

```
root@svwlaptop:~# lsusb

Bus 003 Device 001: ID 000:000
    001        003: ID 1241:1166 Belkin
    001        001: ID 0000:0000
    002        001: ID 0000:0000
```


Then I connected the Western Digital hard drive:

```
root@svwlaptop:~# [17179636.308000] usb 3-2: new high speed USB device using ehci_hcd and address 4
[17179636.308000] Initializing USb Mass starage device
[17179636.308000] scsi 0 : SCSI emulation for USB Mass Storage Devices
[17179636.308000] usbcore: registered new driver usb-storage
[17179636.308000] USB Mass Storage support registered
[17179636.308000] 	Vendor: WDC WD80 Model: 0UE-00HCT0	Rev:0000
[17179636.308000]	Type: Direct-Access	ANSI SCSI revision: 00
[17179636.308000] Driver 'sd' needs updating - please use bus_type methods
[17179636.308000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179636.308000] sda: assuming drive cache: write through
[17179636.308000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179636.308000] sda: assuming drive cache: write through
[17179636.308000]  sda:sda1
[17179636.308000] sd 0:0:0:0: Attached scsi disk sda
[17179636.308000] sd 0:0:0:0: Attached scsi generic sg0 type 0
```

Then a second lsusb

```
root@svwlaptop:~# lsusb

Bus 003 Device 001: ID 1058:0701 Western Digital Technologies, Inc.
    001        003: ID 1241:1166 Belkin
    001        001: ID 0000:0000
    002        001: ID 0000:0000
```

Then disconnect the hard drive:

```
usb 3-2: USB disconnect, address 3
```

lsusb showed up like the first

But when i get into the GUI environment...I can't find the hard drive anywhere, and lsusb in the Terminal doesn't pick it up.

Also a big note...My mouse is made by labtech...not belkin. WTF?

Thanks in advance.

---

### Post by Denis on 2006-08-02
I don't know why the mouse doesn't work, usually you have no problems with usb mouses. Maybe you can try to connect it to another usb port?

can you mount the external HD?

try this in the terminal: 

sudo mkdir /mnt/external
sudo mount /dev/sda1 /mnt/external

can you access your drive at /mnt/external ? (do "ls /mnt/external" e.g.)
This should work if everything is allright.

---

### Post by esayex on 2006-08-02
hmmm...wierd...everything started working. Mouse, hard drive, even my digital camera. I'm not sure what I did (I didn't manually mount it...It just came up on its own...) But it works now. Thanks for all your help ^_^

[EDIT] Nevermind...i guess it was temporary (?). Now this is just confusing me. I'm moving stuff around all my ports. what the deuce is going on? :'(

---

