---
title: "How to use gparted"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by rbrittner on 2008-03-02
Ok so long story short, my hard drive is messed beyond repair.  I've read to wipe all partitions I need to use my live CD and use gparted.....one problem.  how do you do this?  I've read other posts but all of them talk about once you get gparted going.....my question is how to get it going?

Thanks

---

### Post by loserboy on 2008-03-02
hmm, well if u just want to start gparted,  go to a terminal and type 
> sudo gparted

if you need help formating partitions theres plenty of howtos around that could explain better than me

---

### Post by JoshuaRL on 2008-03-02
I would suggest Parted Magic, its a Live CD.  You should put it in, restart, and boot from the CD drive.

---

### Post by rbrittner on 2008-03-02
> **JoshuaRL said:**
> I would suggest Parted Magic, its a Live CD.  You should put it in, restart, and boot from the CD drive.

ok i guess i'll download it at work tomorrow, i thought there was something on the ubuntu live cd that I could use.  I only have a laptop without a burner (other than the one that is down) so i'll have to do this tomorrow.   Thanks again, you've been lots of help.

Ryan

---

### Post by iris-n on 2008-03-02
There is, gparted. I've always used it without problems.
Just boot on the live CD and System->Administration->gparted (or partition editor, don't know the english name).
It's GUI is pretty straightforward, just select and delete the partitions if you only want to wipe out.

---

### Post by loserboy on 2008-03-02
yep gparted has always worked for me just fine, although recently i was unable to format ntfs partitions, appearently they changed it so u need to install ntfs supposrt or something.

oh heh and the command i gave is wrong i think....  its Gparted or GParted  (case sensitive)

---

