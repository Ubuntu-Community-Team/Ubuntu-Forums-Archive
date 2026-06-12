---
title: "need alternative to Etcher to install ubuntu on MAC"
date: 2024-02-22
forum: Apple Hardware Users
---

### Post by d3vlabs on 2024-02-22
Im trying to install Ubuntu on MAC. Can someone recommend an alternative to Etcher? The earliest version of Etcher doesnt support Mac 10.8.5 (starting 10.9 only), which is all I have access to. (unupgradeable on my hardware)


Reffering to this
[https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#community](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#community)

Also how can I find out whats the oldest version of Ubuntu that supports my MAC hardware?

---

### Post by howefield on 2024-02-22
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by TheFu on 2024-02-23
You can use **cp**, but you'll need to know how the OS names different storage devices.  Any program that moves/copies bits unmolested can be used.

On Linux, I use a command like this:
```
sudo cp /path/to/ubuntu-xx.yy.iso  /dev/sdZ
```

Put your path to the ISO in and be 100% certain you understand how USB flash drives are named in your OS. Point at the whole drive device file, not a partition.

I think **diskutil list** on MacOS will show the different drives, so you can get the name from that. People report that it doesn't show USB storage devices. IDK.
**system_profiler SPUSBDataType** should get the USB drives listed.  

I've made a bunch of assumptions based on MacOS being Unix-like. Some Unix commands don't work the same on MacOS as they do on all other Unix variants.

If you get the copy target device wrong, it will be a very, very, very, bad day.  Total data or OS loss is possible. Be very careful.

---

### Post by oldfred on 2024-02-23
> Also how can I find out whats the oldest version of Ubuntu that supports my MAC hardware?

Typically the newer the distribution the better the support.
It is only if system is so old that drivers have been obsoleted, often for security reasons.

Very early Macs used 32 bit UEFI, which then is an issue.

I believe all UEFI systems boot from /EFI/boot/bootx64.efi on external drive. 
Not sure how Mac boots, but have seen some posts where they recommended keeping Mac system as that was the only way to be able to update system.

Pure UEFI boot only needs FAT32 partition with boot, esp flags and the Ubuntu ISO extracted into that partition. I have used p7zip, but do not know what tools Mac may use to extract files.

I have only done this from Ubuntu, and do not typically use extracted ISO anymore. I boot ISO directly with grub's loopmount.
sudo apt-get install p7zip-full
p7zip Note no space after -o  or gzip?
7z x [ISO_NAME]  -o[DESTINATION_FOLDER]
sudo 7z x ~/ISO/impish-desktop-canary-amd64.iso -o/media/fred/EFI_SSD64

If you have 4GB of RAM or less, you may not want Ubuntu.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

I like Kubuntu which is more mid-weight but has worked on both older & newer systems for me. Seem pretty fully featured.

---

