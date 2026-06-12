---
title: "Finding duplicate photos"
date: 2012-07-28
forum: Art &amp; Design
---

### Post by Stonecold1995 on 2012-07-28
I often have many images, but I only need one of each.  I've used DoubleKiller, but the problem with it is that it uses the CRC32 checksum of the files to tell if they are duplicates, which is problematic because it will only find exact, byte-by-byte duplicates, but not two images that are the same but have different metadata, or different compression ratios, or different file types, etc.  So it's not very effective for me.  So can anyone recommend a free (preferably open source) Linux program that can do that (I can handle using a Windows program if it at least runs through Wine) program that is able to detect similar images based on *visual* similarities instead of file contents?  Or even better, does GIMP or another pre-installed program have that capability?

I'm thinking of something like [this]("http://download.cnet.com/Awesome-Duplicate-Photo-Finder/3000-2193_4-75206819.html"), although I don't really trust that program (I don't like CNET in general), plus it's not for Linux.

---

### Post by quirino77 on 2012-09-30
Try Visipics (for Windows), using Wine.

---

### Post by kayosiii on 2012-10-04
Digikam has this function

---

### Post by quirino77 on 2012-10-06
Yes. I tried digikam, but for me visipic is easier. Visipics is just to find duplicate photos. Digikam do lots of things. So visipics can be easier.
Maybe i have to get used to digikam. But anyway, visipics is an option.
Visipics have an "auto seletc" that deletes all the duplicate image but one. I also find easier to mark pictures i want to delete on visipics. Maybe there is a easy way on digikam but i dont know.


Do you have some tips about digikam?
Do you know how can i auto select duplicated pictures?

---

### Post by marioluigi123 on 2012-10-06
Forget all the other suggestions - download Geeqie. You should be able to apt-get or install from Synaptic or Software Center.

Once you open the program, you can press D to bring up a duplicate finder. Change the comparison field to "Similarity" and add files/folders to the window (drag & drop is easiest).

The app will process the photos first to get the similarity comparison data so the first run will take longer; geeqie, however, saves this info so further runs on the same folder will be faster as only newly added files need to be parsed.

---

### Post by cjoleann on 2012-10-07
> **marioluigi123 said:**
> Forget all the other suggestions - download Geeqie. You should be able to apt-get or install from Synaptic or Software Center.

Once you open the program, you can press D to bring up a duplicate finder. Change the comparison field to "Similarity" and add files/folders to the window (drag & drop is easiest).

The app will process the photos first to get the similarity comparison data so the first run will take longer; geeqie, however, saves this info so further runs on the same folder will be faster as only newly added files need to be parsed.

I agree!

---

### Post by Stonecold1995 on 2012-10-07
I found two programs that better fit my needs.  They're both for Windows, but they run flawlessly through Wine.  The first one is called [Double Killer]("http://www.bigbangenterprises.de/en/doublekiller/").  It finds duplicates by comparing CRC32 sums and file size (this one only finds exact duplicates, but it's quite fast as it can scan more than 2000 pictures in under 5 seconds), and one called [Awesome Duplicate Photo Finder]("http://www.duplicate-finder.com/photo.html") that is much slower (it took over 7 minutes to scan the same 2000+ images) but will find images that are similar, if not perfectly identical.

---

### Post by marioluigi123 on 2012-10-07
> **Stonecold1995 said:**
> I found two programs that better fit my needs.  They're both for Windows, but they run flawlessly through Wine.  The first one is called [Double Killer]("http://www.bigbangenterprises.de/en/doublekiller/").  It finds duplicates by comparing CRC32 sums and file size (this one only finds exact duplicates, but it's quite fast as it can scan more than 2000 pictures in under 5 seconds), and one called [Awesome Duplicate Photo Finder]("http://www.duplicate-finder.com/photo.html") that is much slower (it took over 7 minutes to scan the same 2000+ images) but will find images that are similar, if not perfectly identical.

Glad that your problem was solved. Geeqie can do the same thing as both of those applications (just changing comparsion to either file size or similarity content), and it's Linux native. Then again, Wine compatibility is usually pretty solid so I'm sure those apps will continue to work in the future.

---

