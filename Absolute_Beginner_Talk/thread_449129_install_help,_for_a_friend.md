---
title: "install help, for a friend"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by drowner on 2007-05-19
Hey, i am trying to switch a friend over to ubuntu

We initially got an error msg on the live install, and a quick search here showed the best option was to install kubuntu, install the gdesktop and remove the kdesltop. No problems.

So, we booted Kubuntu, went to desktop, but was very slow.

Clicked on install, and it takes forever, and eventually hangs.

I remember when I installed Ubuntu (badger) there was not the graphical interface (i understand this has since changed) and its possibly that his computer is struggling with the load.

Any thoughts on how to get it going smoothly?



System specs:

Acer extensor
256MB RAM
Intel Celeron M360 1.4GHz
1mb L2 cache

---

### Post by Bachstelze on 2007-05-19
The "old school" command line installer (the one you used in Breezy) still exists, it's on the "Alternate" CDs.

---

### Post by lazyart on 2007-05-19
I would try the alternate install CD.  It's text based but it should get you rolling.

---

### Post by yabbadabbadont on 2007-05-19
Your best bet would be to download and use one of the alternate installation cd's.  They are the recommended ones to use for low memory systems.  You may want to use Xubuntu as it seems to handle resource challenged systems better than the others.

Edit: I am forever doomed to be too slow.  :lol:  Looks like "operation overkill" is complete.

---

### Post by drowner on 2007-05-19
Oh by the way....

He mentioned to me that he had 2 hard drives.... he didn't know if it was 2x20 gig physical HD's, or 1 x 40g partitioned into 2

I booted DamnSmallLinux (genius OS, absolute genius), and it showed me that he, infact, had partitions on the one disk....

First: A 'Compaq Diagnostics' partition
Second: The NTFS partition (bootable)
Then: FAT32 formatted storgage

Is that diagnostic partition going to cause trouble? LIke, will GRUB write over it or something?

---

### Post by drowner on 2007-05-20
For completenesses sake:

1. The alternate CD worked a treat, and Kubuntu installed fine

2. The diagnostic partition wasn't an issue at all, although kubuntu managed t mount it as a fat32 partition LOL (we commented it out of the fstab)

I had never used kubuntu before so i was pleased to be able to see it. I prefer gnome i think, but only because it reminds me less of windows ;)

---

### Post by zvacet on 2007-05-20
If you want Gnome you have it on your CD

```
sudo aptitude update
```
```
sudo apt-cdrom add
```
```
sudo aptitude install ubuntu-desktop
```

or you can look on this page

[http://www.psychocats.net/ubuntu/gnome]("http://www.psychocats.net/ubuntu/gnome")

---

### Post by zorog on 2007-05-20
Hi all I spent all weekend trying to get Feisty Fawn (7.04) standard CD up and running on my thinkpad r30 laptop with 256mb of ram, the install was so very slow, after much playing around, burning new CDs, swapping out HDD's ect...

I almost gave up..

until I tried one last time  this time I found a post about enabling a swap file on the hard drive for the live CD to use ([http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html](http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html))
and bingo the install was snappy and quick! so here's a quick run down of what I did...

Firstly I let the live CD boot up

then using **Ctrl+Alt+F1** I brought up a  console and entered to following commands:

I used fdisk to delete my old windows XP partition and created a new empty partition I'm lazy so I just used the whole disk  for my new partition as the Install was going to overwrite it anyway
**sudo fdisk /dev/hda**

then I used my new blank partition for a swap
**sudo mkswap /dev/hda1**  
**sudo swapon /dev/hda1 **

the re entered  graphical mode by pressing **Ctrl + Alt +F7**
and then used the install icon on the desktop and all was and still is sweet

I hope this helps
Have Fun,
Simon

---

### Post by reagos on 2007-05-21
Hey this sounded like a good idea... my 256 RAM was too slow for graphical install too (tried every Ubuntu disk out there)...I deleted all the xp partition through fdisk and the sudo mkswap worked well, but swapon failed with error message:
 "[17180636.97600] Out of Memory: Killed process 6260 (nautilus)." 

The command-line is now completely unresponsive; too paranoid to reboot since there's nothing left on the hard drive. Any ideas?

---

### Post by reagos on 2007-05-21
also, i have 80GB of hard drive

---

### Post by yabbadabbadont on 2007-05-21
Reboot using the CD again.  Run fdisk on the drive.  Delete all partitions.  Create a single primary partition that is only 1 or 2 gigabytes.  Now use the 't' command (type) to change the type of that partition to 82 (swap).  Save your changes.  Reboot using the CD if fdisk tells you that you need to.  Run mkswap on that partition and then try to activate it with swapon.

---

### Post by reagos on 2007-05-21
mount -a!!! zorog, i love you thank you

---

### Post by zorog on 2007-05-22
probably spacked out because you partition was to big.. my bad.. a quick google tells me that the max possible swap size for x86 is 2gb so try making your partition smaller than that.

512mb is overkill for what you need(128mb should do).

good luck,
Simon.

---

