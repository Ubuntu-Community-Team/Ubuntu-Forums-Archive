---
title: "Permission problems on mac"
date: 2009-01-25
forum: Apple Hardware Users
---

### Post by mkvnmtr on 2009-01-25
I have found it impossible to work with my external hard drive and usb sticks in 8.10. I have used hfs+ as a file system and can't seem to get write permission. I also want to connect on my acer ubuntu and have no luck making it more that read only. I haave been fighting it for two days and have nnow found a bug report that it is something in the kernal. I change ownership and I change permissions. They read correctly when I do ls -la but then when I try to write I can't. Then I do ls -la and they are back where I started. I have installed disk managers till I am blue in the face.But guess what. When I reformat to fat 32 all my problems go away. I am posting this lso no one has to go through the work I have. Maybe they will fix it. I think I will down load the next 9.04 or what ever it and put it on a partition to see if it is a little easier.

---

### Post by Kobalt on 2009-01-26
HFS+ support isn't native on Linux systems, so if you didn't install it this is your problem.
As far as I know you can enable it, [this wa]("http://ubuntuforums.org/showthread.php?p=2346494")y, though I never tested this myself.

---

### Post by mkvnmtr on 2009-01-26
I have enabled every cross platform program there is to work with windows formats and also mac formats. It seems this is a kernel problem that doesn't work write with ext3 also. Why would the default mount ow an esternal hard drive be read only? And then why would it not let you change it?

---

### Post by cyberdork33 on 2009-01-26
> **mkvnmtr said:**
> I have enabled every cross platform program there is to work with windows formats and also mac formats. It seems this is a kernel problem that doesn't work write with ext3 also. Why would the default mount ow an esternal hard drive be read only? And then why would it not let you change it?
HFS+ is mounted read only unless journaling is disabled (and it can only be disabled from within OS X). This is true whether it is an external partition or an internal partition. This is a limitation of the ABILITY of Linux. If you would like this to change, ask Apple to give all the specifics of their proprietary file system so that a proper driver can be written.

---

### Post by mkvnmtr on 2009-01-26
Thanks cyberdork. After your post I realized that I had to reformat in Mac disk utility to plain hfs. Now I can read and write on My mac and the three Ubuntu distros I have running. I was really needing to pass some configuration files back and forth and this makes it much easier.

---

### Post by didg on 2009-01-26
> **cyberdork33 said:**
> HFS+ is mounted read only unless journaling is disabled (and it can only be disabled from within OS X). This is true whether it is an external partition or an internal partition. This is a limitation of the ABILITY of Linux. If you would like this to change, ask Apple to give all the specifics of their proprietary file system so that a proper driver can be written.

Huh? what's  [http://developer.apple.com/technotes/tn/tn1150.html](http://developer.apple.com/technotes/tn/tn1150.html) ?

Fact is that nobody cares enough for doing it (It's not easy).

---

### Post by cyberdork33 on 2009-01-27
> **didg said:**
> Fact is that nobody cares enough for doing it (It's not easy).
Then why is it in the kernel at all?

---

### Post by didg on 2009-01-27
Hi,

> **cyberdork33 said:**
> Then why is it in the kernel at all?


There's basic HFS+ support in the kernel but this thread is about HFS+ journaling, isn't it?

HFS+ journal format has been documented by Apple since March 2004. If after nearly five years it's still not supported by Linux then yes on my book nobody cares enough.

---

