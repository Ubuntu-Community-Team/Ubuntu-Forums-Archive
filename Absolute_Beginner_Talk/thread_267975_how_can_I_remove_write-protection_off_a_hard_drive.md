---
title: "how can I remove write-protection off a hard drive?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by selbekk on 2006-09-29
I just installed linux for the first time, and I think it's kinda hard to understand. 

I used to have windows xp, and I had a lot of pictures and stuff on a different hard drive. However, when I try to change the owner rights and stuff on the hard drive, I get an error saying that it's on a write-protected disc. What could I do to fix this?

Oh, and totally unrelated, I need something to play my gigs of music, where do I find that?

Peace, and thanks for all help.

~ selbekk

---

### Post by steve.horsley on 2006-09-29
Linux can't write to NTFS - MS won't publish the spec. You can read NTFS though - I guess that's both easier and safer than writing.

For playing MP3 etc, these codecs are not shipped by default for legal reasons. See this link: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by selbekk on 2006-09-29
so will I lose all my music and all my pictures then?

---

### Post by skymt on 2006-09-29
Why not just copy your stuff to your Linux drive?

---

### Post by muep on 2006-09-29
No, you won't. You just can't write them on your NTFS partitions.

If you are no longer using Windows, try to switch to another filesystem. FAT32 works for both Windows and Linux. Ext2/3 is also possible to make working in both operating systems.

---

### Post by selbekk on 2006-09-29
I only have 30 gig worth of space on my linux drive, I thought I didn't have to do anything to the rest of the discs :/

how can I install mp3 support in linux then?

---

### Post by mendingo84 on 2006-09-29
i had the same problem as you mention here right, surprise!, today! i used partition magic to turn ntfs partitions into fat32, as ntfs can't be written. after having that done, i had to mount the partitions (that goes like 
sudo mount /dev/hdaX mnt/path   whre hdaX is the name of your desired partiotion) to actually be alble to use the data on them.
as for music, the easiest way is to use Adept to downlaod the "libxine-extracodecs" package and then, also using Adept downlaod Xmms.

---

