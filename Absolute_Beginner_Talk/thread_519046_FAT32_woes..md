---
title: "FAT32 woes."
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by CrashintoDMB on 2007-08-06
is there a way to get around the 4 gig limit on this other than repartitioning the hard drive?

---

### Post by Ek0nomik on 2007-08-06
No.

You can take your pick:  NTFS or EXT3.

What type of files are you dealing with anyways?

---

### Post by por100pre1 on 2007-08-06
No. Repartitioning is the best solution.

---

### Post by stchman on 2007-08-06
> **CrashintoDMB said:**
> is there a way to get around the 4 gig limit on this other than repartitioning the hard drive?

No, that is the limitation of FAT32.  You can use either NTFS or EXT3.

---

### Post by CrashintoDMB on 2007-08-06
iso files. my brother was sending me the first two bourne movies and i could only share up to 4 gigs. i didnt get to see the last 10 minutes of either of the movies.

---

### Post by Ek0nomik on 2007-08-06
> **CrashintoDMB said:**
> iso files. my brother was sending me the first two bourne movies and i could only share up to 4 gigs. i didnt get to see the last 10 minutes of either of the movies.

Oh, you didn't miss much.  He dies.

...

just kidding.  ;)

---

### Post by CrashintoDMB on 2007-08-06
hahaha. nice. so i have a 500 gig hard drive. could i technically just partition it 1 gig and 499 gigs in the NTFS or EXT3? which one is better to use? i also have to start over, don't i?

---

### Post by Ek0nomik on 2007-08-06
> **CrashintoDMB said:**
> hahaha. nice. so i have a 500 gig hard drive. could i technically just partition it 1 gig and 499 gigs in the NTFS or EXT3? which one is better to use? i also have to start over, don't i?

You can partition the drive any way you'd like.

You could do all 500GB as EXT3 or all 500GB as NTFS.  The EXT3 drive will work with Linux out of the box, while if you use NTFS you will have to use third party software in order to read and write to the disk.

Being a Linux user myself, I would go with EXT3 as I rarely use Windows (except now, while I am at work).

---

### Post by CrashintoDMB on 2007-08-06
i *will* have to start over though, won't i? (not like i got really far anyway)

---

### Post by Ek0nomik on 2007-08-06
> **CrashintoDMB said:**
> i *will* have to start over though, won't i? (not like i got really far anyway)

Start over with... what?

You will lose all your data.  I would suggest putting anything you want to keep on an external hard disk or an internal disk on another computer.

Or you can just scratch everything and start fresh.

---

### Post by CrashintoDMB on 2007-08-06
im saying i'd have to reinstall ubuntu that's all. okay. well thanks.

---

### Post by Ek0nomik on 2007-08-06
> **CrashintoDMB said:**
> im saying i'd have to reinstall ubuntu that's all. okay. well thanks.

Oh, I didn't know Ubuntu was installed on the same hard disk.  I just assumed this was an external hard disk you were referring to.

Yep, you will have to restart.  Although, if you have wallpapers, themes, and icons you want to keep, you can backup your home folder so you can keep all of your settings.  :)

---

### Post by CrashintoDMB on 2007-08-06
what about sound? when i first for ubuntu (ubuntu studio) my sound wasnt working at all. i came home from work one day and my brother had fixed it. his explanation was "i installed a lot of crap."

---

### Post by Ek0nomik on 2007-08-06
> **CrashintoDMB said:**
> what about sound? when i first for ubuntu (ubuntu studio) my sound wasnt working at all. i came home from work one day and my brother had fixed it. his explanation was "i installed a lot of crap."

LOL.  Well, you could also talk to him.  Otherwise if you tell me what kind of sound card you have I can try to find some documentation for you.

If you don't know the card model,

```
lspci
```

should reveal it.

---

### Post by stchman on 2007-08-07
Ubuntu can READ NTFS partitions out of the box.  If you wish to write to NTFS partitions then you will need ntfs-3g to be installed.

---

