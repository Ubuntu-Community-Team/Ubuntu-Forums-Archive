---
title: "manually mounting a usb portable music player"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by fiat42lux on 2008-02-23
Hi,
I'm trying to mount an mp3 player, and thus need to know its name. I've found the relevant lines in the output of lsusb and dmesg, but unfortunately they don't mean all that much to me...
Your help would be most appreciated.

```
fiat42lux@elbeestu:/$ lsusb
Bus 001 Device 006: ID 04e8:508a Samsung Electronics Co., Ltd 
```
```
fiat42lux@elbeestu:/$ dmesg
[26900.976000] usb 1-2.3: new full speed USB device using uhci_hcd and address 7
[26901.084000] usb 1-2.3: not running at top speed; connect to a high speed hub
[26901.112000] usb 1-2.3: configuration #1 chosen from 1 choice
```

---

### Post by loboc on 2008-02-23
try leaving it unplugged and listing the "scsi" devices
```

ls /dev/sd*

```
```

loboc@uburtubur:~$ ls /dev/sd*
/dev/sda  /dev/sda2  /dev/sda5  /dev/sda6  /dev/sda7
```

then plug it in and see if a new one shows up after

```
ls /dev/sd*
```

```
loboc@uburtubur:~$ ls /dev/sd*
/dev/sda  /dev/sda2  /dev/sda5  /dev/sda6  /dev/sda7  [COLOR="Red"]/dev/sdb  /dev/sdb1[/COLOR]
```

---

### Post by fiat42lux on 2008-02-24
Thanks for the reply, but no dice:
```
fiat42lux@elbeestu:~$ ls /dev/sd*
/dev/sda  /dev/sda1
```
...before and after plugging it in.

Something else just occurred to me that I should probably have mentioned: The player is connected to a USB slot, but in Windows, it was represented as "MTP Device" and supported a limited set of file operations. I just looked up [MTP on Wikipedia]("http://en.wikipedia.org/wiki/Media_Transfer_Protocol") and found:
> Support for Media Transfer Protocol in Windows XP requires the installation of Windows Media Player 10 or higher. Apple and Linux systems do not support it natively but have software packages to support it.
I was unable to find any such packages via Applications -> Add/Remove, however. Am I screwed? :(

---

### Post by (((X))) on 2008-02-24
Hell, where do you buy such winsofted devices, I mean..samsung:)

---

