---
title: "Wiped Windows"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-23
I should have known better but I installed two distros on my Dell Desktop and seem to have wiped Windows completely. There is no sign of it in the attached screen print!!

I have backed up all my own files or at least those I need but does the picture attached mean that my Windows is gone forever??

Thanks


Bern

---

### Post by Ub1476 on 2007-11-23
Yes, it looks like you removed it.

---

### Post by bodhi.zazen on 2007-11-23
Unless you have a second hard drive ....

Oh, and my guess is you have too much swap. Typically swap = RAM x2 , i Gb max.

You may need swap = RAM on laptops if you use hibernation.

In general, the more RAM you have the less you need swap , although it depends on the apps you run, and more swap does not increase performance.

---

### Post by markp1989 on 2007-11-23
why do you have 2 swap partitions?

---

### Post by bern1939 on 2007-11-23
In honesty I have two swaps because I did not quite know what I was doing!!

I really only want to use Ubuntu .... it is really working very well indeed and a lot to learn up ahead.

The second distro (SUSE) is on SDA2 as you see .... should I just remove that one?
And what other partitions should I remove?

Thanks

Bern

---

### Post by azimuth on 2007-11-23
Looks like Windows is gone to me. You may take some comfort in my observation that the more installs you do the less likely you are to wipe the Win partition. The flip side of that coin is, the more you use Ubuntu, the less you care if Windows is on the machine when you finish an install.

---

### Post by bern1939 on 2007-11-23
Good point indeed.

How then do I remove the second distro?

Thanks

Bern

---

### Post by ukripper on 2007-11-23
unless you pay third party to retrieve from your hard-disk, it is gone with the wind.

Always create backup or clone your Hard-disk before you try something new on partitions without knowing the end product.

---

### Post by hyper_ch on 2007-11-23
You want to remove the other distro? There's no need to unless you know you won't use it or if you need the diskspace for something else.

---

### Post by ukripper on 2007-11-23
> **bern1939 said:**
> Good point indeed.

How then do I remove the second distro?

Thanks

Bern

Before you get rid of other distro make sure you check your boot partition is not on it.
```
df /boot
```

and then just use gparted through live cd and get rid of it if you want to.

make sure you backup any needed files before you play with gparted

---

### Post by bern1939 on 2007-11-23
Thanks to all.

Finally can you direct me to a site or whatever to see how one can backup or clone the hard drive.

Thanks again


Bern

---

### Post by ukripper on 2007-11-23
Backup is already default with ubuntu you can use sbackup - [http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

For cloning - use [http://clonezilla.sourceforge.net/clonezilla-live/](http://clonezilla.sourceforge.net/clonezilla-live/) 

I clone all my HDD using this app's live cd

For backup i use [http://www.mondorescue.org/](http://www.mondorescue.org/)


For files backup alone - i just use  tar backup 
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by bern1939 on 2007-11-23
Thanks..... this is what I get:

bernard@bernard-desktop:~$ df /boot
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             26557436   8846880  16361504  36% /

Does that mean that the boot is residing on /dev/sda6?

Thanks for assistance.


Bern

---

### Post by ukripper on 2007-11-23
> **bern1939 said:**
> Thanks..... this is what I get:

bernard@bernard-desktop:~$ df /boot
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             26557436   8846880  16361504  36% /

Does that mean that the boot is residing on /dev/sda6?

Thanks for assistance.


Bern

Yes. that means your boot partition is on same as your root i.e. on /dev/sda6

---

### Post by bern1939 on 2007-11-23
This is what I get.

bernard@bernard-desktop:~$ df /boot
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             26557436   8846880  16361504  36% /

I take it that 'boot' is on /dev/sda6 so keep away from that partition.

I can then safely delete sda2 and its associate swap?

Thanks 

bern

---

### Post by ukripper on 2007-11-23
> **bern1939 said:**
> This is what I get.

bernard@bernard-desktop:~$ df /boot
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             26557436   8846880  16361504  36% /

I take it that 'boot' is on /dev/sda6 so keep away from that partition.

I can then safely delete sda2 and its associate swap?

Thanks 

bern

**Do no**t delete /dev/sda6

Make sure  the swap you are deleting is associated with partion you want to get rid of otherwise you'll end up deleting your current swap.

---

### Post by bern1939 on 2007-11-23
I am most grateful to you all.

How come I have almost forgotton that there was a Windows!!!!


Thanks again

Bern

---

### Post by ukripper on 2007-11-24
Welcome to ubuntu!:guitar:

---

### Post by markharding557 on 2007-11-24
wiping windows was excellent thing to happen now you've no need to think about windows again
welcome also

---

