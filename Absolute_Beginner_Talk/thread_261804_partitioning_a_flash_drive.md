---
title: "partitioning a flash drive?"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by notjohn101 on 2006-09-20
hey i wanna partition my flash drive...half for windows have for linux

but the disk managent tool wount let me add a sencond partition

[[IMG]http://img55.imageshack.us/img55/8933/screenshotdp3.th.png[/IMG]](http://img55.imageshack.us/my.php?image=screenshotdp3.png)

---

### Post by comppsyco on 2006-09-20
Why do you need to do this? If you format it as FAT32 (which I don't know if you can do, I don't know much about flash memory formats), you should be able to share between them. But I could be wrong, as perhaps HDs and Flash drives are treated diferently.

---

### Post by robins_web on 2006-09-20
Do you want to use the drive for programs, or just for data? If all you want to use it for is storing data, you can use gparted to repartition the entire drive as FAT32. That way, both Windows and Linux (regardless of distribution) can read it.

Otherwise, if you want it for programs, gparted is still the way to go. Partition  half of it as FAT32, and half as EXT3.

I have a 512Mb flash dfrive from Lexar that I set up as FAT32 via gparted, and it works like a charm. I can work on files at home, save them to the flash drive, then work on them at work as well.

And now, for something completely different: you can load several Windows versions of open-source software such as AbiWord, OpenOffice.org, Firefox, Thunderbird, GIMP onto a flash drive and then run them from that drive. I do it all the time when I need to use somebody else's computer, but don't want to have to install the program I want if they don't have it. I simply plug in my flash drive and run the program from there. Best of all, it leaves no tracks on the other computer. More information is here: [http://portableapps.com/](http://portableapps.com/)

---

### Post by notjohn101 on 2006-09-20
well actully...i just wanted to experiment

---

