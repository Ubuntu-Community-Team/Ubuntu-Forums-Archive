---
title: "Install on a g4?"
date: 2011-01-11
forum: Apple Hardware Users
---

### Post by moore.bryan on 2011-01-11
I've installed Debian from USB on my Mac g4 in the past, but can't seem to get it going after reinstalling Mac OS X. I've tried "dd"-ing the USB with the Natty PPC daily iso, using Unetbootin, and Ubuntu's own USB creator, but to no avail. When I use any of those methods and hold-down the Option key as I turn on the Mac, the boot menu only registers the USB when it's "dd"-ed, but can't load it.

Any ideas? Thanks, in-advance.

---

### Post by linuxopjemac on 2011-01-12
dd the contents onto a stick, then boot from open firmware either with:
```
boot usb0/disk@1:2,\\yaboot
```
or
```
boot usb1/disk@1:2,\\yaboot
```

---

### Post by moore.bryan on 2011-01-12
> **linuxopjemac said:**
> dd the contents onto a stick, then boot from open firmware either with:
```
boot usb0/disk@1:2,\\yaboot
```
or
```
boot usb1/disk@1:2,\\yaboot
```
Thanks, linuxopjemac, but where should I type those commands? In a term on the Mac?

---

### Post by shawnhcorey on 2011-01-12
> **moore.bryan said:**
> Thanks, linuxopjemac, but where should I type those commands? In a term on the Mac?

The second link below tells how to boot from OPen Firmware.

[LIST]
[*][HOWTO Create A Bootable USB Drive From An ISO Image For Apple PowerPCs In Linux]("http://sites.google.com/site/shawnhcorey/howto-create-a-bootable-usb-drive-from-an-iso-image-for-apple-powerpcs-in-linux")
[*][HOWTO Boot Apple PowerPCs From A USB Drive In Open Firmware]("http://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware")
[/LIST]

---

### Post by moore.bryan on 2011-01-12
.

---

### Post by moore.bryan on 2011-01-12
.

---

### Post by moore.bryan on 2011-01-12
Unfortunately, mac-fuse is no longer in Ubuntu. APT claims it's contained in gnu-fdisk, but after I install that and "man fdisk," mac-fdisk doesn't seem to be an option any longer.

Regardless, I tried using GParted, created a "mac" partition map, and formatted the partition HFS.

I then ran down to the "Loading the ISO files" section and hit a snag:
```


blue-asus liveusb # (cd ./iso ; tar cBpf - .) | (cd ./usb ; tar xvBpf -)
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
tar: -: Cannot write: Broken pipe
tar: Error is not recoverable: exiting now

```
Not sure where to go from here.

Thanks so much for your help so far, though!

BTW: Any reason why I need to jump through so many hoops to get Ubuntu going when--and for the life of me I can't remember how I did it--Debian installed in a flash before?

---

### Post by moore.bryan on 2011-01-16
Any help?

---

### Post by moore.bryan on 2011-04-02
> **shawnhcorey said:**
> 
[LIST]
[*][HOWTO Create A Bootable USB Drive From An ISO Image For Apple PowerPCs In Linux]("http://sites.google.com/site/shawnhcorey/howto-create-a-bootable-usb-drive-from-an-iso-image-for-apple-powerpcs-in-linux")
[*][HOWTO Boot Apple PowerPCs From A USB Drive In Open Firmware]("http://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware")
[/LIST]
Sorry to have let this thread go so long with input, but I didn't have time to try anything out until today. I was able to use the commands on the above two webpages and put Natty on my USB; however, when I try and boot I receive two errors:
```

Claim error, can't allocate b00000 at 0xc2000000
Claim error, can't allocate kernel memory

```
Any ideas on this one?

---

### Post by moore.bryan on 2011-05-18
Broke-down and burned a CD... crappy, but a solution.

---

