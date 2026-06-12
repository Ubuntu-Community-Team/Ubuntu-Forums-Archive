---
title: "Resizing my partitions"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-11-21
Okay . . .I'm slowly making progress in understanding how Linux works. ~LOL~ This is very little comfort in regards to how my computer works. ~LOL~ I installed Ubuntu onto my 40 gig drive, only to find out that it repartitioned  the drive and placed itself in a VERY small portion . . .here's a screenshot of GParted to elaborate my problem . . .from this view, can anyone tell me how to resize my drive to allow Ubuntu to have a larger space? I'm in LiveCD mode as we speak, so I'm ready to kick bum and chew bubble gum. ~LOL~

---

### Post by meng on 2006-11-21
No, Ubuntu is on that huge 36GB partition, also called /dev/hdb1. The linux swap partition is on the small partition.

---

### Post by CheshireMac on 2006-11-21
Okay . . .but why have I run out of space? When I was installing from Automatix, it told me the device was out of room.

---

### Post by meng on 2006-11-21
I don't know why that should be. GParted clearly indicates that you have plenty of room left. Perhaps it's an Automatix error.

---

### Post by CheshireMac on 2006-11-21
So all is as it should be in the land of lollipops . . .groovy . . .try Automatix again?

---

### Post by meng on 2006-11-21
I read your other thread, and I can't figure out why df -h is showing / as a unionfs with all space allocated. That should only be the case if you were running from a LiveCD at the time. I don't think one can install Automatix while running the LiveCD ... was that what you were doing?????

---

### Post by CheshireMac on 2006-11-21
I can't recall now if I posted that printout in Live mode or not . . .so what I'll do is boot up the OS on my comp instead of in Live, and give you a readout from there . . .Arg! ~LOL~ Looks like another four pots of java for Mac tonight. ~LOL~

---

### Post by meng on 2006-11-21
My advice is not to screw with your system unless you're well-rested. To each his own though ...

---

### Post by CheshireMac on 2006-11-21
Sleep is for the weak, and I'm more alert when I'm tweaked. ~LOL~ Here's my readout in normal mode, and I'd like to thank you for the time you're spending with this problem, Meng. I appreciate it.
mac@mac-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              36G  1.9G   32G   6% /
varrun                252M   84K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  112K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-26-386/volatile
/dev/hdd               77M   77M     0 100% /media/cdrecorder

---

### Post by meng on 2006-11-21
Yeah the top line is what I would have expected running normally. Your /dev/hdb1 is mounted as the root filesystem / and has 32G available, only 1.9G used. If Automatix tells you there's not enough space, it's a damned liar. I don't want to badmouth Automatix here, but I find that I can install what I need without using it.

---

### Post by CheshireMac on 2006-11-21
Groovy . . .so all is well, or should be by the readout, anyhow . . .okay. Thanks so much, again. :)

---

