---
title: "Partition help required (GParted)"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-05-15
hey guys, long time no pester. 

seems i`ve found another OS i wanna try which seems to suit my audio/midi requirements....Musix is the name and it seems pretty kool from what i`ve seen on the live disk. 

now my problem lies with resizing a 117gig partition i have set up. i wanna free up about 17 gig to install Musix to my hd to avoid any sample loss etc. i`m trying to use GParted for this. i unmount the drive, click the desired partition and select resize. i get the sizes right and click ok followed by apply and then ok (or something) to start the partEd on it`s merry way to resizing my partition, about 20 minutes later the 'operations pending' window disappears and no changes have been made. this is becoming quite time comsuming, does anyone know why ths is happening or if i`m doing something wrong, i cant for the life of me work out why it aint working.

any help would be greatly appreciated, i.e. any other suggestions as to how i could resize the partition (tried QTParted but that didnt wanna give me the 'resize' option...)


cheers 

DK

EDIT: Thought i`d point out, i aint ditching Ubuntu! just re-read my post and figured it sounded like i was asking for advice on how to scrub the breezy one ;) , not me, just a dual boot!

---

### Post by Sef on 2006-05-15
Three things I can think of are 

1) Bad CD - reburn

2) Bad Burn - reburn

3) Bad Download - Did you md5sum?

---

### Post by DiscoKiller on 2006-05-15
i`m not using the live cd

i have run gparted in ubuntu to resize my partition b4. the disk i`m partitioning has nothing but media on it i.e. no programs etc so it should be easy to edit the wee blighter, i`m convinced i`ve done it before because i remember installing windows earlier this year to see if it was good enough to run on a desktop pc and carry out simple tasks without breaking....needless to say i deleted the partition.

is it more likely that i will succeed using the live disk? 

cheers 

DK

---

### Post by Sef on 2006-05-15
If it is mounted, then you can't use GParted in Ubuntu.  You will need a Live CD of Ubuntu, GParted or another partioner.

---

### Post by DiscoKiller on 2006-05-15
i have unmounted the drive beforehand, the option is available to unmount in GParted.

 i also tried using the command sudo umount /media/hda1 b4 i started the partitioner

if i was to edit the fstab to permanently unmount it....i.e. so it didnt mount on boot, would that help?

i`m really stuck as to why this isnt working...

---

### Post by DiscoKiller on 2006-05-15
Thanx for your help anyway Cef, i`ve downloaded the Live CD so i`ll gve it a go with that....take it easy dude


DK

---

### Post by Sef on 2006-05-15
You're welcome.  The Live CD will work well also.

---

### Post by DiscoKiller on 2006-05-17
Thanks again Cef, i now have a working dual boot system with Musix (knoppix variant i think) and ubuntu......now i`m happy!


cheers

DK

---

