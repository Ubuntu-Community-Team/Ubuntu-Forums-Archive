---
title: "Partition Help - GParted"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by VeryKoreySorry on 2007-08-16
Hello, I am looking to install Ubuntu and to keep my Windows installation as well. I have a few questions:

(I am using [this guide]("https://help.ubuntu.com/community/WindowsDualBoot"))
1. If, in the future, I decide to trash my windows installation and just keep Ubuntu, will I easily be able to delete the windows partitions and add space to my ubuntu partition?

2. "Create a swap partition of at least your amount of RAM (if you don't know, 2000 MB is a good value).
Create a partition for your Ubuntu installation, at least 10 GB."
What filesystem should the swap partition be? Should it be primary? Same questions for the ubuntu installation partition, as well.

That is all for now. Thank you for your help.

---

### Post by amazingtaters on 2007-08-16
1. I was dual booting. Trashing my vista partition was horrible, because I did not want to reformat the entire dics, just the one partition. It was a pain, just really horrible. Now, if I had just backed everything up and reinstalled, it would have been much easier. So take that into consideration.

2. The swap will be made in the installer, it will let you select the size and automatically format it correctly. As far as the ubuntu partition, I'd counsel ext3.

---

### Post by Bachstelze on 2007-08-16
1. Not easily, but you will. Heavy partitioning tasks like those are always a bit complex.

2. The swap partition has it's own filesystem. Your partitions can be Primary or Logical ones, as you wish. When you install GRUB in the MBR, it doesn't matter.

---

### Post by overdrank on 2007-08-16
> **VeryKoreySorry said:**
> Hello, I am looking to install Ubuntu and to keep my Windows installation as well. I have a few questions:

(I am using [this guide]("https://help.ubuntu.com/community/WindowsDualBoot"))
1. If, in the future, I decide to trash my windows installation and just keep Ubuntu, will I easily be able to delete the windows partitions and add space to my ubuntu partition?

2. "Create a swap partition of at least your amount of RAM (if you don't know, 2000 MB is a good value).
Create a partition for your Ubuntu installation, at least 10 GB."
What filesystem should the swap partition be? Should it be primary? Same questions for the ubuntu installation partition, as well.

That is all for now. Thank you for your help.

Hi and welcome, Yes you will be able to delete the windows partition in the future and then format it for ubuntu to use. And the swap will be just that swap, and it is recommended to be at least twice your memory. Good luck and enjoy! :popcorn:

---

### Post by VeryKoreySorry on 2007-08-16
Thank you for your help everybody :)

---

### Post by mikewhatever on 2007-08-16
> **VeryKoreySorry said:**
> Hello, I am looking to install Ubuntu and to keep my Windows installation as well. I have a few questions:

(I am using [this guide]("https://help.ubuntu.com/community/WindowsDualBoot"))
1. If, in the future, I decide to trash my windows installation and just keep Ubuntu, will I easily be able to delete the windows partitions and add space to my ubuntu partition?

2. "Create a swap partition of at least your amount of RAM (if you don't know, 2000 MB is a good value).
Create a partition for your Ubuntu installation, at least 10 GB."
What filesystem should the swap partition be? Should it be primary? Same questions for the ubuntu installation partition, as well.

That is all for now. Thank you for your help.
1. yes, if is fairly easy to manage partitions using Ubuntu live cd or gparted, or any similar one.
2. 1-2 BG is a good size for swap. It does not matter whether primary or logical, and the file system is none, that is, there isn't one.
Ubuntu partition has ext3 file system.

---

