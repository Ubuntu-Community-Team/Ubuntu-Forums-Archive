---
title: "Partition Space neede for Ubuntu"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-05-16
I have  windows xp running on my system at the moment and i would like to share with Ubuntu and eventually migrate to an all Ubuntu system. I have a 40 gig hard drive. Could someone suggest how best I could break up the memory. I mean partitioning. I want to use Ubuntu for surfing the net to start with. So please some kind of figure for smooth running of Ubuntu.

Thanks a lot for your time. Hats off to you ppl at the forums. This is the best forum i have ever visited, such amazin ppl..;)

---

### Post by glotz on 2006-05-16
The minimum install requires around 2.2 gigs methinks. I'd allocate at least 3 or 4 so you'll have some elbow room. Linux cannot write (reliably) to NTFS so if your XP is on NTFS, you'll probably want a FAT32 disk that both OSes can use. (Also, disk space is relatively cheap nowadays, you might want to invest in a new disk.)

---

### Post by nalmeth on 2006-05-16
hmm how big is your windows installation?
Can you back it up easily --> have a DVD-burner?
If your windows installation + media is around 20 gigs, then I'd say you're safe to just dual-boot for the moment.

Backup your important files, defrag your windows at least a couple times, and:
a. Let the ubuntu installer resize your windows and then install windows
or 
b. use your favorite partitioning tool to resize windows, and leave as much space as you can for ubuntu. Then use the ubuntu installer, and ask to install in the unused space.

Any other questions?

---

### Post by hotbrainz on 2006-05-16
thanks for the reply. I can format the entire system coz i have back ups for everything. So wat would u ideally suggest the partitioning can be like. I have abt 20 gig data which i would ideally like to be acessible by both OSes

---

### Post by nalmeth on 2006-05-16
That's good news.

I would recommend erasing the whole disk, then partitioning 20 gig's as FAT32, and 20 gig's as EXT 3.
You can use a free partitioner like the [Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php")
You have to create the fat32 partition first, because by default windows will *only *install to NTFS. If there is FAT32 available it can install to that however.
This way, you can read/write from Ubuntu to your Windows, and using something like [this]("http://uranus.it.swin.edu.au/%7Ejn/linux/ext2ifs.htm"), you can read/write to your Ubuntu from Windows as well.

Alternatively, If you prefer to have a data/media share partition (it seems you might), you can just install windows normally, tell it to stay around 10-15 gigs, install ubuntu, keep it to 10-15 gigs, and create a fat32 partition for Data to share between the two.
Just remember if you want to be able to write 'safely' to your windows from ubuntu, it *needs* to be fat32.

You can still set all this up with Gparted, just remember the names of the partition's created. For second method, I'd go fat32 (windows), ext3 (ubuntu), fat32 (data)

---

### Post by hotbrainz on 2006-05-16
thats great news!

Thanks again for the help. Cant wait to do it...

---

