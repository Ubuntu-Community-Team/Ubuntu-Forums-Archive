---
title: "Windows won't load after reformatting Linux Partition"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by jolt459 on 2008-01-25
Hey,

I reformatted my Ubuntu Partition of my hard drive to NTFS so I could store data on it when on my Windows Partition. But when I try to boot up into Windows, Grub has an error and doesn't let me load.

I know my windows is on the partition, but it seems that GRUB is getting in the way. So do I need to delete it? If so, how?

Thanks. (This may not be in the correct forum, if not, then I apologize)

---

### Post by UltraMathMan on 2008-01-25
Looks like the Grub Super Disk might help you. [http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download") I've never used it myself, but the Documentation has a Remove Grub menu option.

-Hope this helps :)

---

### Post by jolt459 on 2008-01-25
I'm really sorry if I sound like a complete moron, but I can use this to get rid of GRUB? And once I do remove GRUB, how will I boot into Windows?

Thanks..


And does it help if I say the error was number 15? I'm pretty sure it was 15.

---

### Post by UltraMathMan on 2008-01-25
What's happening is that grub is looking for more information on the partition where your linux install was located but (obviously) cant find it. The Grub Super Disk, looks like it will remove it, but I found another method you might want to try first. Bootup your XP install disk and go to the recovory console by pressing 'R'. Then type ```
fixmbr
```

-Hope this helps :)

---

### Post by jolt459 on 2008-01-25
Eh, don't have an XP Install Disk.

All I have is the disk that came with my computer that re installs everything, all the trial software that originally came with the computer, etc.

I don't think I can use that. But is there another way?

---

### Post by UltraMathMan on 2008-01-25
Then Super Grub disk will do that for you [Instructions]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows")

---

### Post by jolt459 on 2008-01-25
Alright, I'm going to try that.

But one question, I'm using a Pen Drive, do I just extract the tar.gz file into the pen drive and boot up with it? I just want to make sure.

Thanks.

---

### Post by UltraMathMan on 2008-01-25
It looks that way to me, for more info check [Grub Super Disk - USB]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#bill")

---

