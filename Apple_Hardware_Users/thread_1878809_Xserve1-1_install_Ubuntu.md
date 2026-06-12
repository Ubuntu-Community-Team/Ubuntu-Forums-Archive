---
title: "Xserve1-1 install Ubuntu?"
date: 2011-11-10
forum: Apple Hardware Users
---

### Post by urthmover on 2011-11-10
I have been blessed with the task of installing Ubuntu Server on a few apple xserve machines.  I have successfully installed 11.04 on xserve3-1, since it was able to boot directly from the 11.04 cd.

Unfortunately, the xserve1-1 is a different story.  That system does not boot from the cd.  I noticed that the cd does not have bootia32.efi but does have bootx64.efi.  From my googling and running some commands on the xserve1-1 I think that it only has a 32bit version of EFI.

I have attempted to compile my own grub2-1.99 with no success.

I have created a usb key that uses grub 1.96 to boot net installs, but those do not properly copy the boot information to the local hard drive.

Can someone help point me at how best to install 11.04 on an xserve1-1?

Thanks for any assistance that you share.

---

