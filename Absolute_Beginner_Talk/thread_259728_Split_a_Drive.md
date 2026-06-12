---
title: "Split a Drive"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by bri_06 on 2006-09-17
I installed ubuntu on a 30GB HD, but I would like it split in 2 drives.

1. Main Drive (10GB for OS/Installed Software)
2. Storage Drive (20GB for my junk)

Thanks

---

### Post by comppsyco on 2006-09-17
The program that you want to use is called gparted. To get it, type into the terminal:
```
sudo aptitude update
sudo aptitude install gparted
```
Next type ```
sudo gparted
```
Now the application gparted should come up. Right click your partition. There should be an option to resize your partition. Resize it to 10GB. Then right click on the empty space that's created and select "Make new partition"
Format your new partition probably with ext3, and let her rip.

[https://help.ubuntu.com/community/Au...ountPartitions](https://help.ubuntu.com/community/Au...ountPartitions)

should tell you how to mount it after you're done with that.
Be careful while doing this, as you can lose all your data while messing with partitions, and I'm not in front of a linux box right now, so I'm not sure if these are exactly correct.

---

### Post by bri_06 on 2006-09-17
I right click and it will only show "Unmount or Information"

---

### Post by bodhi.zazen on 2006-09-17
Last time I checked you could not partition a drive that was mounted. This means you will have to partition via a live CD, either Ubuntu live or Gparted live CD.

[Download Gparted live CD](http://prdownloads.sourceforge.net/gparted/gparted-livecd-0.3.1-1.iso?use_mirror=jaist)

---

