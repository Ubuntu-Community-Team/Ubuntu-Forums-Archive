---
title: "Archives and Compression..."
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-04-16
I have another question, hehe. I seem to say that so often, but in all honesty this place is really great for learning. I have a large archive of videos and audio and while I've burned the most important to storage dvds I'd like to keep the rest on my external USB drive archived. I'd like this to be longterm storage and now I am kinda curious what the difference is between all of the archive formats (tar.gz , tar.bz2 , rar, zip, etc...) Which one offers the best compression over all to give me smallest filesizes? Is there a page somewhere explaining the differences between them all?

Thanks, will check back later.

---

### Post by RedSquirrel on 2007-04-16
I find bzip2 gives the smallest sizes. [Here]("http://www.linuxjournal.com/article/9370") is just one page explaining the different compression tools. If you google "compression linux" you'll find lots of pages. :)

---

### Post by stmiller on 2007-04-16
Yes tar.bz2 is the best. And can be opened in OS X, and Windows (with 7-zip).

---

### Post by dreadlord_chris on 2007-04-16
> **starcraft.man said:**
> I have another question, hehe. I seem to say that so often, but in all honesty this place is really great for learning. I have a large archive of videos and audio and while I've burned the most important to storage dvds I'd like to keep the rest on my external USB drive archived. I'd like this to be longterm storage and now I am kinda curious what the difference is between all of the archive formats (tar.gz , tar.bz2 , rar, zip, etc...) Which one offers the best compression over all to give me smallest filesizes? Is there a page somewhere explaining the differences between them all?

Thanks, will check back later.

In all likelyhood your audio & video files are already in a compressed format - mp3, wma, avi, mov, etc - these are all already compressed. If you try to compress them more with some *data compression* app you are very likely to end up with a file larger then the original.

The reason for this is very simple. Since the data contained in the audio/video file is already compressed, then there is very little, if any, further compression possible. All ***data*** compression apps have one thing in common - after compressing the target file, they must add code to the file header so that the file can be decompressed later. Generally this is not an issue as the compression more then compensates for the overhead, unless you're dealing with data that's already compressed.....

---

