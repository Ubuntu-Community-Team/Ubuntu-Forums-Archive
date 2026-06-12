---
title: "[SOLVED] Hardlinks"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by CommanderBob on 2008-02-15
I was using FSlint to remove duplicate mp3 files but I accidentally merged them with hardlinks and did not delete them. How can I delete the duplicate hardlinks? I don't care witch one is deleted just so I only have one so when I import it into Amarok it is not duplicated.
Thanks,
Justin

---

### Post by stevejesus on 2008-02-15
This would interest me to know as well.

---

### Post by dcstar on 2008-02-15
> **CommanderBob said:**
> I was using FSlint to remove duplicate mp3 files but I accidentally merged them with hardlinks and did not delete them. How can I delete the duplicate hardlinks? I don't care witch one is deleted just so I only have one so when I import it into Amarok it is not duplicated.
Thanks,
Justin

Hardlinks are essentially just duplicate directory entries pointing to the same file - only when the last entry is deleted does the actual file become "deleted" (that is, the O/S can use the space for another file).

Hardlinks all point to the same inode (file **Information Node**), and will have the same file size and Timestamp as the original file that they were linked to.

If you use the command:
```
ls -i | sort
```
you will see all the entries sorted in inode order, those with the same inode are hardlinks.

---

### Post by mbsullivan on 2008-02-15
What dcstar said is correct... if you want the moral of the story: just delete the duplicates!

Mike

---

### Post by CommanderBob on 2008-02-15
I want to keep the file but delete the second link to it. Is there a program that will look at the inode and delete the duplicates for me? I have over 100 songs that are duplicated. Also they are in multiple folders. (in /media/Disk/Music/folders_with songs) All of the duplicates are in a different folder. (this happened when I added music from my brothers computer to mine and I already had some of the songs.)

Thanks
Justin

---

### Post by CommanderBob on 2008-02-15
I removed the hardlinks! All I did was copy all of my songs and then deleted the copies then the hardlinks were gone (I had real copies) Then I ran FSlint and it found the copies and I deleted them.

---

### Post by CommanderBob on 2008-02-15
Just found an easier way
fdupes -r -H -d directory_name
Justin

---

### Post by dcstar on 2008-02-16
> **CommanderBob said:**
> Just found an easier way
fdupes -r -H -d directory_name
Justin

There you go, you had a problem and dug out the solution that does the job for you - well done (hopefully more will follow your example!).

Now all you have to do is use the forum tools to mark this thread as "Solved"........

---

