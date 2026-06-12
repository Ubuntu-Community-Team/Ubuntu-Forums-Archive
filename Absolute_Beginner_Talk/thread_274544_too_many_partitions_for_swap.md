---
title: "too many partitions for swap"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by creigscofield on 2006-10-10
Hello, absolute newbie here. I just got done installing ubuntu on my dell laptop. I use this computer for work and cannot remove win xp, but wanted linux for play.  However I ran into a small snag during install.  The dell came with norton ghost pre-installed and thus already had an 18 gig partition for backup.  I decided that since I have never used ghost I would just remove this partition and use this space for my linux partitions.  However when I ran the partition app it showed 2 additional partitions I never knew about.  Since that makes 4 I could not put in the 256 meg swap partition the installer reccomended.  Will the lack of a swap file reduce my performance greatly?  Also does anyone know what the 2 partitions you cant see in windows are for and whether they can safly be removed?  Any help will be GREATLY appriciated since I know nothing whatsoevevr about linux.

p.s. my setup is;
Pentium M 1.7 GHZ
RAM - 1024 MG DDR2 (speed unknown)
Intel 915gms vidio card

---

### Post by bodhi.zazen on 2006-10-10
You have several options.

One is to use an EXTENDED partition. A disk my have 4 primary partitions or 3 primary partitions and one extended partition.

The extended partition can then have several "logical" partitions within it extending the total number of partitions. Put Ubuntu and swap into the extended partition as 2 logical partitions.

You can do all this via GParted on  the Live Ubuntu CD.

Other option, make and mount a swap file:

```
LANG=en sudo dd if=/dev/zero of=/swap.file bs=1024 count=524
sudo mkswap /swapfile
sudo swapon /swapfile
```

This will make a swap file of 524 MB. If you want larger or smaller, change the count number.

To activate swap on each boot, edit fstab;

```
sudo gedit /etc/fstab
```
 Add this line:> /swapfile  none  swap  sw  0  0
Save and exit gedit.

---

### Post by po0f on 2006-10-10
creigscofield,

You could add a swap file.  Just follow the directions posted [here](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html).  I've never used a swap file, always a swap partition, so I don't know the performance pros/cons of using a swap file over a swap partition.

---

### Post by creigscofield on 2006-10-10
ok I feel a little retarted asking this but what do I do with the text in the "Code:" boxes?  Also can I change a partition from primary to extended without loosing or damaging the data on it? And what size should teh swap be, the page on red hat manuals implies that it should be twice your phisical mem so 2gig rite?

---

### Post by dannyboy79 on 2006-10-10
the code boxes are bascially the exact things you would type into a terminal or command line to do what the person was suggesting you do. you can even copy and paste it right into the terminal. it's a great way for a guru to help a newbie.

---

### Post by mixmaster on 2006-10-10
I think you will find that if you delete your "ghost" partition and then run the Ubuntu install CD and take the option "use largest free space" then it will sort everything out for you.

---

### Post by CatKiller on 2006-10-10
> **creigscofield said:**
> ok I feel a little retarted asking this but what do I do with the text in the "Code:" boxes?

Applications -> Accessories -> Terminal.
Just paste the commands in.

> Also can I change a partition from primary to extended without loosing or damaging the data on it?

Not as such. If you've got three primary partitions, you can still create a fourth extended partition, then make logical drives in that partition, and then copy stuff from one of your partitions to one of the logical drives. There is no way to turn a primary partition into an extended partition in one go.

>  And what size should teh swap be, the page on red hat manuals implies that it should be twice your phisical mem so 2gig rite?

Certainly no more than 2 Gigs. That rule of thumb was developed when people had less RAM than is common now. Some non-zero value that's less than 2 Gigs will be fine.

---

### Post by Straevaras on 2006-10-10
If you have two Gigs of System Memory then you don't need to worry about having a Swap partition.

---

### Post by creigscofield on 2006-10-11
Thanx for all the help I just removed my ubuntu part. and reinstalled letting the installer setup the parts. automaticly.  now i have another issue but Ill start a new thread about that.:D

---

