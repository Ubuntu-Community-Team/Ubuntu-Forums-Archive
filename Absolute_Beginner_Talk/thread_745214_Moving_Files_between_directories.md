---
title: "Moving Files between directories"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by twp_twm on 2008-04-04
Have been trying to move a file from one directory to another and failing everytime!
I have tried using: 
[CENTER]mv file.extension targetdir
and/also
sudo mv file.extension targetdir[/CENTER]

But have failed at each attempt. The reason being that i don't have "root" permissions?

I have even tried using: sudo nautilus with the same result.
Very close to admitting defeat and giving up altogether.

---

### Post by aeiah on 2008-04-04
that's very strange. is there anything unusual about the destination? like, does it have strange permissions, or is it read only for some reason (ntfs without the read/write ntfs drivers?)

right click and go to properties, and see if the ownership is something odd and see if its read only

---

### Post by ByteJuggler on 2008-04-04
> **twp_twm said:**
> Have been trying to move a file from one directory to another and failing everytime!
I have tried using: 
[CENTER]mv file.extension targetdir
and/also
sudo mv file.extension targetdir[/CENTER]

But have failed at each attempt. The reason being that i don't have "root" permissions?

I have even tried using: sudo nautilus with the same result.
Very close to admitting defeat and giving up altogether.

As others have said, there must be something going on with your destination that's not apparent from your description.  You'll need to give us more information, ideally exactly where you're trying to move the file to.

Even so:
1.) Do you have ownership of the target folder?  If not, who does?  "ls -al targetdir" will tell you.
2.) Do you have permissions to write in the target folder?  "ls -al targetdir" will tell you. 
3.) What filesystem type (NTFS? EXT3? Reiser?) is the targetdir on?  Is this your root partition?

If you can paste the output of "ls -al targetdir" and the answers to the above questions here, we might be able to glean what's going on and how to fix it.

---

