---
title: "JPG rotated in Windows but not in Linux"
date: 2008-02-25
forum: Art &amp; Design
---

### Post by ItalOz on 2008-02-25
Hi
I was preparing a backup for my photo collection that, when I was using windows, I used to browse with ACDSee.
I was browsing to it with Gwenview (painfully slow: I had a folder with 1200pict and 4.3Gb large - each pict up to 3Mb on an NTFS partition).

I found out that some, NOT ALL, of the pictures I already had rotated in windows appeared not rotated in linux.

I booted windows and I found out that they actually WERE rotated. ACDSee  and Paint Shop Pro showing them correctly.

Back to linux they are not rotated (not all of them as said).

What is the reason?

If I rotate them with Gwenview they would appear correctly orientated in both linux and windows.

What is it that windows knows and that linux doesn't and where is this information written since performing the rotationg in linux does not change the orientation of the picture (that was already correct) in windows?

---

### Post by Martje_001 on 2008-02-27
There is some meta-data written to the file. If you open these images with The Gimp, does it ask you to rotate?

---

### Post by ItalOz on 2008-03-03
That was the clue!
I run some tests
GIMP is a very smart program and understands that the orientation metadata does not correspond with the actual orientation of the file.
I found out that the files I did not see rotated under linux where shot with my other camera (I have two digital cameras).
So all the picts from my Olympus camera I had previously rotated under windows with ACDSee were rotated also in Linux
and all the picts from my Canon camera I had previously rotated under windows with ACDSee were NOT rotated also in Linux.

There was another fact I did not know, that is that these photo manager programs DO NOT actually rotate the pictures, they just change this "orientation tag" in the metadata which I did not not it existed and which, I am sure, most of people are unaware of.

This is evident also if you have some large file and you open it with Gwenview (which is incredibly slow compared with ACDSee on the same machine, somebody knows why?), some files are opened line by line from top to bottom (if the orientation is the original one the photo was shot) some others are opened from left to right or vice versa if the orientation is different from the original.

That's it.

I just keep on wondering why Gwenview is so slow in performing the operations of showing and rotating the images compared to ACDSee under windows, do you think it might be a problem of my installation or it is like that?

---

