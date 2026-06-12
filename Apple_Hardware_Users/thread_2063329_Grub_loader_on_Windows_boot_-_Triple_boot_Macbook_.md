---
title: "Grub loader on Windows boot - Triple boot Macbook 9,1"
date: 2012-09-26
forum: Apple Hardware Users
---

### Post by Fi5hy on 2012-09-26
Hey all, I've had my triple boot working for a while, but every time I booted up Windows, it's given me the Grub loader first. This hasn't bothered me until this week. I started a programming (C++) class, and to simplify things, I installed VMWare Fusion. Apparently, from what I can tell, Grub loader prevents VMWare from booting into my Windows partition, so I would like fix this Grub loader issue.

I read something about a hybrid MBR fix somewhere, would someone like to clarify?

---

### Post by Fi5hy on 2012-10-09
Bump.

---

### Post by Fi5hy on 2012-10-10
Bump; again.

---

### Post by Fi5hy on 2012-10-16
I really need some help on this still, guys...

---

### Post by Fi5hy on 2012-11-23
Bump

---

### Post by trogdor1138 on 2012-12-05
Do you still need help with this?

You have a couple of options; it really depends on whether Ubuntu is currently installed in EFI mode or BIOS emulation.

Basically, when you install Windows and then later Ubuntu, GRUB overwrites the MBR boot code. It's relatively simple to replace GRUB with the Windows boot loader, but simply doing this renders Ubuntu unbootable. If you installed Ubuntu in BIOS emulation, you'll need to:

- Boot into Ubuntu natively
- Use DD to copy the MBR boot code to a binary
- Boot Windows natively through GRUB
- Re-install the Windows boot loader
- Use BCDedit to chain-load the GRUB binary file

I'm guessing this is the case, since if you installed Ubuntu in EFI mode it wouldn't have any need to overwrite the MBR boot code.

Also, if you do indeed need to fix the hybrid MBR, you're going to need gdisk: [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

gdisk is used from OS X, and you can then select which GPT partitions to add to the MBR, and which to set as active.

---

### Post by Fi5hy on 2012-12-13
> **trogdor1138 said:**
> Do you still need help with this?

You have a couple of options; it really depends on whether Ubuntu is currently installed in EFI mode or BIOS emulation.

Basically, when you install Windows and then later Ubuntu, GRUB overwrites the MBR boot code. It's relatively simple to replace GRUB with the Windows boot loader, but simply doing this renders Ubuntu unbootable. If you installed Ubuntu in BIOS emulation, you'll need to:

- Boot into Ubuntu natively
- Use DD to copy the MBR boot code to a binary
- Boot Windows natively through GRUB
- Re-install the Windows boot loader
- Use BCDedit to chain-load the GRUB binary file

I'm guessing this is the case, since if you installed Ubuntu in EFI mode it wouldn't have any need to overwrite the MBR boot code.

Also, if you do indeed need to fix the hybrid MBR, you're going to need gdisk: [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

gdisk is used from OS X, and you can then select which GPT partitions to add to the MBR, and which to set as active.
Could you explain a bit more? I don't understand what it is I need to do. If you could post a link to a tutorial, that would be great. :) I just don't want to mess anything up.

---

### Post by trogdor1138 on 2012-12-15
Sure, check out this TechNet post on how to get the GRUB code into a file: [http://blogs.technet.com/b/port25/archive/2006/10/13/http-port25-technet-com-archive-2006-10-12-windows-and-linux-integration-3a00-a-conversation-with-the-author-aspx.aspx](http://blogs.technet.com/b/port25/archive/2006/10/13/http-port25-technet-com-archive-2006-10-12-windows-and-linux-integration-3a00-a-conversation-with-the-author-aspx.aspx)

If you need help using gdisk to correct the hybrid MBR information, check out the appropriate article on Rod Smith's site: [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

