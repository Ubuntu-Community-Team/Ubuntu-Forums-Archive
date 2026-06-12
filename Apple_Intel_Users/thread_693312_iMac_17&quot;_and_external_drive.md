---
title: "iMac 17&quot; and external drive"
date: 2008-02-10
forum: Apple Intel Users
---

### Post by BoyGenius on 2008-02-10
I'd like to install ubuntu on a partition of an external hard drive to then dual boot with OS X.  I have a 17" Intel iMac and a 500g external usb hd.  Is this possible?  If so, are there any tutorials around?  I've searched but couldn't find anything.

BTW: I've tried booting from the livecd (7.04 and 7.10) but I can't.  The monitor keeps going  black-then-text, until on the 6th time it gives me an error message.

Thanks in advance... 
/bg

---

### Post by cyberdork33 on 2008-02-10
Check the FAQ about the external drive thing. It is likely a no-go. Blame Apple.


The LiveCD is not that big of a deal. Xorg is not starting, likely because the driver on the CD is not compatible with you Mac. You can download the Alt install cd and install with that, then you can get the needed drivers to run your video properly. Which graphics card do you have in your iMac? The ATI? Have you tried booting in safe graphics mode?

---

### Post by BoyGenius on 2008-02-10
I actually did download the alt cd and started installing with it, but then I got a little worried.  I had no idea where the alt CD was putting all those files it was copying.  Was it overwriting my OS X?  I stopped it and ran away very quickly.  I'll try in safe graphics mode.  As for graphics card, I believe it's this: ATI Radeon X1600

---

### Post by cyberdork33 on 2008-02-10
> **BoyGenius said:**
> I actually did download the alt cd and started installing with it, but then I got a little worried.  I had no idea where the alt CD was putting all those files it was copying.  Was it overwriting my OS X?  I stopped it and ran away very quickly.  I'll try in safe graphics mode.  As for graphics card, I believe it's this: ATI Radeon X1600
safe-graphics mode ought to get it up.

You should partition before you install with bootcamp or gparted. It wouldn't be installing anything other than to memory unless you had made it to the partitioner already and told it to partition the drive.

---

