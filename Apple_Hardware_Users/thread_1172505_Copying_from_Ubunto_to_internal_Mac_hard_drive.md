---
title: "Copying from Ubunto to internal Mac hard drive"
date: 2009-05-28
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-28
My apologies if this is in a FAQ or something - I know I have seen this problem but I can't figure out where and so far my search strings have not been the right ones. I have a G4 PPC (Sawtooth) with Jaunty installed as well as OS 10.3.9. From Jaunty I can see the Mac partitions and copy data from them just fine but I can't do it in the other direction because of permissions (I guess that's the problem, anyway). I just had some 450 megs of pictures which I had grabbed using my card reader and Ubuntu (worked great - much better than with the Mac OS, interestingly - actually, that's why I tried doing it from the linux side in the first place) but I needed to get the data onto the Mac. For some reason, this Mac freezes with large amounts of data from a flash drive even though the Ubuntu side does not, so that was out. I ended up burning it to a CD with Brasero and copying it off of that but it sure would have been a lot easier to just copy it directly to one of the Mac partitions.

What is the solution to this?

Thanks!

Edit: Ack, I can't edit the title to fix "Ubuntu". !?

---

### Post by tiresia on 2009-05-28
You can't copy files to the MacOSX Partition, because most probably MacOSX uses HFS+ Journaled. Which is correct, but while Linux support reading HFS+ Journaled, does not support writing on it.
If you want to be able to write to a HFS+ Partition, you should disable Journaling, and you can do it only from MacOSX. You can disable Journaling in MacOSX using the Apple Disk Utility or open a Terminal and run```
sudo diskutil disableJournal name_of_the_disk 
``` 
where name_of_the_disk can be "/" if you want to disable journaling where MacOSX is running or something like /Volumes/myDisk for another partition 

Anyway is not a good idea to disable journaling. If you want to be able to permanently exchange file between MacOSX and Ubuntu, you should create a third 'share' partition, formatted as FAT32 (both System can read it - but as a 4GB limitation per file) or with HFS+ (NOT Journaled)

---

### Post by Benboom on 2009-05-28
Ah, I understand. Thanks for that information; I think the best thing will be a shared partition of the kind you mention. That doesn't sound too onerous.

---

### Post by Benboom on 2009-05-29
I got it working now. The partition was already unjournaled. I needed to run Nautilus as root user, that's all.

However, my normal file browser is thunar and I can't seem to figure out how to do that in thunar. When I run gksudo thunar it pops up with a warning (Warning: you are using the root account, etc.) which I can disregard but it still won't let me copy files to the mac side; I seem to be able to do that only from within Nautilus.

---

