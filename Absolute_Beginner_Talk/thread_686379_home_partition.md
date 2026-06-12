---
title: "/home partition"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by bossa on 2008-02-03
Hi All

I want to create a /home partition on a 80 GB hard drive that already has Ubuntu installed.What would be the ideal size?. I am dual booting with Vista on a second 250 GB hard drive . Vista has 50 GB and the rest I have as FAT 32.Would it be better to just back up everything to the FAT partition?
Thanks Steve

---

### Post by njparton on 2008-02-03
You could use gparted to free up 20 - 30 Gb on your 80 Gb drive and create a /home partition there.

You would then need to mount it via fstab at startup.

I would stay away from backing up to a FAT partition.

---

### Post by bossa on 2008-02-03
Hi njparton 
Thanks , why would you stay away from backing up to a FAT partition? I created it on the advice from another thread so that Vista see it.

---

### Post by bossa on 2008-02-03
Could I just make an EXT3 on the vista drive then? (to store extra data)

---

### Post by jaytek13 on 2008-02-03
You could use ext3, yes. That would be fine. But what is this advice that you got about using fat32?

---

### Post by bossa on 2008-02-03
Hi jaytek13

Yeah , just that I could have Vista on a second disc create a partion on that disc (Fat32) to put extra data etc Make that partition Fat32 so that Windows and Ubuntu could use the partition.Thats what I have done . I saw another thread that said, if you have the space ie another disc just backup your stuff on there and dont bother creating another /home on the first disc. Would be nice if windows could see the backed up data too.

---

### Post by jaytek13 on 2008-02-03
> **bossa said:**
> Hi jaytek13

Yeah , just that I could have Vista on a second disc create a partion on that disc (Fat32) to put extra data etc Make that partition Fat32 so that Windows and Ubuntu could use the partition.Thats what I have done . I saw another thread that said, if you have the space ie another disc just backup your stuff on there and dont bother creating another /home on the first disc. Would be nice if windows could see the backed up data too.

Well technically, if I understand what you're saying, you could have just used NTFS and then both Ubuntu and Vista could use the partition in question. 

But you are right, if you use ext3 Windows will not be able to see it. There are some windows programs that would allow you to read a ext3 drive from windows, but you wouldn't be able to write to it.

---

### Post by njparton on 2008-02-03
FAT or NTFS aren't linux native so I would be wary about backing things up to partitions formatted with these filesystems.

I believe there are windows programs out there that allow writing to ext2, check them out.

---

### Post by bossa on 2008-02-03
Thanks guys 
I will do a bit more research on the EXT2 option ;)

---

