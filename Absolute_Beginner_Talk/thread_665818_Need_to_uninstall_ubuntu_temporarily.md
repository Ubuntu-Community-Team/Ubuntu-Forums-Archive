---
title: "Need to uninstall ubuntu temporarily"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by hirou on 2008-01-12
Okay, so I have ubuntu and I am very happy with it and am starting to learn my wayt around all teh differences of using a linux system.

However, I have to needs for a windows install. for gaming and the use of some art software.

My problem is that I need to uninstall ubuntu and replace is with WinXP pro, I have the disk, It's just that when I put it in the tray and reboot *hoping it will boot the windows install process* It goes straight back into grub without seeming to have even considered my disk : S

I need help :(

thanks

---

### Post by maharbA on 2008-01-12
check your BIOS settings. Make sure it's set to boot off of the CD/DVD drive.

---

### Post by hirou on 2008-01-12
HI, thanks for the reply
My CD/DVD drive is second after the floppy drive, would that be the reason?

---

### Post by hirou on 2008-01-12
I have changed the BIOS so that my CD/DVD is first. Still no luck.

---

### Post by armandh on 2008-01-12
try the ubuntu live disk if it comes up then the problem is the windohs disk

---

### Post by hirou on 2008-01-12
Okay, thanks. The livecd is loading fine so I guess it's a bad disk. A friend recommended I try to install win98 then "work my way up" to XP.  Do you know if this will work? I would have to go hunting for the disk is the only reason I ask : P

---

### Post by hirou on 2008-01-12
Okay, I went hunting nd found a Win98 SE install disk "for PCs without windows" pff yeah right.. Anyway that boots fine and I was going to try my friends method but I get an error telling me that windows cannot be install on _my_ system. Is this to do with linux using an ext3 format or something?

---

### Post by MNICY on 2008-01-12
Is there any reason not to dual boot?

---

### Post by hirou on 2008-01-12
I would love to, but I don't have a hard drive with windows installed on it to begin with, hopefully by doing this I can have ubuntu on this drive alongside the "replacement" XP
Unless I am missing a massive point here xD:confused:

---

### Post by MNICY on 2008-01-12
I dont know how well this would work, but would not installing gparted
```
sudo apt-get install gparted
```, creating a new partition, and installing windows on it now work?
Well, the only problem i can see is it might mess up GRUB, (or grub might not reconise it)

When you install Ubuntu after, it reconises your windows installations and creates a link to the bootloader for windows in it.

So, your right. It may be a good idea to reformat the hardrive, install widnows and then load up Ubunut, and used the Manual install to create a new partition and install Ubuntu on that.
Then GRUB will be configured properly :)

---

### Post by hirou on 2008-01-12
Thanks.
If I were to format my harddrive, I know it sounds incredibly nooby, but. I was searching for something to do so earlier and they all seam like "might work"s.
Do you know of one that is good? I don't really want to go down the manual partitioning route : S That's what turned me away from linux last time I had a go

---

### Post by hirou on 2008-01-12
I just tried another option on the Win98 disk and i got as far as telling it to remove files from the drive, then I get a blue screen headed Windows 98 install and various options at the bottom... Hell, it brought back painful memories of "tHe BlUe ScReEn Of DeAtH" nevertheless, I need an install.

---

### Post by MNICY on 2008-01-13
The manual paritioning is actually really easy.
gparted lines it out really nicely. 

And when you install ubuntu, you just select the partiton you want to install it on (change it from dev/sda1 or 2 or whatever to "/").

There would be how-to's on the internet, so i suggest you find one and at least read about it. :)

---

### Post by Limpan on 2008-01-13
> **hirou said:**
> A friend recommended I try to install win98 then "work my way up" to XP.

That's not the solution to a faulty Win XP install disk. It's just stupid.

---

### Post by hirou on 2008-01-13
Okay thanks, I'll find out a bit about gparted  :)

---

### Post by hirou on 2008-01-13
Okay it does actually seem very simple, thanks. Do I need to delete partitions to format the disk?

---

### Post by MNICY on 2008-01-13
well, to format the WHOLE disk you need to delete the partitions, but to format a single partition, you can leave the other ones alone.

You can even resize a large partition to create two (one partition, and some free space) then you can make the free space into a new partition.

---

### Post by Sef on 2008-01-14
> I dont know how well this would work, but would not installing gparted

It won't if the hard drive is mounted (in use.)  I would instead download [GParted]("http://gparted-livecd.tuxfamily.org/") and use that to partition the hard drive.

---

### Post by hirou on 2008-01-14
Thankyou, I used gparted to create a big enough partition. In the end I used a Home Edition disk, it's not as good, but the Pro wasn't working. Now I have WinXP HE and Ubuntu 7.04. 
Thanks for all your help  :)

---

