---
title: "using micro sd as part of filesystem"
date: 2012-08-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jessel on 2012-08-11
Is it a reasonable thing to add a line to the fstab and mount a micro sd card as part of the filesystem? What partitions would I put on the micro sd? 

i have an asus x101, with an 8bg ssd drive.

with ubuntu installed its only a matter of time before updates fill up all the drive space.

i have a 16 gb micro sd card, that never gets used, as any temporary file transfer happens using a usb flash drive...

any suggestions would be appreciated, thanks.

---

### Post by jessel on 2012-08-12
i formatted the 16gb sd card ext4 and moved the /home partition to it.

this is how [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

next i resized the / partition to be the full 8gb, and eliminated the swap partition (also deleting the line in the fstab file). note that i upgraded the memory to 2gb.

so far its working, no crashes. i am concerned that the regular updates are going to fill up the 8gb ssd. i gave myself 25% more disk space so perhaps this was enough.

---

### Post by oldfred on 2012-08-12
Even though flash is not a SSD, the settings should be similar.

With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

You normally want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD&#8217;s, Journaling, and noatime/relatime 
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

SSD Example mounting line:
UUID=41b6b187-be76-4447-b18b-d39cc744b184 /               ext4    noatime,discard,errors=remount-ro 0       1

---

