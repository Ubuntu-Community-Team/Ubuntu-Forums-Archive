---
title: "MacBook 2,1 hangs on black screen booting Ubuntu 13.10"
date: 2014-03-30
forum: Apple Hardware Users
---

### Post by Benjamin_Krug on 2014-03-30
I'm a complete newbie to Ubuntu and Linux in general (and not particularly computer savvy, which is why I was drawn to Ubuntu), but I'm trying to eke some more life out of my old MacBook. I know similar questions have been asked in the past, but that's generally been with different hardware and/or Ubuntu versions, so I'll throw this out there as well.
First off, I have a MacBook 2,1 from 2007 running Mac OS 10.4. I've never updated any firmware that I can recall. I created a new partition using this method: [http://www.ffnn.nl/pages/articles/apple-mac-os-x/nondestructive-partitioning.php](http://www.ffnn.nl/pages/articles/apple-mac-os-x/nondestructive-partitioning.php)
 It seemed to me that I would be able to run Ubuntu 13.10 based on my specs, so I downloaded the 64 bit version and successfully installed it (as far as I can tell) to my new partition. However, when I rebooted it, I couldn't get anything other than my Mac OS to boot after that. I installed rEFIt afterwards and can now choose to boot into what should be the Ubuntu partition, but after the penguin screen shows up, all I get is a blank black screen with a blinking cursor in the upper left corner. Nothing I type will show up at that point, so I just do an emergency power down.
I know I made at least one mistake in partitioning by not leaving myself enough swap space, so my inclination is to erase the new partition and start again from scratch anyway. Am I right in this? Should I do anything else differently, or use an older version of Ubuntu?
Thanks for the help!

---

### Post by PartisanEntity on 2014-03-31
I had the exact same issue on my iMac. I was able to solve it by booting from the Ubuntu Live CD, launching gparted, and changing the flag on the bios_grub partition from "bios grub" to "boot". Then restart.

After that, in refit when I selected Linux, it showed be the usual Grub menu and allowed me to boot into Ubuntu.

---

### Post by Benjamin_Krug on 2014-03-31
I'm sorry, like I said I'm new to this, so I need a little clarification.
Does "launching parted" mean going to the partition portion of the Ubuntu installer where I created the bios grub, swap space, etc when I was doing the original install? And what do you mean by "changing the flag" on the bios-grub partition?  Changing the partition type? The only option I saw was to change it to "EFI boot partition", which makes it show up as EFI just like the regular booter for Mac OS. Is that right?

---

### Post by PartisanEntity on 2014-03-31
On the live cd, there is an application called gparted. It is a partition editor. (Has nothing to do with the Ubuntu installer)

Launch it and it will show you all the partitions that are on your hard disk.

Locate the one called "bios_grub" and right click on it. Then you will see a menu entry "manage flags" click on it.

Untick "bios_grub" and tick "boot". I am not sure now but you may have to click on "apply".

After that restart your computer and try booting Ubuntu from your hard disk.

---

### Post by Benjamin_Krug on 2014-03-31
How should that partition be formatted? Right now it has no effect because Ubuntu describes the file system as "unknown". On getting information about the file it says "warning: Unable to detect file system! Possible reasons are:
The file system is damaged
The file system is unknown to Gparted
There is no file system available (unformatted)
The device entry /Devin/sda4 is missing"
I flagged it as boot, but saw no option to apply, and it didn't indicate that an operation was pending.

---

### Post by PartisanEntity on 2014-03-31
Don't change the format, leave it as "unknown". As I said, I changed the flag from "bios_grub" to "boot" and it worked on my iMac.

---

### Post by Benjamin_Krug on 2014-04-02
Well, I ended up reinstalling Ubuntu after playing with the partitions some. I accidentally installed Ubuntu onto the same partition as Mac OS, but it works like a charm now. So as far as my needs got this is solved.

---

