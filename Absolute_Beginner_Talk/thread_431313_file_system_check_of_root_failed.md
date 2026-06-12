---
title: "file system check of root failed"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by mikawber on 2007-05-02
I have Edgy installed on my laptop and I shut it down to move it out into the living room. After working on it out there for awhile I shut it back down to bring it back in my room. When turning the maching back on I get an "Automatic file system check of the root filesystem failed." error. It says to run fsck manually, but when I try that I get " fsck.ext3: Unable to resolve 'UUID=07D5-0615' ". I didn't mess with anything that I shouldn't have, I was just writing a paper. Please help! Thanks

---

### Post by mikawber on 2007-05-03
I fixed it. All I did was boot into the Live CD, mount my hard drive, and then run fsck on my hard drive. It worked but I'm still confused on why I couldn't run fsck when it prompted me to do so. Any ideas?

---

### Post by bren21 on 2007-05-25
it seems I have the same exact problem, and I am wondering if anyone could help me. I got onto the live cd, and mounted my harddrive, now I just need to now how to run fsck on my harddrive. Sorry if this is a noob question, I have never had to run anything off of the live cd.

---

### Post by bren21 on 2007-05-25
bump

---

### Post by mikawber on 2007-05-26
I'm sorry, my post last time had a typo. I **_DID NOT_** mount my hard drive. 

First, find out the location of your hard drive by typing:

```
sudo fdisk -l
```

Afterwards type in the following command, replacing /dev/sda1 with your hard drive location

```
sudo fsck -y /dev/sda1
```

---

### Post by bren21 on 2007-05-27
Nice, it worked. Thanks for the help.

---

