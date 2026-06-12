---
title: "Old USB1 External Drive"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by yustr on 2006-08-25
I have an old external drive housing that is vintage = USB1. I have a new Seagate 120G HD in it and would like access it. I think its FAT32 but it might be NTFS. When I hook it up I don't see any indication that my comp sees it. When I plug in a usb stick I get an icon on my desktop.

Is there a way to check?

Thanks

---

### Post by amo-ej1 on 2006-08-25
take a look at the output of the 'dmesg' command, which displays your kernel messages. You should see the usb device popping up there and seeing it try to read the partition table and see it having a device number assigned (or see it fail)

---

### Post by yustr on 2006-08-26
Thanks for the quick response.

The device shows up as: uhci_hcd address 2

It is formatted as NTFS. So can I just make a dir for it and mount hcd with the ntsf stuff added (I 'm pretty sure I know what that is...) DO I need to call it hcd? hcd1? hcd2?

Thanks again.

---

