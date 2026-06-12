---
title: "ubuntu on a partition"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by JTJackson on 2007-08-29
I am trying to install ubuntu on a partition of hd.  I am running windows XP right now.  Using Partition Magic i created a partition for linux, one solely for data and a last one to run BootMagic with(Since it requires a FAT or FAT32 partition).  I have downloaded Ubuntu and burned it to a CD.  From here i have no clue what to do.  I am not even sure if what i have done so far is right either.

---

### Post by Seti on 2007-08-29
How big is this partition? 
At this point all you need to do is run the ubuntu live CD. You should probably make a swap partition as well, this only needs about 6 or 7 hundred MGB.

---

### Post by JTJackson on 2007-08-29
My linux one is 50GB, the data one is 10GB, the one for bootmagic is 100MB, and the one for windows is about 150GB.  when i ran the CD it opened a window but i didn't see anything for installing it.

---

### Post by kellemes on 2007-08-29
OK, keep it simple..
Don´t use Bootmagic.. get rid of it, simply leave 60 Gb unformatted. You can do this from Part. magic.
Startup Ubuntu-livecd and use the partitioner from the installer to create..
- swappartion of 2x size of your ram (with a maximum of 2Gb)
- 10 Gb ext3-formatted mounted at /
- 20 Gb ext3-formatted mounted at /home
- 30 Gb fat32-formatted mounted at /media/share (or whatever you want)

This last sharedisk may be formatted ext3 also, then you do need to install some ext3-driver on Windows to access it. I actually prefer it.

Does this help?

Edit: These sizes may vary obviously..

---

### Post by Seti on 2007-08-29
For starters, you don't need a partition for 'Bootmagic'; you don't need this at all. ubuntu will install grub bootloader to your MBR (or to a floppy if you prefer), so get rid of it.
As long as Windows is the first partition on your disc, you'll be fine. Under the application menu you will find something called 'Gnome Partition Editor' Use that to partition your disc after the 1st primary partition. Then click the 'Install' Icon on the Desktop for the actual installation.
Good Luck!!

---

### Post by JTJackson on 2007-08-29
so i just need uninstall bootmagic, right?

Then do i use Part.mag to take all the partitions i have and get rid of them?  Or do you mean turn the partitions i have now into a single partition?

could you explaing the partitioning with the livecd?  I am not sure i understand what the different types are or what ext3 means (extension?).  also, does the livecd show this process/how does it get me through that section of it?

---

### Post by kellemes on 2007-08-29
> **JTJackson said:**
> so i just need uninstall bootmagic, right?

Then do i use Part.mag to take all the partitions i have and get rid of them?  Or do you mean turn the partitions i have now into a single partition?

could you explaing the partitioning with the livecd?  I am not sure i understand what the different types are or what ext3 means (extension?).  also, does the livecd show this process/how does it get me through that section of it?

The space you want to use for Linux you can simply delete/unformat, so delete all the partitions in it from Part.Magic. So when you startup the Ubuntu-installer you need to creating all the partitions for Linux.
There are some filesystem-formats you can choose for GNU/Linux and ext3 is one of them.
Like I said.. keep it simple, when you choose ext3 all the way, you'll be fine.
The partitioner is very easy indeed and will have some docs available I'm sure.

Edit: Yes, get rid of bootmagic.. Ubuntu will use it's own bootloader to load itself **and** Windows.

---

### Post by JTJackson on 2007-08-29
oki thanks for the help, i cant do this now since i am busy, but i will try it when i can, and then  report my success or failure(though hopefully success).

Thanks for now

---

