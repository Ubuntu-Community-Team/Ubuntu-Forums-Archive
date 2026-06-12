---
title: "MD5sum"
date: 2005-06-01
forum: Absolute Beginner Talk
---

### Post by heltinde on 2005-06-01
Hi people

How do I use MD5SUM?

---

### Post by GeirG on 2005-06-01
$ md5sum --help
and
$ man md5sum
is a good start ;-)


The command "$ md5sum imps_chapter1_DAVENPORT_928735.avi" will give you the md5 checksum of the file imps_chapter1_DAVENPORT_928735.avi:

4040481718f4463b3e2c9e7643285a81  imps_chapter1_DAVENPORT_928735.avi

"$ md5sum imps_chapter1_DAVENPORT_928735.avi > imps.md5" creates the file imps.md5, containing the output of the previous example.

If you have both files imps_chapter1_DAVENPORT_928735.avi and imps.md5, you can use the following command to verify the integrity of named files:

$ md5sum -cv imps.md5
imps_chapter1_DAVENPORT_928735.avi OK

Have fun,

---

### Post by heltinde on 2005-06-01
Efter at have læst det 3 gange, tror jeg næsten, at jeg forstår det ;-)

(Eng.: After reading it 3 times I think I almost understand it).

Thanks

---

### Post by xmastree on 2005-06-01
You can also run it on an entire disc. There's a file **md5sum.txt** in the root directory of your install CD, which lists the checksums of all the files on the disc.

The command is md5sum -c md5sum.txt (or whatever the file is called). This will check each file against the list, and inform you of any broken ones.


**GeirG** is right though, man md5sum is a good place to start. That holds true for most commands or programs. man = manual, and it displays the manual for whatever command you wish. It's a good idea to maximise your terminal window before running it. Some of them are quite long, and you can see more of the file at once that way.

---

### Post by heltinde on 2005-06-02
Thanks.

I just downloaded Warty to see if it runs faster than Hoary on my secondary pc. Before the installation I would like to do the md5 checksum on the cd I burned  - can I do that from a windows computer? Sorry I wasn't more specific in my initial question. After a long dag with my eyes glued to the screen, I simply don't think so well.

I'll remember the man pages. I must admit I don't use them very often because they look complicated. I'll learn though.

---

### Post by GeirG on 2005-06-02
There is definetly some md5 programs for Windows, I know I have used a couple.

I'd recommend googling for md5 and windows


Regards,

---

### Post by heltinde on 2005-06-02
OK, I'll do that!

---

