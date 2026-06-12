---
title: "Lacie USB hard disk in EXT3, error"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by kukuku on 2007-12-28
Hello.

I just formatted a Lacie 500gb USB drive with the command,

```
mkfs.ext /dev/sdf1
```

The drive manual only said it supports Windows and Mac filesystems, but I saw discussions about other Lacie drives using EXT3. mkfs completed the task in a matter of minutes, but when I try to mount the drive it only results in the error,

```
Cannot mount volume
Unable to mount the volume 'LaCie'.

mount: wrong fs type, bad option, bad superblock on /dev/sdf1,
missing codepage or helper program, or other error
In some cases useful info is found on syslog -try   dmesg | tail   or so
```

```
sami@groovebox:~$ dmesg | tail
[249975.848000] usb 2-4.3: reset high speed USB device using ehci_hcd and address 5
[250338.064000] usb 2-4.3: reset high speed USB device using ehci_hcd and address 5
[250470.072000] usb 2-4.3: reset high speed USB device using ehci_hcd and address 5
[250535.544000] usb 2-4.3: reset high speed USB device using ehci_hcd and address 5
[251061.564000] usb 2-4.3: reset high speed USB device using ehci_hcd and address 5
[251145.572000] usb 2-4.3: reset high speed USB device using ehci_hcd and address 5
[251245.048000] usb 2-4.3: reset high speed USB device using ehci_hcd and address 5
[251664.528000] FAT: bogus number of reserved sectors
[251664.528000] VFS: Can't find a valid FAT filesystem on dev sdf1.
[251709.052000] usb 2-4.3: reset high speed USB device using ehci_hcd and address 5
```

Is there any way to fix this? Thanks for any help.

---

### Post by taurus on 2007-12-28
Use gparted to format it to ext3 if you wish.  Or you can use mke2fs command if you know the name of the device.

```
sudo mke2fs -j /dev/sdf1
```

---

