---
title: "Looking to installin Ubuntu on MacBook 4,1"
date: 2012-09-21
forum: Apple Hardware Users
---

### Post by bbqamazing on 2012-09-21
Hi, I'm new here. Never been a Linux user (except once I bought a used iPod that had Linux installed). I have a MacBook from early 2008 (4,1) with a Intel Core 2 Duo processor and I'm running OS X 10.5.8. I have 120GB of internal storage. I also have a 1TB external hard drive. I'm wanting to run a dual boot of OS X and Ubuntu. I've backed up my computer onto the hard drive, I've downloaded Ubuntu Desktop 12.04 LTS, bought some blank CD's, and now I'm a little stuck. I guess I need to partition my hard drive? I don't have Boot Camp, and I guess I can't get it, because I'm running 10.5. I'm a little wary of doing it in Disk Utility, because I'm not sure I understand what I'm doing. I only have 21 GB of free space on the laptop. Does that mean that I can only partition 21 GB of space for Ubuntu? Can I boot one OS from the external? I think I would prefer that.

---

### Post by bbqamazing on 2012-09-23
Figured it out.

---

### Post by Ivan Vazov on 2012-12-06
Hello, 

I have the same macbook and the same question as you. Can you please share what was the best solution for you?! 

Thanks!

---

### Post by trogdor1138 on 2012-12-07
> **Ivan Vazov said:**
> Hello, 

I have the same macbook and the same question as you. Can you please share what was the best solution for you?! 

Thanks!

If you have only OS X on your Mac currently, you'll need to shrink the OS X partition and create another for Ubuntu. The safest way to do this is from inside OS X, using the Boot Camp Assistant. The assistant refers to Windows, but all it's doing is creating a FAT partition. The Ubuntu installer can read and use this partition easily.

If for some reason Boot Camp Assistant doesn't work, or it's not currently on your Mac, the 'diskutil' utility can be used from Terminal. It's a little more in-depth, and I can't post exactly the steps you'll need since your drive may likely be different, but you can find Apple's documentation here: [http://developer.apple.com/library/mac/#documentation/darwin/reference/manpages/man8/diskutil.8.html](http://developer.apple.com/library/mac/#documentation/darwin/reference/manpages/man8/diskutil.8.html)

Once you've moved partitions about, reboot your Mac with the Ubuntu CD or DVD in your drive. Most Mac's can't boot legacy OS's from a USB drive, so you'll probably have to burn a disc.

If you need help with diskutil, please post the output from Terminal of the following:

```
diskutil list
```

---

