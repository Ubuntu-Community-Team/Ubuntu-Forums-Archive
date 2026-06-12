---
title: "Installed grub by accident -- now my Mac drive wont boot!"
date: 2010-01-18
forum: Apple Hardware Users
---

### Post by rlinsurf on 2010-01-18
I was trying to install 9.10 on a volume already partitioned using Bootcamp 3.0 in 10.6.2 for windows. I was told to enter into the ubuntu installer, choose the fat32 partition, delete it, make a new partition from the free space just created of 600MB for a swap partition, and one ext3 partition using "/" for the remaining free space.

I did. Then I proceeded with the install. However, when I tried to reboot, it would neither boot into ubuntu, even with option held down, or into my normal startup Mac drive :(

I wrote to the apple discussions, and they said I had installed grub onto the startup volume, not the one I had specified, and that I should have gone under Advanced to specify where to install grub.

Ok, no harm no foul. Except that even after deleting the efi folder from the startup drive, it still wouldn't boot. So then I did a quick erase on the drive using Disk Utility, and cloned my backup of the startup drive back to it. It still doesn't boot.

So now I'm stuck. How do I get grub off this drive? Please help.

---

### Post by rlinsurf on 2010-01-19
Hello? Is there anyone here?

---

### Post by linuxopjemac on 2010-01-19
Can't you do a repair from the OSX installation CD ?

---

### Post by rlinsurf on 2010-01-19
I just got a reply at the Apple site. Here it is:

"Is the clone on an external HD ?

If so, boot from it and use Disk Utility to not only erase but repartition your internal HD.
Make sure that the 'Option' is set to use GPT as partition scheme.
Might be needed, to first repartition to two partitions and after that's done once again repartition to one partition.
Then clone back the OSX clone to your internal HD."

It's not an ext. drive, and I haven't actually tried this as yet. That being said, this sort of thing really should be built into the partitioner. The installer should assume that the volume selected to be partitioned, is also the one to install grub onto, rather than defaulting to hd0,0, IMHO.

---

### Post by linuxopjemac on 2010-01-19
if you have two drives built in, you should start from an OSX CD I think and to then try to repair something. Then try to boot from the OSX drive.

---

### Post by linuxopjemac on 2010-01-19
[http://mewcetti.com/2009/07/11/remove-grub-from-a-mac-under-osx/](http://mewcetti.com/2009/07/11/remove-grub-from-a-mac-under-osx/)

---

### Post by rlinsurf on 2010-01-19
Damn! I already partitioned the drive. Wish I'd known that before.

Great article. Thanks :)

(But please any dev's here, consider my suggestion) :)

---

### Post by linuxopjemac on 2010-01-19
May it ever happen again, I made a copy of that article in my own forum. It's easier to have all information at one place I always think:

[http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot](http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot)

---

### Post by rlinsurf on 2010-01-19
As I haven't tested it, I don't know, but it would seem that it's incorrect to say that command would only work if you only have one HD. It should work no matter how many you have, as long as they're not in an array of some sort.

<shrug>

---

