---
title: "Creating an archive of 1000's of files"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by zgerrz on 2006-03-12
I have over 10,000 mp3s that I would like to backup to an external hard drive. My issue is that all the files together take up about 65 GB, so I wondering how to reduce the size of a backup of them since I don't have unlimited space.

I thought that I could use an archive (tar file) to make a backup of all the files and compress them. My question is, what variables should I use to achieve maximum compression? Is a tar file the best route to go or are there better archive formats that can generate better compression for 1000's of mp3 files?

---

### Post by skymt on 2006-03-12
First off, tar doesn't actually compress anything. It just bundles the files into one file, which can then be compressed by something like gzip or bzip2. bzip2 is probably your best bet, as it claims to have better compression than gzip. I wouldn't use anything out of the ordinary, like 7zip. New programs have bugs, and you don't want to lose your backup due to a bug. bzip2 and gzip have been around long enough to be trustworthy.

---

### Post by sapo on 2006-03-12
I think you arent going to gain anything compressing mp3, mp3 is already compressed :p

---

### Post by Pragmatist on 2006-03-12
I got the below excerpt from this website (my emphasis):
[http://www.linux.org/lessons/beginner/l18/lesson18c.html]("http://www.linux.org/lessons/beginner/l18/lesson18c.html")
> [INDENT]-rw-r--r--    1 mike     users      441044 Nov 28 08:34 2001-11-28_good.wav
[/INDENT]If for some reason you wanted to keep these reminders, files of this size would quickly begin to take up space. Disk space is cheap, but there's no reason to occupy space if we can compress it. We could take out our tools gzip or bzip2 that we learned about in a previous lesson. **'bzip2' **will actually get the file down to about** half its original size**:  [INDENT] -rw-r--r--    1 mike     users      206442 Nov 28 08:34 2001-11-28_good.wav.bz2
[/INDENT]But there is a much better way of doing this, for now, by converting it to **MP3 format**. Look what we get for the same file as an MP3:  [INDENT] -rw-r--r--    1 mike     users       80234 Nov 28 08:48 2001-11-28_good.mp3
[/INDENT]You've got it down to about **one fifth of its size**. And you can hear it right away with an MP3 decoder/player.
 

---

### Post by zgerrz on 2006-03-12
Well I didn't think I would gain a tremendous amount of space compressing mp3s in an archive, but more is better than none.

When using bzip2, how can I tell the program to write the output file to my external hard drive? By default it creates the archive to the same directory of the files. I read the man but I don't see my answer.

---

### Post by Bandit on 2006-03-12
Well If yo tar anything the final file size of the tar can not exceed 2GB unless I am mistaken. So you will need to create about 33 Tar files and use 17 DVDs.
2 tarbles per DVD. 
As far as compression. A 2GB tarble compressed full of MP3s may compress very little or even none at all since the MP3s are already at a highly compressed state.
Not to mention bzip2 is going to take forever trying to recompress the files..
Best bet is to just grag and drop groups onto a DVD and burn them.
Cheers,
Joey

---

### Post by engla on 2006-03-12
Take ten or more mp3 files and try to see what you can gain...

make a tar file to see how much data it is
tar cfv test.tar test-dir
gzip --best -c test.tar >test.tar.gz
bzip2 --best -k test.tar

Try any other compression algorithms if you have them

See where that goes, I would guess you save less than 3%

---

