---
title: "Readable and Writable file system between OS X and Ubuntu ?"
date: 2008-10-27
forum: Apple Hardware Users
---

### Post by Sweet Spot on 2008-10-27
I'm trying to back up the data from my Kubuntu machine to an external HD which I just remembered was formatted to OS X's native file system. My first question is whether or not I can re-format the external drive (from within Kubuntu) so that it is read and writable to both Ubuntu and OS X, and how would I do this ? 

I know that FAT 32 is the common thread between them, but it's not a very secure file system. I don't mind too much though, since it won't be hooked up permanently, so if the answer is simply FAT 32, so be it. I'd just appreciate someone telling me how I can go about formatting the drive to said file system from the command line within Kubuntu. Thanks ! 

Doug

---

### Post by cyberdork33 on 2008-10-27
HFS+ (OSX's filesystem), FAT32, and NTFS will all work.

FAT32 is, of course, the most compatible. HFS+ and NTFS can have issues in one OS or another. 

You can format your external drive just like any other hard drive. Install gparted (sudo apt-get install gparted) and then run it. Make sure you select the appropriate hard drive and delete the existing partition and crate a new one in it's place (formated however you want).

---

### Post by Sweet Spot on 2008-10-28
Thanks. I don't know why but, when I had opened Gparted previously, it didn't show the drive I had attached, which is why I posted the thread. It has shown up now, and I reformatted to FAT 32. It was already HFS+ which wouldn't play along.. 

Doug

---

### Post by cyberdork33 on 2008-10-28
> **Sweet Spot said:**
> Thanks. I don't know why but, when I had opened Gparted previously, it didn't show the drive I had attached, which is why I posted the thread. It has shown up now, and I reformatted to FAT 32. It was already HFS+ which wouldn't play along.. 

Doug
You have to disable journaling (in OSX) on the filesystem in order to enable writing under Linux.

---

### Post by Sweet Spot on 2008-10-28
I wish I had done this in the first place, actually, because now that I've copied most of the stuff I need for backup, I realized that a couple of files are over 4 gigs, and I'm not sure of what to do with them. They're about 7 gigs in size. Any ideas ? Or am I going to have to hook it back up to the MBP and reformat it to HFS without journaling from there ?

doug

---

### Post by cyberdork33 on 2008-10-28
> **Sweet Spot said:**
> I wish I had done this in the first place, actually, because now that I've copied most of the stuff I need for backup, I realized that a couple of files are over 4 gigs, and I'm not sure of what to do with them. They're about 7 gigs in size. Any ideas ? Or am I going to have to hook it back up to the MBP and reformat it to HFS without journaling from there ?

doug
or use ntfs... or just burn the 7GB files to a dual layer DVD.

---

### Post by Sweet Spot on 2008-10-30
Thanks buddy. I had completely forgotten that you can install NTFS permissions on to Ubuntu, so that's just what I did, and am now backing my stuff up. I'm really glad it's an viable option now, as it makes a lot of things so much easier to deal with across the board.. 

Doug

---

### Post by cyberdork33 on 2008-10-30
> **Sweet Spot said:**
> Thanks buddy. I had completely forgotten that you can install NTFS permissions on to Ubuntu, so that's just what I did, and am now backing my stuff up. I'm really glad it's an viable option now, as it makes a lot of things so much easier to deal with across the board.. 

Doug
Could you please mark this thread as solved? (Thread Tools menu at the top of the page).

---

