---
title: "Using Ubuntu"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by shekter on 2007-04-29
Good Day !   To All Forum Members I'M A New User Of Ubuntu Still Did'nt Use The CD Shipped To Me Earlyer Because I've A Brother Who Lives In South Africa  That Told Me There'll Be A New Ubuntu And Reaslly We'll Have It Is It Possible To Run Ubuntu On A New Partition On My HD The New Partition Is Made By Norton Partition Magic So Plwase If It's Possible to run It On the New Partition Until Learning To Work With The Ubuntu Then Only One Will Be On The HD "UBUNTU "That's Sure But As I've Said I ust Learn How To Work With It So Please Waiting Your Reply A.S.A.P Thank You In Advance BY>>>BY>>>

---

### Post by shekter on 2007-04-29
:popcorn:

---

### Post by shekter on 2007-04-29
:guitar:

---

### Post by moephan on 2007-04-29
What addition of Ubuntu do you have? If it is 7.04 (Feisty Fawn), than you have the latest version. If you want to try it without installing anything on your computer, you can run it as a "Live" CD, meaning it will run off of your CD without installing anything on your hard drive.

---

### Post by Happy_Man on 2007-04-29
So, first thing you need to do is to download the .iso of Feisty Fawn 7.04 from [http://ubuntu.com/download](http://ubuntu.com/download). 

Next, you burn the CD using these directions:[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then, boot from the CD and click the Install icon; when it gets to the screen asking you how to partition, click "manually edit partition table" and go forward.

Edit your partitions, making sure to give at least 20-30 GB to Ubuntu, and 1GB of space for a swap partition. The Ubuntu parttion should be formatted as ext3, the swap partition in "swap" format. Then go ahead and install. Voila! One brand-new Ubuntu install, ready to go!

---

### Post by tophatandy on 2007-04-29
To start off, sorry if this isnt your question, I had some difficulty understanding what you wrote. It seems as though you arent native to english.

yes, it is possible to run ubuntu on a new partition, although probably not the one you made with norton. Norton probably made the file system ntfs and not ext3. You should put the new cd in (7.04 if you have it) and use GNOME Partition Editor to change that partition to ext 3.  then just install ubuntu on that partition. Do you have windows installed on the other partition?

---

