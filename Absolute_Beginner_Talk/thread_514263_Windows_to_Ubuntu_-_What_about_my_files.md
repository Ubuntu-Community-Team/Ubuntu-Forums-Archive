---
title: "Windows to Ubuntu - What about my files?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by jamieh on 2007-07-31
I am going from Windows to Ubuntu, but the migration assistant isn't Vista compatible, does anyone know of a free online storage place that is both Windows and Linux compatible so I can store my files while I install Ubuntu? I need to transfer my documents. music, and videos.
And also, has anyone successfully used Lego Mindstorms NXT under CrossOver or Wine? Or does Lego have a Linux version on their website?
Thanks.

---

### Post by jba6511 on 2007-07-31
create another partition (which you should have anyways) for data. Place all of your important files here. Then, once you have installed Ubuntu, you can use NTFS-3G, which will allow you to read and write to that partition, allowing you to access your stuff.

So basically, 1 partition for data, 1 for ubuntu
or if you are dual booting
1 for vista, 1 for ubuntu, 1 for data.

In case you are not aware, by keeping a seperate partition for data, if you ever need to reinstall an OS, such as windows or ubuntu, your data will remain, and only the partition holding the OS will be changed.

---

### Post by jamieh on 2007-07-31
If I edit partitions with Gparted, what is the risk of my Vista being unusable, so I can't get my files?

---

### Post by st33med on 2007-07-31
The only risk is if you shrink the ntfs partition to where you are deleting files. Check first to see how much memory you are using.

---

### Post by ajgreeny on 2007-07-31
And make sure you defrag two or three times at least, preferably having temporarily deactivated your windows virtual memory and doing it in safe mode, before doing anything to your windows partition with gparted.  Otherwise gparted is just great!

---

### Post by hessiess on 2007-07-31
buy a usb hard drive and put the files on that, if you modify the partition table, there is alwase a risk of curupting somthing. or burn it to cd/dvd

---

### Post by henriette_holm on 2007-07-31
Please, please do a backup of some sort before you start changing the size of partitions. Like someone else suggested - usb hard drives are really cheap. Get one, and throw all your stuff on to that.

/Henriette

---

### Post by gpilkay on 2007-07-31
I'd second the USB/DVD solution.  That's what I did, I haven't found ANYTHING that's compatible with Vista (including Vista itself...)

One thing, though, I'd make two copies of the backup CD/DVD, just to be safe.  Files can be corrupted, disks scratched, USB keys stuck near the fridge magnets, etc.  On-line backup's ok but for large files it  can lead to trouble with errors, just like a giant ISO file.

---

### Post by jba6511 on 2007-07-31
you could also create the partition is vista using disk manager or third part software like partition magic. The when installing ubuntu just select to install to that partition if you are not comfortable doing so with gparted. Like everyone else said, make sure to backup any info you do not want to loose just in cause the worst happens.

---

### Post by TKR101010 on 2007-08-01
I used WinRar to archive all the files I wanted to transfer from Windows to Ubuntu. It has a feature so that you can break up the archive into segments. I told it to break it up into 700Mb segments and then burned them to CDs (which unfortunately took like 34 cds). Then I installed rar in Ubuntu and used that to unzip the archives to my home directory.

---

