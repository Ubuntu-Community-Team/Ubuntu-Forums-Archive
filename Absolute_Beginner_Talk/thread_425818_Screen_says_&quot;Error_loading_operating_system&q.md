---
title: "Screen says &quot;Error loading operating system&quot;"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by fallenvee on 2007-04-27
please help. I've followed the instructions on a dual boot installation video by two guys, i know i've followed the instructions closely, but screen still says "Error loading operating system" after i've installed Ubuntu. i've configured my bios to boot from cd then hdd, what else do i need to do? thanks in advance.

---

### Post by fallenvee on 2007-04-27
another thing...i'm installing server edition of ubuntu, downloaded today from ubuntu website.

---

### Post by Najand on 2007-04-27
Did you make at least a root partition and a swap for your linux OS?

---

### Post by fallenvee on 2007-04-27
thanks for a reply...well, my hdd is 120 gig, i partitioned it in ubuntu install to 70 gig, made a swap for 512mb (per the instruction video), then made another partition as primary...is that correct?

---

### Post by fallenvee on 2007-04-27
i'm redoing it as we type and post replies...thanks for the help again...

right now...it shows this on my screen

IDE4 master (hdg) - 122.9 GB Maxtor XXXXXX
     #1 primary  70.9 GB    K     ntfs              /media/hdg1
     #2 primary 510.0 MB  F     swap            swap
     #3 primary   51.1 GB  K     ext3             /media/hdg3

what should i do now?? is this correct?? remember, this is after i've already followed the instructions video once already

---

### Post by Najand on 2007-04-27
I don't know which introduction you have used, but if you have formatted an "ext3" partition for root("/") and have selected it to be the root filesystem it must be OK.

---

### Post by Najand on 2007-04-27
Is it a dualboot system? do you have Grub Menu and do you get any grub error number?

---

### Post by fallenvee on 2007-04-27
grub menu installs at the end of it all...when it rebots then the error message appears when it's ready to boot an os

---

### Post by fallenvee on 2007-04-27
and yes it's a dual boot, windows xp pro is already installed

---

### Post by fallenvee on 2007-04-27
i've followed the video twice now...check out the video here..

[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+dual+boot](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+dual+boot)

---

### Post by fallenvee on 2007-04-27
any luck with some help Najand??

---

### Post by Najand on 2007-04-27
When it reboots are you able to select Windows?

---

### Post by fallenvee on 2007-04-27
i am not able to boot to windows at all, it's like as if no operating system exists...though when i re-insert the cd in and do the process all over again...when it asks if you want to install the grub, it says at the top that it was able to find ubuntu and windows xp, do you want to install grub?...i ofcourse say yes, take out the cd and restarts...then the error message appears, no screen for me to select any OS...

man, what could be the problem?? could it be my bios??

---

### Post by Najand on 2007-04-27
Yep. Can you disable other booting other medias option in your BIOS Setting and try to boot?

---

### Post by fallenvee on 2007-04-28
you know what...before i do that, do u think it could be that on this screen where i'm partitioning the hdd for ubuntu, shown below

IDE4 master (hdg) - 122.9 GB Maxtor XXXXXX
#1 primary 70.9 GB K ntfs /media/hdg1 <----------------i just found that the "bootable flag" was turned OFF
#2 primary 510.0 MB F swap swap
#3 primary 51.1 GB K ext3 /media/hdg3


could that be an issue???

---

### Post by fallenvee on 2007-04-28
and i've tried disabling all boot devices except for the hdd, it still says same, error loading operating system...dammit..could it be disk?..i've verified it TWICE !!

man..what else can i do now?

---

### Post by Najand on 2007-04-28
> **fallenvee said:**
> you know what...before i do that, do u think it could be that on this screen where i'm partitioning the hdd for ubuntu, shown below

IDE4 master (hdg) - 122.9 GB Maxtor XXXXXX
#1 primary 70.9 GB K ntfs /media/hdg1 <----------------i just found that the "bootable flag" was turned OFF
#2 primary 510.0 MB F swap swap
#3 primary 51.1 GB K ext3 /media/hdg3


could that be an issue???

That make sense.  Did you select the boot flag when installing? Anyway how many IDE hard disks do you have?

---

### Post by fallenvee on 2007-04-28
i have primary ide hdd = 1
then secondary raid configuration = 1 hdd

is the secondary effecting the install??

also, i've just did another install, i've deleted partitions, started from scratch, turned on "bootable flag" ON for the 1st partition, then second line is the swap for 512MB, then 3rd line for 77 GB which i also turned "bootable flag" ON...

this still gets me the same results...error loading operating system

is this how it should be??

---

### Post by fallenvee on 2007-04-28
i hate this, and i appreciate all ur help and time...

i'm just going to insert disk...do another install...

this time, i am going to delete all partitiions..and do a guided install where it partitions the hdd's for me...i'm not doing a manual partition anymore..lets see how this goes...i'm in the process right now...

---

### Post by fallenvee on 2007-04-28
NOPE.....same result...i'm close to quitting..

---

### Post by fallenvee on 2007-04-28
i know there's a recover windows feature...is there anyway u know of, that i can boot to windows now..??

---

### Post by mactechy on 2007-04-28
try the option of "repair this system"

---

### Post by Najand on 2007-04-28
Use Super Grub Disk:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

