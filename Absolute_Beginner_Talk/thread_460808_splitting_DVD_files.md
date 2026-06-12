---
title: "splitting DVD files"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-06-01
hi is there any tools (free) for splitting DVD(VOB) files such that they can be viewed individually .


just for e.g

i have a 1GB VOB file.


i need to have it as 2 chunks as 600MB and 400 MB files so that i can put them on 2 CDs and take away so that i can view them in CD players.


also is there any tool for merging the VOB (other formats like mpeg,avi,wmv,dat too)files into a single file.

---

### Post by adamJ5 on 2007-06-17
Bump

I have the same problem...

---

### Post by qpieus on 2007-06-17
the split command could be used to break up your big file into 2 pieces. But I don't think you would be able to view each piece separately. I'm not aware of a simple tool that can do that for you, other than actually transcoding the vob file into 2 smaller, standalone video files. I'm pretty sure that can be done, but I can't help you with that, as I know nothing about video manipulation.

Anyway, back to split.

split -b 600m filename

will break the file *filename* into a 600 mb chunk and a 400 mb chunk, each with a new name. 

cat newname1 newname2 > filename will combine the pieces back together just like the original file.

type man split in a terminal to read the man page or google for examples, like:

[http://www.computerhope.com/unix/usplit.htm](http://www.computerhope.com/unix/usplit.htm)

---

### Post by cotcot on 2008-02-17
Same question. I was looking for an easy vob splitter, but could not find one. I want to break up a vob of 1 hour into vob's of 6 minutes in order to get subtitles on a dvd.
I have found no better way than this :

1. Load vob in kdenlive
2. copy the vob on the timeline
3. razor the vob into 6 minutes chunks
4. save the kdenlive project
5. load it again
6. delete all but the first chunk
7. save it as kdenlivechunk1
8. export the timeline as dvd
9. redo tis for the second chunk and so on

 Finally i have 10 vob's that i can use with qdvdauthor to a dvd with subtitles.
I tried with chapters as well but do not get a mosaic with all the chapters.

---

### Post by akudewan on 2008-02-17
This may not be exactly what you're looking for, but have a look at k9copy: [http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)

Its available in the repositories

---

