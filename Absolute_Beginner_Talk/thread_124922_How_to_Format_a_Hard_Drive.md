---
title: "How to Format a Hard Drive"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by bijan1832 on 2006-02-02
I currently have a clean 80gb hard drive. During the Ubuntu install process I decided that I wanted to partition 20gb for the ubuntu OS. Now when I look in my disk manager is says that the remaining 60gb is not formatted and so I cannot use it. How can I format that remaining 60gb?

---

### Post by carlosqueso on 2006-02-02
You'll have to use a partitioning tool like gparted.  type ```
sudo apt-get install gparted
```  you will probably have to type "gparted" at the run programs prompt or a terminal to get it to run.   After that, you should be able to select the free space and format it a number of ways.  If you are going to use it to share files with a windows OS, you should format it FAT32, if you are only going to use a *nix distro on it, format it ext3 or ReiserFS.  If you need help mounting it afterward, post back.

---

### Post by bijan1832 on 2006-02-03
[QUOTE=carlosqueso]You'll have to use a partitioning tool like gparted.  type ```
sudo apt-get install gparted
```  you will probably have to type "gparted" at the run programs prompt or a terminal to get it to run.   After that, you should be able to select the free space and format it a number of ways.  If you are going to use it to share files with a windows OS, you should format it FAT32, if you are only going to use a *nix distro on it, format it ext3 or ReiserFS.  If you need help mounting it afterward, post back.[/QUOTE]

What is the difference between ext3 and ResierFS?

---

### Post by carlosqueso on 2006-02-03
I've only ever used the two ext file systems but [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems) that link may help you.

---

