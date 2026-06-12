---
title: "New Install won't boot &quot;Input/output error&quot;"
date: 2011-01-22
forum: Apple Hardware Users
---

### Post by DaleH on 2011-01-22
I finished loading Ubuntu 10.10 onto my Mac PPC G4 from DVD and restarted.

Restart but will not proceed beyond black screen with alert:

boot:
Please wait, loading kernal...
/pci@f2000000/pci-bridge@d/mac-io@7/ata-4@1f000/disk@:3,/boot/vmlinux: Input/output error
boot:_

Tried rebooting with "Option" key and choosing Linux, but no difference.

I am trying this on a Mac G4 with Ubuntu 10.10 installed on its own drive.
There is another drive with Mac OSX 10.2.8.

---

### Post by BlastXng on 2011-01-23
> **DaleH said:**
> I finished loading Ubuntu 10.10 onto my Mac PPC G4 from DVD and restarted.

Restart but will not proceed beyond black screen with alert:

boot:
Please wait, loading kernal...
/pci@f2000000/pci-bridge@d/mac-io@7/ata-4@1f000/disk@:3,/boot/vmlinux: Input/output error
boot:_

Tried rebooting with "Option" key and choosing Linux, but no difference.

I am trying this on a Mac G4 with Ubuntu 10.10 installed on its own drive.
There is another drive with Mac OSX 10.2.8.

Did you do this from using the LiveCD? 

If so, then I'd suggest the alternate which is what I had to use do to some X issues I ran into with Xserver..

---

### Post by DaleH on 2011-01-24
What ever the problem was initially, I reinstalled and it went away. Everything seems fine.

---

