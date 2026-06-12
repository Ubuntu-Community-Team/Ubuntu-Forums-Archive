---
title: "Install/Boot Ubuntu from External HD?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by weasler7 on 2007-12-03
Is this possible? How would I do such a thing?

Thanks:(:)

---

### Post by cotcot on 2007-12-03
[[COLOR="Red"]Here[/COLOR]]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") is a howto for it.

---

### Post by speed145a on 2007-12-03
I am assuming you are talking about installing on a single machine as you would on an internal disk.  this should be possible.  you will need your bios to support booting from usb or "removable" devices.  

all you should need to do is have the drive plugged in when you boot from the live cd, then select the external as the partition to format and install to

----> if you care about your existing system then don't try this without knowing what you are doing!  I have not tried this and do not know what impact it will have on your  existing boot configuration!

---

### Post by 449 on 2007-12-03
Do you plan on installing on a partition or just using the whole drive? Because I had so many issues with installing on a separate partition that I just quit and formatted the whole thing. I even tried Super Grub, but with no success. And if you do have partitions it should work on the first one ,but I don't know about the other ones. Easiest thing to do?

**Make sure you're BIOS supports usb boot and then format the whole drive**

Although if you want to try to get it working on a different partition be my guest. :)

---

### Post by louieb on 2007-12-03
A word of caution. If you plan on unplugging the external drive -  you cannot use the standard install method. 
Your internal drive has an MBR - the external has one too.
The standard method replaces the internal drives MBR with a pointer to GRUB.
What that means is if the external is unplugged and you reboot - the computer will give you a GRUB error and won't boot. 
So read the instructions cotcot gave you carefully and make sure you install the GRUB pointer on the MBR of the external.

---

### Post by rosetown on 2007-12-03
To get good advice please provide :

1) details of your hardware
2) what OSs you are presently running
3) what plans (however vague) you have in mind

The above aside - it is possible to boot Ubuntu from an external drive ( I assume USB)?
If you fill in the blanks the replies will be more specific.

Regards Duane

---

