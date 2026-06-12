---
title: "Few little problems with Ubuntu"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Elad on 2007-05-19
Hi All,

After i stuck with the partition step in the installer, finally i success to install Ubuntu.
Now i have few problems:

1. Cant connect to the internet. Im using PPPoE and i do what i need with sudo pppoeconf, i follow the orders and i write my username and password, etc..
And i try to connect some site with Firefox and im not see it.

2. There is a problem with the screen, how i can to adjust the postition exactly on my screen, he is prone to right.

3. Why Ubuntu is so slow?
Intel Pentium 4, 1.5.
Windows XP Pro SP2, Nvidia GeForce FX5200
My PC not so strong and he working fine on WinXP, but i think he will running fast on Ubuntu.
Maybe i need to update my video card driver or something?

4. I have a 80 GB NTFS disk with songs, movies, pictures etc.., from Ubuntu i can to open the files, but i cant to remove them or change things, what i need to do?

Thanks to everybody that help me....!!

---

### Post by icechen1 on 2007-05-19
> **Elad said:**
> Hi All,

After i stuck with the partition step in the installer, finally i success to install Ubuntu.
Now i have few problems:

1. Cant connect to the internet. Im using PPPoE and i do what i need with sudo pppoeconf, i follow the orders and i write my username and password, etc..
And i try to connect some site with Firefox and im not see it.

2. There is a problem with the screen, how i can to adjust the postition exactly on my screen, he is prone to right.

3. Why Ubuntu is so slow?
Intel Pentium 4, 1.5.
Windows XP Pro SP2, Nvidia GeForce FX5200
My PC not so strong and he working fine on WinXP, but i think he will running fast on Ubuntu.
Maybe i need to update my video card driver or something?

4. I have a 80 GB NTFS disk with songs, movies, pictures etc.., from Ubuntu i can to open the files, but i cant to remove them or change things, what i need to do?

Thanks to everybody that help me....!!

3.Did you installed the graphic driver for NVIDIA?
For 4) see [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+support](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+support)

---

### Post by halitech on 2007-05-19
Linux doesn't normally play well with NTFS, my suggestion, if you can, move/copy the fiels to another drive then format with either ext3 (if only using linux) or fat32 (if any windows partition) and then you can mount it and put your files back.

---

### Post by Happy_Man on 2007-05-19
In a terminal (Applications --> Accessories --> Terminal):
```
sudo apt-get install ntfs-3g ntfs-config
``` that fixes ntfs probs...

What kind of slow? General sluggishness, or just not as fluid?

Use your monitor settings to move the screen over to the left a little.

---

### Post by Elad on 2007-05-19
2Happy_Man

I fix the connection to the internet, and the screen, now about the slow i mean when im open picture, its taking a lot of time, why?

And why sometimes is disconnect me automatically from the internet?

---

### Post by Happy_Man on 2007-05-19
How much RAM do you have?

---

