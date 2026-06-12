---
title: "Gparted problems &quot;unable to find mount point&quot;"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-06-19
When I installed Feisty I set it up to dual boot XP. I underestimated the size I would need for my Linux partition so I have tried to resize it with Gparted from the live CD but I get an error saying something like "please check the disk for errors" and can't carry out the operations.

 I have checked for disk errors and bad sectors in XP and as far as I can see there are none. When looking at my HD in Gparted I have two flags on my HD partitions saying unable to find mountpoint. I don't understand what this means, how owuld I go about fixing it and also any idea if it is stopping me resizing the partitons?

[IMG]http://i54.photobucket.com/albums/g87/dpurdu/temp/Screenshot1.png[/IMG]

Thanks alot!

---

### Post by ggaaron on 2007-06-19
Are this discs unmounted? Because there is this padlock no your screenshot... Gparted can't operate on mounted filesystems. And if you want to really do it right, don't use ubuntu... Maybe it is an easy system, but sometimes too easy, mine automounted discs every time gparted finished an operation, so listing operations to do didn't work. You can use [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) instead. It sometimes has problems with starting X, then mount your partition, copy /etc/X11/xorg.conf from your partition to livecd's filesystem, unmount partition and you can alter your partitions as you like=)

---

### Post by tabithaboof on 2007-06-19
Thanks alot but, As far as I can see I would use GNU parted? Based on the table here

[http://www.gnu.org/software/parted/features.shtml](http://www.gnu.org/software/parted/features.shtml)

It doesnt seem to work with NTFS?

---

### Post by ggaaron on 2007-06-19
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

There is even a liveCD.

---

### Post by psusi on 2007-06-19
You can just run (g/qt)parted from the (u/ku)buntu livecd.

---

### Post by tabithaboof on 2007-06-19
Sorry but as I said in my initial post

> I have tried to resize it with Gparted from the live CD

But it gives me the above result. I am aware that I cant resize partitions from within Ubuntu.

---

### Post by molly_001 on 2007-06-20
Is your computer an OEM machine?  Such as a Dell laptop or desktop?

---

### Post by meep_meep on 2007-06-20
Note: I've only been using linux for a week


My Gparted couldn't find the mount point for my drive after messed around with '/etc/fstab' and I had a backup of fstab and copied it into the current file and then it worked fine.

Get someone else to check this before you do anything....

meep

---

### Post by tabithaboof on 2007-06-20
My PC is an IBM r50e thinkpad. Also I havent touched fstab at all since I started using Ubuntu as all my drives seem to mount fine. I didn't have any problems till I tried to resize the partitions

---

### Post by southernman on 2007-06-20
As suggested already, use the systemrescue live cd or the gparted live cd. You'll have better results as they don't mount any or your hdd/partitions.

---

