---
title: "Installation on Macbook"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by cowboydan on 2006-07-13
Hello, I don't know if this is really a beginners question or not.  I personally am a beginner, but what I'm experiencing is that after I install the x86 version of ubuntu on my macbook and then select the option to restart, I get the message 'GRUB loading, please wait...' and I've let it wait for about an hour with nothing happening.  When I do an installation I completely erase the drive in the machine, there are no other partitions on the drive that I have created.  I'd like to start using this software, but I'm hitting a brick wall.

Can anyone help?

---

### Post by skull_leader on 2006-07-13
Does your Macbook have an Intel chip? 

If not, then you should install with the PPC version of Ubuntu.

---

### Post by cowboydan on 2006-07-13
yeah, all macbooks have an intel core duo chip in them.  mine is running at 1.83ghz.

---

### Post by zc923 on 2006-07-13
Correct me if I am wrong, but I believe all Macbooks, including Pro use the intel chip.

EDIT: Looks like someone beat me to it.

---

### Post by chasisaac on 2006-07-13
> **cowboydan said:**
> Hello, I don't know if this is really a beginners question or not.  I personally am a beginner, but what I'm experiencing is that after I install the x86 version of ubuntu on my macbook and then select the option to restart, I get the message 'GRUB loading, please wait...' and I've let it wait for about an hour with nothing happening.  When I do an installation I completely erase the drive in the machine, there are no other partitions on the drive that I have created.  I'd like to start using this software, but I'm hitting a brick wall.

Can anyone help?

GRUB fails all the time. 

Follow these steps:
[http://www.planetisaac.com/articles/ubuntuinstall.html](http://www.planetisaac.com/articles/ubuntuinstall.html)

---

### Post by cowboydan on 2006-07-14
OK, so I get to the point where GRUB has failed on installation.  I start typing the commands into Terminal, the first one works fine but 'sudo mount /dev/sda3 /mnt/ubuntu/' returns an error of 'mount: can't find /dev/sda3/mnt/ubuntu in /etc/fstab or /etc/mtab'  Now, I've got my main partition on sda 3 as per the directions.  Am I still running live off of the cd when I type these in (that is what I'm doing)?

---

### Post by RAV TUX on 2006-07-14
Did you start by reinstalling Mac OS X?

so that you can repartition your disk safely

---

### Post by cowboydan on 2006-07-17
alright, I've been working on this on and off all weekend and I'm just going around in circles.  I format the drive completely, install the basic mac os x (10.4.6) that came with my machine.  I download bootcamp and create a large partition for linux.  I install refit.  I boot to the live cd, 6.06, and via the installer create a swap partition approx. 2gb and the rest of the hdd to the primary / (roughly 50 gb).  I eliminate the mount/efi system partition then proceed with installation.  Install fails with grub, I pop open a terminal window and every single time I get to the "mount /dev/sda3 /mnt/ubuntu/" command it gives me the error "mount: can't find /dev/sda3/mnt/ubuntu in etc/fstab or /etc/mtab".  I get this everytime whether I try sda3 or sda4.  With information provided, does it sound like I'm doing something wrong?

---

### Post by cowboydan on 2006-07-17
PS - If this helps, typing sudo before the mount command changes nothing, although you probably assumed that because of the error message.

---

### Post by cowboydan on 2006-07-17
Ok, here is a new update....  When I select to manually set up my partitions, there is a partition taking up about 65gb (the one created with bootcamp) that I have to delete to make 2 new ones (swap and /)  When I go into Disks Manager under System/Admin/Disks it says that my internal HDD has only 1 partition.  There has to be some problem with how I'm partitioning my HDD.  I tried doing it through OSX terminal but everytime it tells me to reboot I get a kernal panic.  Can I use disk utility when I install the basic osx, or would that create the same problem?

---

### Post by cowboydan on 2006-07-18
I found out what was going wrong.  In all of my excitement to get Ubuntu installed, I was overlooking where to put spaces.  I got someone here at work to look over them and he found them all right away.  sorry about that.  Thank you all for your help though and I'm sure I'll be around to ask more stupid questions.

---

### Post by citylife on 2006-07-18
thanks for your knowladge

---

