---
title: "Unable to copy the user's Xauthorisation file. ??"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by alanmzifa on 2006-09-02
Hi, I'm getting this error message when I try to update or launch synaptic on a laptop I installed Ubuntu on yesterday.
> 
Failed to run /usr/sbin/synaptic

Unable to copy the user's Xauthorisation file.

I don't know what that means. Can anyone help explain please.


Also, don't know if this is related but I'd just been using Automatix to download some plug-ins and I was getting "low disk space" warnings even though this is a new installation.

df -h reports

> joyce@joyce-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda1             1.9G  1.9G     0 100% /
varrun                126M   80K  126M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
udev                  126M   88K  126M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-26-386/volatile
/dev/hda4             1.1G   42M 1010M   4% /boot
/dev/hda3             5.8G  151M  5.4G   3% /home


I'm a recent (partial) convert to ubuntu and would appreciate any assistance.

thanks

---

### Post by alanmzifa on 2006-09-02
I think I've worked out my problem is down to partition sizing and from my level of knowledge the best way to sort this out will be to do a fresh install.

I haven't been able to understand why I need separate partitions and what they're for.

The laptop will have ubuntu installed as the sole OS and will have just 1 user. It has a 10GB HDD.

Do I therefore just need a boot, root and swap partition. I know the swap only needs to be 1.5 times RAM but what size should the others be and is it important which one comes first?

thanks

---

### Post by dbd on 2006-09-02
I don't know what a separate boot partition is for, as far as I know you only **need** root and swap partitions.

However, I would greatly recommend having a home partition, this way if you ever need to reinstall you can just format the root partition in the installation process but you do not need to touch the home partition. Then you will keep all the data in that partition, even your settings files.

Also, if you have a lot of RAM then there is no need for the swap partition to be 1.5 times its size. If you have 1Gb of RAM you can probably get away fine with 500MB swap partition. (By the way, this is only a rough suggestion, there is far more detailed info on this around the net.)

I'd recommend having a 3.5Gb - 4Gb root partition, a awap partition and the rest of the hard disk as a home partition.

As for which comes first, I think its best to have the root partition first, then the swap, then any others (home etc, whatever you want).

---

### Post by alanmzifa on 2006-09-02
Thanks, that's made things much clearer.

I'm going to try it out now.

---

