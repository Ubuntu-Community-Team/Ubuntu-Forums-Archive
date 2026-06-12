---
title: "Still unable to install"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Swerve1000 on 2007-01-24
Hi,

I cannot install Ubuntu and the tutorial I found does'nt contain any usefull info.

I have just freshly installed XP on my 40gb hard drive. There is only one hard drive and XP has 35gb leaving 5gb for Ubuntu.

I chose 'manually edit partition table' and the following screen appears containing the following info:-

Page Title = Prepare partitions

                                           Size              Used          Unused          Flags
/dev/hda1      ntfs                 34.18gb         4.29gb       29.89gb         boot
unallocated    unallocated

Changing nothing I clicked 'Forward'

The next screen to appear is the 'Prepeare mount points' screen:-

What am I supposed to do here??????? I click 'Forward' and it says 'No root file system'.

Previously I chose the option which was something like 'install on largest unused partion' but ended up having 4 different options for Ubuntu on boot which I don't want, fedora gave me one simple option - XP or fedora and now when I select XP I now have two XP options, one of which is 'blank'. I tried to change it but my XP wont even work now because Ubuntu has screwed up the boot and now it says Grub loading....Error 22.

This really doing my head in... I've tried to install this Linux about 20 times now, all I want to do is install it on the spare 5gb partition I created when I installed XP.

I am really mad with this, could anyone explain what I need to do in a langiage which a complete idiot would understand please.

Thank you very much for your help.

---

### Post by energiya on 2007-01-24
> **Swerve1000 said:**
> 
The next screen to appear is the 'Prepeare mount points' screen:-

What am I supposed to do here??????? I click 'Forward' and it says 'No root file system'.


you must have a partition for mounting "/" and one for swap. I never tried installing with gparted or something like that (using good old partition magic from windows).

---

### Post by Swerve1000 on 2007-01-24
> **energiya said:**
> you must have a partition for mounting "/" and one for swap. I never tried installing with gparted or something like that (using good old partition magic from windows).


Thanks for your help.

There is'nt enough room to have both the / partition and the swap partition.

There is only one partition, the unallocated one.

---

### Post by riven0 on 2007-01-24
You will have to make another partition and label it ext3. The ext3 partition should be at least 5Gbs itself, especially if your using it as root and your /home. It is recommended that swap should be double the size of your RAM, but I use less, (512Mbs for swap), and I'm fine. Don't make it too small, though, or you may run into problems. Make sure the swap is labelled as Swap, too.

Good luck!

---

### Post by energiya on 2007-01-24
> **Swerve1000 said:**
> 
There is'nt enough room to have both the / partition and the swap partition.
There is only one partition, the unallocated one.

Firt of all make 2 partitions from the unallocated space. One ext3 (the largest) and one swap. 
I ran Ubuntu for a long time using 4GB for / and 200MB for swap (I have 128MB ram), so it shouldn't be a problem.

As riven0 said, swap should be double the size of your RAM.

---

### Post by Swerve1000 on 2007-01-24
> **riven0 said:**
> You will have to make another partition and label it ext3. The ext3 partition should be at least 5Gbs itself, especially if your using it as root and your /home. It is recommended that swap should be double the size of your RAM, but I use less, (512Mbs for swap), and I'm fine. Don't make it too small, though, or you may run into problems. Make sure the swap is labelled as Swap, too.

Good luck!

Thanks!!

So I will end up with 3 partitions then??? 1 partition being unallocated, 1 labelled ext3 and a third being the swap partition.

Could someone just write how I should do it please, like:-

Partition 1 - ext3 
partition 2 - swap
Partition3 - unallocated

Also which need to be primary or whatever the other option it is called? What is this /home thing?

Many tahnks to anyone who expalin this point in simple english please

---

### Post by Swerve1000 on 2007-01-24
> **energiya said:**
> Firt of all make 2 partitions from the unallocated space. One ext3 (the largest) and one swap. 
I ran Ubuntu for a long time using 4GB for / and 200MB for swap (I have 128MB ram), so it shouldn't be a problem.

As riven0 said, swap should be double the size of your RAM.

That makes more sense!1

What about this Primary stuff?

---

### Post by Swerve1000 on 2007-01-24
OK , i've watched a video tutorial. It says that both partitions (ext3 and swap) should be primary partitions.

Is this correct?

Which shopuld I make first? the swap or the ext3?

---

### Post by energiya on 2007-01-24
> **Swerve1000 said:**
> OK , i've watched a video tutorial. It says that both partitions (ext3 and swap) should be primary partitions.

Is this correct?

Which shopuld I make first? the swap or the ext3?

I don't it matters. I have swap the last partition on my hdd, but most have it first.
Found some links: [[1]]("http://www.pcmech.com/show/os/903/"), [[2]]("http://www.psychocats.net/ubuntu/partitioning"), [[3]]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=2"). Hope this helps.

---

### Post by Swerve1000 on 2007-01-24
Thanks for your help energia, I'm going to try it all again now.

Thanks

---

