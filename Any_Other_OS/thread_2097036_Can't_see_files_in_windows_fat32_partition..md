---
title: "Can't see files in windows fat32 partition."
date: 2012-12-21
forum: Any Other OS
---

### Post by Buruk on 2012-12-21
I have a logical partition that has been formated in windows vista. I've put some documents on the partition in windows but can't see them in linux mint 14. The partition is mounted, but when I click on it to view files nothing shows up.

---

### Post by lisati on 2012-12-24
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by Karlchen on 2012-12-24
Hello, buruk.
 
 
> I've put some documents on the partition Which kind of documents? Are they Word dcouments? Are they JPEG pictures? What are they?
I assume the files can be opend in Windows by double clicking their filenames in Explorer. Which programmes will Windows launch when you do so?
 
 
What I am after is finding out whether the problem on Linux Mint may really be that so far no programme has been assigned the the task of opening the relevant document types.
 
 
> The partition is mounted, but when I click on it to view files nothing shows up. Can you post a screenshot which illustrates what "nothing" means in detail, please. 
If you click on the partition something must happen. In the worst case you will get an error message.
 
 
Kind regards,
Karl
--
P.S.:
Basically Linux Mint can handle FAT32 partitions quite well. I use this ability all the time when reading from and writing to my USB pendrives.

---

### Post by Buruk on 2012-12-25
I just changed the partition to ntfs and used the support for that (ntfs-3g, already installed in linux mint). It works now, and with a newer file system as  a plus. 

The files are word documents and some jpegs.

When I said nothing I meant when I would go to the linux equivalent of windows explorer or windows file manager (I'm not sure what it's called) to click on the directory the page was blank, no files or directories listed even though I knew they were there. I'm not sure how to post a screen shot.

I'm guessing the partition never got mounted correctly in fat32 even though they appeared to mount fine. 
sudo mkdir /mnt/Sdoc
sudo mount -t vfat  /dev/sda11 /mnt/Sdoc went fine, but I still couldn't see anything.

I'm just glad it's working now with ntfs, though it's strange why it didn't work in fat32.

---

