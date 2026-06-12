---
title: "EEEPC 701 Fails to boot"
date: 2011-07-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Tylerjd on 2011-07-26
I know this isn't the preferable place to put this, it would be better in the ASUS forums, but I have a higher rank here and I would be a n00bie there. 

Here is my problem: I have a 2-3 year old ASUS EEEPC 701 4Gb and it has been working fine for all of that time. I went on a 4 day trip without it, with it plugged into a surge protector, and I come back from the trip, turn it on, POST test is fine, and then goes to a blank screen with a blinking cursor & no drive activity. I had UNR (Ubuntu Netbook Remix) on it (GRUB2, ext4 format, Ubuntu 10.04). I have tried many things to get it to go further (Restore BIOS to original settings, plug it into an external monitor, re-install UNR, and try installing other Linux distros.) 

When I boot a distro such as Ubuntu 10.04 Alternate Install, it will goto the purple screen where I choose what to do, I choose an option such as install, the external CDROM drive spins up for a few seconds, then stops and I get the blank screen with cursor again. The same thing happens with a SD card or USB stick. When I do a verbose boot, I seem to recall that the message it stops on is when it loads initrd but I could be wrong. 

Then I went and tried Windows XP *shudder*. It will ask to press a key to continue, then format the drive, then it will copy the required files over, then on reboot, POST will of course go by, then I get the blinking cursor again. I checked the RAM to make sure it was still seated, its all good, and the SSD chips (mounted on-board) are still good. 

Any remedies or comments are greatly appreciated. Thanks.

---

### Post by Plumtreed on 2011-07-27
Have you tried to boot via a usbdrive? You will probably get a similar result as a boot from a CD but it might also tell you if the internal SSD is borked.

---

### Post by GHerzog on 2011-07-29
At some point, the EEEPC 701-4G begins to suffer from old age. Is it not charging properly? Initially I thought I had a Ubuntu bug, so I reinstalled Xandros Linux (which it came with). It would refuse to boot and refuse to charge. So I thought it was the battery - which a replaced and did not succeed in resolving.

Since I live in Taiwan, a friend took it into the Asus repair center and they sold him a new wall wart. They claimed that was the problem, but I really wonder.

I had already given up and purchased a Toshiba NB250, so I gave him the EEEpc, which he loves and he has had no trouble with it.

---

