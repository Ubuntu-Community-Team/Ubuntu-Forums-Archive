---
title: "usb/thunb drive info?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by loucks357 on 2007-09-28
I am new to this so please excuse newbie q's..I am having trouble using my usb drives w/ ubuntu...Any tips ? Thanks in advance..( and I am a bit older than many of you ( I am guessing) but very young in using this application..so please  be patient!

---

### Post by master_kernel on 2007-09-28
What specifically is wrong?

---

### Post by bruce89 on 2007-09-28
[LIST=1]
[*]What kind of problems?
[*]What happens when you insert the stick?
[*]What is the output of ```
tail -f /var/log/messages
```
[/LIST]

Do the above command before inserting the USB drive, post the output.

---

### Post by loucks357 on 2007-09-28
Thanks for your quick reply..Nothing at all happens when I plug in usb..I did the code and still nothing..I may have entered code in wrong command line?

---

### Post by loucks357 on 2007-09-28
okay..did it again..


 Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep 28 20:33:10 rich-desktop gconfd (root-9295): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Sep 28 20:33:10 rich-desktop gconfd (root-9295): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep 28 20:33:10 rich-desktop gconfd (root-9295): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep 28 20:33:10 rich-desktop gconfd (root-9295): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep 28 20:33:40 rich-desktop gconfd (root-9295): GConf server is not in use, shutting down.
Sep 28 20:33:40 rich-desktop gconfd (root-9295): Exiting
Sep 28 20:37:02 rich-desktop kernel: [ 7514.058621] usb 3-5: new high speed USB device using ehci_hcd and address 38
Sep 28 20:37:03 rich-desktop kernel: [ 7514.602402] usb 3-5: new high speed USB device using ehci_hcd and address 39
Sep 28 20:37:03 rich-desktop kernel: [ 7515.146189] usb 3-5: new high speed USB device using ehci_hcd and address 40
Sep 28 20:37:04 rich-desktop kernel: [ 7515.665990] usb 3-5: new high speed USB device using ehci_hcd and address 41



so, what does all this mean? Thanks!

---

