---
title: "How to remove Grub/Ubuntu from a Dual Booting System?"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by bunnicula on 2006-07-11
I set up a dual boot with Windows XP and Ubuntu last week, but I have decided that Ubuntu/Linux is not for me and I would like to go back to Windows. I used Partition Magic to delete the two partitions that I had set up for Ubuntu (an Ex3 and a swap) and I resized my NTFS partition to cover the free space. It appeared as though this worked, but when I rebooted my computer, Grub was still there and of course, it was coming up with an error and wouldn't let me into my computer. Is there a way to fix this or am I going to have to re-install Windows?

---

### Post by izmaelis on 2006-07-11
No, you don't have to reinstall your Windows. Master boot record must be fixed. You can do this by starting Windows Recovery Console (more info [here]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true")) and run **fixmbr** command in the command line interface. That's all!

P.S. It's sad, that you are leaving Ubuntu although you can still dual boot it sometimes to get more knowledge.

---

### Post by pbaehr on 2006-07-11
If you boot to your Windows XP CD and select recovery console it will drop you at a command line. Typing:
```
fixmbr
```
should put everything back to normal.

Edit: Crap. I was beat to it!

---

### Post by dmizer on 2006-07-11
actually you may have far more problems at this point than just grub.  once you make your ntfs partition size smaller to give linux room, it's nearly impossible to return it to it's former size ... windows doesn't know what to do with itself if suddenly it's main partition becomes bigger.

i really don't know for sure if partition magic can overcome this problem or not, but it comes down to ntfs not reading the partition table correctly anymore.  it's possible to recover from this, but it's not easy.

in order to get rid of grub, you simply need to boot to window's install cd, and do a repair on your master boot record (mbr).

---

### Post by bunnicula on 2006-07-11
Thanks for the help. I completely forgot about the 'fixmbr' command (I only learned about it last week).


izmaelis - It is sad, but I wasn't able to set up the wireless and I was having trouble with my notebook overheating.


dmizer - I hope that I don't have anymore problems. After I ran Partition Magic, I was still left with an unallocated partition of 7 megs or so and I'm not sure where that came from. My C drive also seems smaller than it was before (I have a 40G drive and it says that it is 37.2G - I thought that it was 38G before...).

---

### Post by dmizer on 2006-07-13
you'll be okay if you can boot to it, but don't be surprised if you run into roadblocks.

windows doesn't handle disk space nearly as efficiently as linux does so that's probably why you're not seeing as much disk space.  kind of a moot point now, but you would have been better off to leave the ubuntu partion as it was and simply reformat it into a windows file system (fat32 or ntfs).  this would have given you an extra drive letter, but it would have been safer and would have allowed you to retain all your drive space.

at least part of the missing space is most likely the remnants of your old partition table, which in order to retain the integrity of the os, partition magic was not able to remove.

---

