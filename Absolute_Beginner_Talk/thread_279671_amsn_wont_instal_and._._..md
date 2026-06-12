---
title: "amsn wont instal and. . ."
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by mattgaunt on 2006-10-18
Hey every1 i installed dapper and the install didnt work, so i installed edgy and its happy :mrgreen: 

Now i want to install amsn but it comes up jus saying it had dependencies that wont be installed, any1 hav any ideas??](*,) 

I also wanted ask the age old question im sure you guys answer again and again but ive scanned and search the threads and had no luck, how can i get files from my windows hard drive??:-k 

Jus so you all kno, my computer is an AMD 64 machine with 2 IDE hard drives which dual boots Windows xp and ubuntu 6.10

I am a completely new to this and hav no idea what im doin lol, im sure it'll be fun!!!

Thanks guys

---

### Post by bulldog on 2006-10-18
Well know nothing about amsn,but your hdd you can mount.

Did you by anychance unplugged the windows hdd when you installed Ubuntu?

Otherwise they should be visible in /media.

To mount a NTFS partition,```
sudo mkdir /mnt/windows
```
To make a mount point.

To actually mount you have to know how the partition is called,like hda4.

```
sudo mount -t ntfs /dev/??? /mnt/windows
```

---

### Post by PriceChild on 2006-10-18
amsn... You might need to enable extra repositories: [https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

As for getting files off the harddrive: [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

