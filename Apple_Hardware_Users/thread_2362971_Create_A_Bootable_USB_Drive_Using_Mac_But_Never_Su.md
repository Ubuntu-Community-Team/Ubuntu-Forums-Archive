---
title: "Create A Bootable USB Drive Using Mac But Never Succeeded"
date: 2017-06-04
forum: Apple Hardware Users
---

### Post by EDLIU on 2017-06-04
Hi,

I'm trying to create a bootable USB devise from a Mac.

I followed the steps in "How to install Ubuntu on MacBook using USB Stick(Manual Approach)".

The commands worked fine **until the last "sudo dd if=/path/to/downloaded.img of=/dev/diskN bs=1m"**.

The .img file never finishes uploading to the USB Stick.

It took hours and I had to unplug the USB Stick.

So, what went wrong?

Besides, anyone knows that "How much time does it normally take to create a bootable USB drive?

Thanks in advance.

Ed

---

### Post by howefield on 2017-06-04
> **EDLIU said:**
> Besides, anyone knows that "How much time does it normally take to create a bootable USB drive?

Can't answer the first question but just for info and seeing as I have just dd'ed todays Artful daily on a slow USB stick using a USB2 port, it took 

```
sudo dd if=artful-desktop-amd64.iso of=/dev/sdb bs=4M; sync
369+1 records in
369+1 records out
1549615104 bytes (1.5 GB, 1.4 GiB) copied, 344.813 s, 4.5 MB/s
```

5 minutes and 45 seconds. Different hardware will perform better or worse but certainly shouldn't be hours...

---

### Post by monkeybrain20122 on 2017-06-04
I think the Mac version of Unetbootin lets you create a Ubuntu live usb on a Mac.

---

### Post by EDLIU on 2017-06-04
Hi,

Does my USB stick is an old 2.0 USB stick matter?

Besides, should I try "[COLOR=#333333][FONT=Ubuntu]Using [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]/dev/rdisk[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] instead of [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]/dev/disk since it[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] may be faster"?

What's the difference between "[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]/dev/rdisk" and "[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]/dev/disk"?

If I use "[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]dev/rdisk", should I enter **"**[/FONT][/COLOR]**[COLOR=#333333][FONT=Ubuntu]dev/rdisk or [/FONT][/COLOR]**[COLOR=#333333][FONT=Ubuntu]**dev/rdiskN**" (N[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] the device node assigned to the flash media[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]) at the command line?

Thanks.

Ed[/FONT][/COLOR]

---

### Post by yancek on 2017-06-04
You could read through the page below which explains the process of identifying the drive/partition on a Mac.  Never used one so can't test it.

[http://osxdaily.com/2015/06/05/copy-iso-to-usb-drive-mac-os-x-command/](http://osxdaily.com/2015/06/05/copy-iso-to-usb-drive-mac-os-x-command/)

---

### Post by HermanAB on 2017-06-04
See this:
[http://www.aeronetworks.ca/2013/05/using-dd-on-mac-to-copy-iso-file.html](http://www.aeronetworks.ca/2013/05/using-dd-on-mac-to-copy-iso-file.html)

It would take about 5 minutes.

Note that I'm assuming that there is only ONE disk in your Mac, so the USB will be /dev/disk2.  You better check that...

---

### Post by oldfred on 2017-06-04
Another I have seen, but do not know for sure works as I do not have a Mac.

[https://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](https://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)

This might work also.
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by howefield on 2017-06-05
And moved to the "*Apple Hardware Users*" forum.

---

### Post by EDLIU on 2017-06-05
Hi,

If you want to "Create A Bootable Ubuntu USB Drive For Mac In OS X". Read the following article.

How to install Ubuntu on MacBook using USB Stick([https://help.ubuntu.com/community/Ho...113.1482443622](https://help.ubuntu.com/community/Ho...113.1482443622))

If you have the same problem while creating a Ubuntu Bootable USB Drive following the step by step instructions in the article.

Try use the command: "**sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m**"
(Use /dev/rdiskN instead of /dev/diskN)

But there's still one problem. After creating a bootable USB drive, a message: "error, files not found" showed when I tried to boot the Mac using the USB stick. I was able to see the "Try, Install, ..." menu though.

Thanks.

Ed

---

### Post by EDLIU on 2017-06-20
My Bootable Ubuntu USB Drive still have problems. Anyone can help me with it?

Thanks.

Ed

---

