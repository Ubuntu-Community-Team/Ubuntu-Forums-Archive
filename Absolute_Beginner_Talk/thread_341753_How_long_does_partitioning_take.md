---
title: "How long does partitioning take?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by tidge87 on 2007-01-19
How long does it usually take to partition a drive?

My comp has XP installed and I'm trying to resize my 120GB drive (52%)

and its taking more than 30 minutes.. is this normal or has something gone wrong?

My XP system only has about 1GB of stuff on it. :???: 

Thanks

---

### Post by Kobalt on 2007-01-19
Hello,

Did you defragment your disk before partitioning it ? I know it sounds crazy but even with only 1Go of datas, Windows could have place some files after the 52% space you want to set for Ubuntu... And these would be lost. 
FOr your partitioning, what tools are you using ? With Gparted from the LiveCD it took me like 10secs to partition a same capacity hard drive....

---

### Post by tidge87 on 2007-01-19
> **Kobalt said:**
> Hello,

Did you defragment your disk before partitioning it ? I know it sounds crazy but even with only 1Go of datas, Windows could have place some files after the 52% space you want to set for Ubuntu... And these would be lost. 
FOr your partitioning, what tools are you using ? With Gparted from the LiveCD it took me like 10secs to partition a same capacity hard drive....

I dont really mind if some of the data is lost on XP.

I just went through the standard Ubuntu install and went with option 1 on partitioning and its not working.

---

### Post by Kobalt on 2007-01-19
> ...went with option 1 on partitioning and its not working.
What do you mean then : is it taking a long time (a complete install process takes usually about 30min, depending on your system speed) ? Is it stopping/crashing ? Do you get an error message ?

---

### Post by tidge87 on 2007-01-19
> **Kobalt said:**
> What do you mean then : is it taking a long time (a complete install process takes usually about 30min, depending on your system speed) ? Is it stopping/crashing ? Do you get an error message ?

My system is fairly new...

I chose Resize SCSI1 (0,0,0) partition #1 (sda) and use free space.

It just shows the loading circle thing and its been doing it for about an hour.

Also tried using Gparted but I got confused because i resized the XP partition then it says unallocated space for the rest and it doesnt let me put Ubuntu in there.

---

### Post by housam on 2007-01-19
Welcom to ubuntu.
I prefer to manage the partitioning manually to put every thing under control. You have to keep windows in a separate partition and create another 3 partitions for ubuntu.
Using the partitioning tool Gparted you can devide the unallocated space to the following partitions as an examples:
- 10 - 15G ext3 ( / ) for root
- 1G swap ( useless if more than 1G , you may not use it ever if you have 1G RAM or more.)
- 10-15 Gb is ext3 for /home
Remember that you can only create 4 primary partitions on your HDD. if you need more partitions you can change the 4th primary partition to be an extended one. and that one can be devided to what ever you want.
After creating the partitions you can go for the installation.

---

### Post by linux_believer on 2007-01-25
I had a similar issue. Dell Inspiron 8600 with Windows installed. I was not given the option to resize the partition only to install on the entire disk or manual partitioning. I didn't want to mess around with manual so what I did was:
wipe the entire drive, even deleting the dell driver partition
installed fresh copy of windows

I was now presented with the option to resize the partition and I proceed thats where it stops. It says its resizing the partition and can sit on that screen for a couple of hours. I cancel it and it is as if Ubuntu was doing nothing but sit there. I tried this several times with no success. [B]Any ideas?
[/B]

---

### Post by linux_believer on 2007-01-25
Ttt

---

### Post by zekopeko on 2007-01-25
try the manual partitioning or download gparted liveCD (30mb). 

manual partitioning is simple and you have more control.

for partitioning methods use the info from post #6. 
only thing i suggest is to give home the remaining space after you give the root ('/') and the swap space as suggested in post #6

P.S. my partitions

/ - 12 GB
swap - 0.5 GB
/home - 37 GB 

...under a minute to format

---

