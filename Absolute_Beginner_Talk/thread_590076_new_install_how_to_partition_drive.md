---
title: "new install how to partition drive"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by cybergalvez on 2007-10-24
Hi all,
I'm building a new system with a 400 gig drive, how big should I make the / partition?  I was thinking of doing the partition like this:
/swap = 8gig (I have 4 gig or ram)
/ = 100 gig
/home = remaining

Does this sound reasonable? 
Jose

---

### Post by Arwen on 2007-10-24
Hello,I'd like to tell you my opinion but you should wait for more responses:

I think your swap is tooooo big,1GB might be enough.Your root partition can be installed in even 5GB and your /home can be as large as you want.That is to say everything is OK except swap which is bigger than needed.
To be honest,if I were you and had a 400GB hd,I would allocate 100GB for ubuntu((swap,/ and /home) and if I needed more space,create partitions later on ;-)



To be more honest I would do an extreme multibooting system :-P

---

### Post by aysiu on 2007-10-24
This is what I would do:

swap = 2 GB of RAM
/ = 20 GB
/home = remaining

Most of your files will be personal files (videos, music, photos, documents), and those are stored in your /home/*username* directory.

/ will probably never be more than 6 GB, but if you have 400 GB total, 20 GB will leave you more than enough room, just in case.

---

### Post by cybergalvez on 2007-10-24
So even If I install a bunch of software for say video editing and stuff I really wouldn't need more then 20 Gig

If I do run out of space in my root (but still have some left in the other partition) would I be able to simply shrink one partition to give space to the other ?
Jose

---

### Post by ant2ne on 2007-10-24
> **cybergalvez said:**
> So even If I install a bunch of software for say video editing and stuff I really wouldn't need more then 20 Gig

If I do run out of space in my root (but still have some left in the other partition) would I be able to simply shrink one partition to give space to the other ?
Jose
with gparted

---

### Post by aysiu on 2007-10-24
I really can't see the root partition getting bigger than 20 GB, even with a ton of programs installed. If you want to be even safer than that, maybe make it 30 GB?

---

### Post by Last on 2007-10-24
Not meaning to hijack this thread, But as reading through I am questioning my own partitioning scheme. I am dual booting on a laptop so my partitions are small. I manually partitioned this - I have 1gb swap (512 RAM) and a 7.5gb / and then the rest is for windose. No /home. Is this not a standard way of doing it? Or am I missing something?

-Thanks ;)

---

### Post by MegaJim on 2007-10-24
To be completely honest with you, I wouldn't trust any file system to be mounted to /home other than 3fs, and equally I wouldn't trust other operating systems to read/write a 3fs partition.

For this reason I would recommend you create things pretty much as you've laid out, but just leave yourself a small amount of space for /home just to hold settings and install data incase the root partition is destroyed, or so when you want to update settings are intact.

For your personal data files, music, videos and what-have-you, I would use the rest of the drive on its own primary partition using ntfs, as now its a fairly universal filesystem.

---

### Post by MegaJim on 2007-10-24
> **Last said:**
> Not meaning to hijack this thread, But as reading through I am questioning my own partitioning scheme. I am dual booting on a laptop so my partitions are small. I manually partitioned this - I have 1gb swap (512 RAM) and a 7.5gb / and then the rest is for windose. No /home. Is this not a standard way of doing it? Or am I missing something?

-Thanks ;)

The thinking behind creating a separate partition in /home is that your settings/configuration files will be intact even after a complete OS breakdown and reinstall.

I'm in the same situation as you though, (a tiny 40gb HD) and have exactly the same setup with windows taking up more than half the space - M$ development tools are real data hoggers.

---

### Post by Last on 2007-10-24
I see, thanks for the answer. I guess I'll just use what I have set up for the time being. I'll probably be upgrading laptops soon anyway. Thanks.

---

### Post by cybergalvez on 2007-10-24
> **MegaJim said:**
> To be completely honest with you, I wouldn't trust any file system to be mounted to /home other than 3fs, and equally I wouldn't trust other operating systems to read/write a 3fs partition.

For this reason I would recommend you create things pretty much as you've laid out, but just leave yourself a small amount of space for /home just to hold settings and install data incase the root partition is destroyed, or so when you want to update settings are intact.

For your personal data files, music, videos and what-have-you, I would use the rest of the drive on its own primary partition using ntfs, as now its a fairly universal filesystem.


What is 3fs?

---

