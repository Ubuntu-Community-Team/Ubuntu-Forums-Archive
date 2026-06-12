---
title: "External HDD won't start plz help!"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by infernus_crusher on 2008-03-25
Ok last time I remembered, I shut Ubuntu down without unmounting the HDD properly. And then I put it on Vista and I went to Device Manager, and it says "Device won't start". I've uninstalled and reinstalled the device, rebooted, everything whatsoever but it won't work.

I went to Hardware Info and checked the device and apparently there's this property of the HDD called usb.can_wake_up set to "false", in contrast to my USB mouse's, which is set to "true".

Is that what caused the HD not to start? How can I change it?

---

### Post by bumanie on 2008-03-25
Is your external drive a seagate free agent by any chance? If so they don't seem to be compatible with ubuntu/linux due to sleep/wake mode. The only work around I've heard of is running them via an e-sata port. Then they work apparently.

---

