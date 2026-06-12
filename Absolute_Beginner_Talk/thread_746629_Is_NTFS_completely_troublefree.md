---
title: "Is NTFS completely troublefree?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by BetterSense on 2008-04-05
For reasons of *dows migration, I have a HDD that used to be in an external enclosure that has a bunch of  media on it. I would like to stick it in my desktop computer and use it. It's NTFS. Can I just do that, or should I reformat it to a linux file system (not easy, since I don't have anywhere to store what's on it while I reformat it). 

What are the downsides of using NTFS in a linux system?

---

### Post by markharding557 on 2008-04-05
ntfs is supported in ubuntu by defualt so you can leave it as it is

---

### Post by Joeb454 on 2008-04-05
NTFS Read/Write is supported fully as of Ubuntu 7.10 (Gutsy) :)

It *shouldn't* be a problem, I've never had any myself, I often write to my iPod from Ubuntu (that's NTFS formatted)

---

### Post by InfinityCircuit on 2008-04-05
Delete support, in particular when it comes to defragmentation, is sketchy with the ntfs-3g drivers.  NTFS is also horribly slow even for a journaling filesystem.  For long-term compatiblity I'd recommend reformatting

---

### Post by superprash2003 on 2008-04-05
yes ubuntu does not have great support for ntfs

---

### Post by JoshuaRL on 2008-04-05
The issues you will likely have here is the common ones to NTFS.  It's slower, it isn't as reliable, and it fragments easy.  Plus, there aren't a lot of defrag programs for Linux as ext3 doesn't neet it.  They're out there if you search around for a bit, but not as easy as other tools.

---

### Post by articpenguin on 2008-04-05
plus if you use ntfs in linux and have hard poweroff then you have to load the ntfs partition in a windoze box as linux dosent know how to replay the journal yet.

---

### Post by harrybazeegar on 2008-04-06
I think if you are dual booting with windows then ntfs will be fine... but with only ubuntu u will sometime run into the "hard poweroff" problem

---

### Post by Zeroangel on 2008-04-06
Fat32 is superior for trouble free operation. Especially if your using it as an external enclosure.

Reasons are this
- If you transfer an NTFS drive to a computer whos linux does not have NTFS properly configured, then your gonna have problems mounting it and have to jump through some hoops.
- If theres ever an error in the NTFS journal, then you cant fix it within linux, you have to boot into windows and run chkdsk /f e: (or whatever the external drive is).
- If theres an error in the NTFS journal, then if you try to mount it in vista, theres a small chance that vista will lock up because it doesnt handle errored NTFS externals very well.
- If theres an error in the NTFS journal, then you have to run the command sudo ntfsfix /dev/sdaX (for whatever the drive is) just to get it to be writable.

NTFS will work, but if you have to format something in a new filesystem, go with FAT32 unless data protection is critically important (as in you manage thousands of dollars worth of data).

---

### Post by BetterSense on 2008-04-06
> plus if you use ntfs in linux and have hard poweroff then you have to load the ntfs partition in a windoze box as linux dosent know how to replay the journal yet.

> - If theres ever an error in the NTFS journal, then you cant fix it within linux, you have to boot into windows and run chkdsk /f e: (or whatever the external drive is).

Quite true, I've already had to do that once, and I nuked my windows part now. One thing though, the linux error told me to run ckdsk /f, and that the /f was 'very important!' When I booted from a windows CD (into command line since my XP install wouldn't boot anymor) there weren't any /f option for chkdsk. I ran chkdsk /R, and then it worked. WTF?

Thanks for reminding me about he hard poweroff thing. Maybe I'll buy a new HDD.

---

