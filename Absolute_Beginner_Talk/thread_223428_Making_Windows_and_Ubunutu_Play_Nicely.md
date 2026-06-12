---
title: "Making Windows and Ubunutu Play Nicely"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Aikon- on 2006-07-26
First I should note that I **am not** an absolute beginner, however I could not find a more suitable forum for this thread. I have no issue with this thread being moved to a more appropriate location.

I've been playing with dual-boot linux/windows systems for some time now (in fact, after dusting off my old Maxtor I found Ubuntu 5.04 on there ;) )

For me personally, it is absolutely vital that I can actively swap files back and forth between Windows and Linux, and therefore I would like to format my large media drive in such a way that both OSs can access it. I see three options:
[LIST=1]
[*]Format as FAT32 and suffer the dire consequences
[*]Format as NTFS and use the newly-popular ntfs-3g to access it in read/write mode from Linux (native in Windows)
[*]Format as ext3 and use ext2ifs ([www.fs-drive.org](www.fs-drive.org)) to access it in read/write from Windows (native in Linux)
[/LIST]

I'm not an expert on file systems, but I know my way around, and the first option makes me shudder. As for the other two, I'm at a loss as to which is the better way to go. I have more faith in the quality of open-source projects such as ntfs-3g than I do for Freeware projects such as ext2ifs, however I also know that NTFS is a PITA to write to.

Any input would be greatly appreciated (and no, I don't want to use another computer to expose this drive as a network share).

Thanks in advance,
-Scott

---

### Post by T700 on 2006-07-26
Short and simple:  At this stage of the game I would *not* trust my production data to any of the methods of writing to a NTFS drive.  I just don't have the level of confidence that will let me sleep at night, doing that.  Personally, I hold my nose and use FAT32.

Your mileage may vary.

Paul

---

### Post by Third Thoughts on 2006-07-26
From what I've read it sounds like ntfs-3g is fairly safe. Someone else on the forums conducted a test that you can read about here.
[http://www.ubuntuforums.org/showthread.php?t=217009&page=4](http://www.ubuntuforums.org/showthread.php?t=217009&page=4)
I personally have no clue because I wiped windows a few months back. But I used to have a small fat32 partition for sharing files.

~Andrew S.

---

### Post by jincast90 on 2006-07-26
> **Aikon- said:**
> First I should note that I **am not** an absolute beginner,
-Scott

You just had to save your pride huh.

---

### Post by Aikon- on 2006-07-26
> **jincast90 said:**
> You just had to save your pride huh.
Not really.. Just letting people know that I'm not looking for "see this guide" or "read this article" for how to do something, but am in fact looking for opinions as to why one option should be chosen over the other; The idea of a beginner forum is to prevent newcomers from being inundated with technical data, jargon and opinions that they probably neither need nor care about.

Besides, I have no pride to save; nearly everytime I install or update a distro, I break my Windows install and have to fix it; and nearly every time I try to install drivers or software once the distro is up and running, I break the distro ;)

---

### Post by kurniawands on 2006-07-26
> **Third Thoughts said:**
> From what I've read it sounds like ntfs-3g is fairly safe. Someone else on the forums conducted a test that you can read about here.
[http://www.ubuntuforums.org/showthread.php?t=217009&page=4](http://www.ubuntuforums.org/showthread.php?t=217009&page=4)
I personally have no clue because I wiped windows a few months back. But I used to have a small fat32 partition for sharing files.

~Andrew S.

Yup, TT is right. I use ntfs-3g right now and still got no problem with it (yet). I can easily read/write, i can even manage every single file in my hdd (share using samba, set permissions, etc)

---

### Post by jincast90 on 2006-07-26
> **Aikon- said:**
> Not really.. Just letting people know that I'm not looking for "see this guide" or "read this article" for how to do something, but am in fact looking for opinions as to why one option should be chosen over the other; The idea of a beginner forum is to prevent newcomers from being inundated with technical data, jargon and opinions that they probably neither need nor care about.

Besides, I have no pride to save; nearly everytime I install or update a distro, I break my Windows install and have to fix it; and nearly every time I try to install drivers or software once the distro is up and running, I break the distro ;)

Yeah okay. I apologyse.

---

### Post by Aikon- on 2006-07-26
> **jincast90 said:**
> Yeah okay. I apologyse.
S'all good =)

I've decided to give ntfs-3g a shot since I really don't feel like reformating my file server (read: I don't have another drive to back it up on) so we'll see how that goes.

---

