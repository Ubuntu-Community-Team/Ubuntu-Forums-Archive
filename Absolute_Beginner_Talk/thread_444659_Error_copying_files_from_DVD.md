---
title: "Error copying files from DVD"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by anandham on 2007-05-15
Hi All,
   I have burned a DVD with some image files & some media files with proper extensions & improper extensions(just renamed into something random like ".ard").  Now when I try to copy from this DVD I'm getting I/O error while copying the media files from DVD to the destination. I'm not able to copy them in windows also. Same error is occuring in windows too. The image files are getting copied but not the media files.

The other method I have tried is writing the DVD content into an ISO image. Even that didn't work. Only part of the media files are copied not all of them.

I have done a wide search but so far haven't found any favourable answer. It would be of great help if someone can help me with this.

Thanks
anandham

---

### Post by starcraft.man on 2007-05-15
> **anandham said:**
> Hi All,
   I have burned a DVD with some image files & some media files with proper extensions & improper extensions(just renamed into something random like ".ard").  Now when I try to copy from this DVD I'm getting I/O error while copying the media files from DVD to the destination. I'm not able to copy them in windows also. Same error is occuring in windows too. The image files are getting copied but not the media files.

The other method I have tried is writing the DVD content into an ISO image. Even that didn't work. Only part of the media files are copied not all of them.

I have done a wide search but so far haven't found any favourable answer. It would be of great help if someone can help me with this.

Thanks
anandham

Are you always getting trouble when reading material made from the same DVD burner? Maybe its on the fritz, an easy test is to make a DVD iso and then burn it using another burner, if it works then your burner is bad. I don't see any reason why burning data would be unreadable, I do it all the time. Oh and use K3b for your burning, its very good. Post back how that goes.

---

### Post by anandham on 2007-05-16
Hi,
   I'm able to copy the non media files such as Docs & images without any issues. That doesn't mean that my DVD is getting read. Only the media files are not getting copied that to few. Anyways I'll try installing k3b & try the iso method.

thanks
anandham

---

### Post by shimrah on 2007-06-11
I'm having the same problem, trying to copy files from a CD ROM.

I can list the CD contents. The files copy fine if I use XP. But if I try to copy the files to my Desktop in 7.04 I get an I/O error.

Any thoughts?

---

### Post by ticopelp on 2007-09-08
Same problem here as well. I was just about to make a new thread about it. 

I get the same issues from freshly burned DVDs and ones that are several months old. 

Does anyone have any ideas?

---

### Post by circuitsurfer on 2007-09-15
Hello All;

I am having the same or a similar problem. I am using 7.04 I burned the DVD's with Gnomebaker, received no errors, I am able to watch the video files fine from the DVD, but when I try to copy the file I get an I/O error. Depending on which file I get the error after copying different amounts of data, One file cuts out after just a few megs, others get a couple of hundred megs then error out. And some file I can copy the whole thing. BUT THE KICKER IS all the files are viewable when launched from the DVD.

Any help is appreciated.

Serge

---

### Post by gupta_sumesh63 on 2007-09-15
Try command Line Interface using a terminal with the following command:

> dd if=/dev/cdrom/filename of=/home/yourname/filename.extn

Hope this helps.

---

### Post by alindsay81 on 2007-09-23
Same problem here, I can mount a view all the files on a dvd, but i cant copy them to hdd, this includes image files, audio files and windows exe&#347;. the dvd&#347; all work perfectly in windows on the same dvd drive. im running 7.04-64bit. Pioneer dvdrw

[ 7384.690692] end_request: I/O error, dev sr0, sector 147404
[ 7384.690697] printk: 4 messages suppressed.
[ 7384.690703] Buffer I/O error on device sr0, logical block 36851
[ 7384.733461] sr 0:0:0:0: SCSI error: return code = 0x08000002
[ 7384.733468] sr0: Current: sense key: Hardware Error
[ 7384.733475]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)

---

### Post by alindsay81 on 2007-12-16
Finally solved my DVD reading issue by setting the drive to UDMA2 mode in the bios (it was originally UDMA4). I can now copy files from the drive without errors.

---

