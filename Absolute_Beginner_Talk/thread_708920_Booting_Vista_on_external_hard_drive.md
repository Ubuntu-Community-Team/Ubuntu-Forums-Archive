---
title: "Booting Vista on external hard drive"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by QuizasQuizas on 2008-02-26
Hello! I'm actually using Vista right now (ick) on the family PC, but I plan to purchase a laptop before the end of this summer and install Ubuntu. Unfortunately, I'm stuck with Windows until then, as my family would likely flip out if I tried dual booting on this computer. In the meantime, I *would *invest in an external hard drive to stave off curiosity, but that would take a chunk out of the "laptop fund" (and that would just be time-inefficient).

Anywho, jumping into the future, I'm looking at portable external hard drives with the intent to run Vista on said hard drive independently of an Ubuntu-based laptop. Currently, I've got my eye on a Western Digital Passport, but I'm not yet certain that any of this would be plausible.

Does anyone know if it would be possible to format the Passport on a machine running Vista, then access it primarily through a Linux machine? If not, would anyone happen to have any recommendations of external hard drives which might support this craziness? 
Thanks for any input, and please tell me if I'm just being ridiculous!

---

### Post by northern lights on 2008-02-26
As far as external hard drives in general are concerned, I'm very happy with the recent Western Digital MyBook series - might look flashy, but is very robust (fell down my basement staircase, survived).

Anyhow, you could boot Vista off of an external harddrive, but it be way easier (for once Windows wants to reside on the first harddrive, so you'd have to remap) and faster to partition the laptop's drive into three (ext3 & swap (if you know what a pagefile in windows is, that's roughly the swappartition) for linux, NTFS filesystem for Windows).

Modern laptops come with at least 80 gigs of space - 30gig Ubuntu, 1gig swap, 44gig Vista, for instance (80gig HDD, are not 80gig...).

---

### Post by chris.a.barker on 2008-02-26
To be perfectly honest on this subject, unless you purchase an eSATA drive you are going to have some serious performance issues running Vista on an external drive. Another problem to consider is that not all BIOSs support external volume booting. In addition to that limitation I am not sure that Vista can even be installed on an external drive. The bottom line is go with nothern lights' recommendation and simply format the external drive using a filesystem readable by both operating systems. This way you can store the media that would traditionally take up alot of space (movies, photos, music) separate from the operating systems. Thus you should have absolutely no space issues. And for a last benefit, if your computer goes haywire you already have your media backed up. Sounds like a win-win to me.

Have a good day :)

---

### Post by QuizasQuizas on 2008-02-26
Thanks!

---

