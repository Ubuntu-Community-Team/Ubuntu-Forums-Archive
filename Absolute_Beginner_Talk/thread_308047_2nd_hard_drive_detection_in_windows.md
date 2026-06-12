---
title: "2nd hard drive detection in windows"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-27
I recently added a 250g hard drive as my second drive and formatted it as ext 3.  Now I dual boot with windows and have used the program that allows windows to read ext 3 drives.  

my master drive has two partitions 1 for windows and 1 for ubuntu.  ntsc for windwos and ext 3 for ubuntu.  

When I run EXT2 IFS for Windows it will recognize the 30 g partition that ubuntu has in widows but the 250g harddrive is not being recoginzed.  It see's the drive as 30g and raw, even though it is formatted.

Is there a size limit?

---

### Post by taurus on 2006-11-27
Does Ubuntu see that new harddrive all right, with all the 250GB of it?

---

### Post by gentlemanmasher on 2006-11-27
Yes

---

### Post by taurus on 2006-11-27
Do you plan to use that harddrive to share files between XP and Ubuntu?

---

### Post by gentlemanmasher on 2006-11-27
I swapped an old 80g out with this 250.  I was sharing between OS previously.  Would like to again.

---

### Post by taurus on 2006-11-27
If you plan to use the 250GB to share files between XP and Ubuntu, why not format it as fat32!  Then, both OSes would be happy...

---

### Post by gentlemanmasher on 2006-11-27
tried that 1st but couldnt' get windows to detect the drive as formatted then either.

---

### Post by taurus on 2006-11-27
You can use the LiveCD to format that drive to fat32!

---

### Post by lucid_dream on 2006-11-27
In order for XP to see the 250G drive you need to be sure that the drivers are installed in windows for the drive. I just had the exact sape problem with my new HD and after i installed the driverd into windowd it reads the new drive just fine.

---

### Post by lucid_dream on 2006-11-27
You do not want to use FAT32 with XP you should format with NTFS.

---

### Post by gentlemanmasher on 2006-11-27
I actually did have it to Fat 32 and for some reason windows wouldn't read that as fat 32 either.  No big deal I rarely use windows anyway.  I am just suprised the ext 2 program for windows works with on drive that has ext 3 and not the other.

---

### Post by gentlemanmasher on 2006-11-28
> **taurus said:**
> You can use the LiveCD to format that drive to fat32!

I got frustrated last night and reformatted my drive to fat 32 to see if that would work.  Nothing.  This is probably more of a windows thing, but I downloaded the large drive .exe for windows from the maxtor site and still nothing.  windows only see's around 33gigs of my 250g hard drive.  The bios only show 33gigs as well.  But like I said Ubuntu see's the drive no matter what.

Any suggetions anyone?

---

### Post by zekopeko on 2006-11-28
why don't you format the drive to ext3 and use some Windows ext2/3 driver so that you can read/write in windows?

---

### Post by intangir1999 on 2006-11-28
Taurus is right, it should pick it up as FAT32, however I'm not sure if windows will pick it up beyond 120 or so gigs, it may only pick up the rest as an extended drive, even then i'm not sure how it will handle memory management at that point. Which version of windows are you running, I know xp will pick up all 250 no problem, 2k may freak.

---

### Post by gentlemanmasher on 2006-11-28
XP service pack 2.  That's the wierd thing.  It detects it but at 33.  Even if it is FAT 32 formatted I still cannot get into drive.  I mean if Ubuntu detects it then it can't be a jumper issue can it?

---

### Post by gentlemanmasher on 2006-11-28
> **zekopeko said:**
> why don't you format the drive to ext3 and use some Windows ext2/3 driver so that you can read/write in windows?

Tried this also and it still won't work.  The ext .exe see's my other ext 3 partition on my master drive but even when I had the 250gig slave drive all ext3 it still detected the drive as FAT 32 and only 33gigs.

---

