---
title: "Need help in instalation issues"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by micbahar on 2006-11-06
First of all - thanks all for this great forum. I find a lot of helpful information in here :KS 

I'm a new user of Ubunto - or at list a want to be... I'm having problems in my attempt to install Linux for the first time in my life.

I've downloaded the live CD of the latest version of Ubuntu and I'm trying to install it (After that the CD operated Ubunto works fine). I want to use it as the only operating system on a PIII 800Mhz computer with 512MB RAM and a 40G HD of Maxtor.

The Ubunto installation program refuse to partition my HD! I've tried to set it up manually, I've tried to let it go by it's defaults, and nothing!!! 
it's starts the partition progress and blocks after a short time saying that "format failed". the HD is completely blank to begin with. What can be the cause?? I really want to start working with Ubunto already. 

Can someone please help? i don't want to give it up... ](*,) 

Thanks,
Michael.

---

### Post by bulldog on 2006-11-06
You can try the Gparted live cd it's only 25MB.
Burn this on a cd and boot from it.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)



Then try to partition again.

Some tips,

Make a /  [root] about 10GB
Make a swap about      1GB
Make the rest of your space /home

So if you gonna do a reinstall you can keep your data in your /home untouched

---

### Post by micbahar on 2006-11-06
Thanks for the tip! I boot with this CD and prepare the partitions in advance? Than I will not need to deal with partitioning in the installation process?

---

### Post by bulldog on 2006-11-06
> **micbahar said:**
> Thanks for the tip! I boot with this CD and prepare the partitions in advance? Than I will not need to deal with partitioning in the installation process?

Yep,that should do it.:D

---

### Post by micbahar on 2006-11-06
You're great, thanks a lot! :D 

I'll let you know if it worked.

---

### Post by micbahar on 2006-11-06
By the way - Should all the partitions be primary? and what filesystem to use for each one?

---

### Post by bulldog on 2006-11-06
> **micbahar said:**
> By the way - Should all the partitions be primary? and what filesystem to use for each one?

Use ext3 for your / and /home your swap will be automaticly set right.
Just choose to make a new partition in your free space and choose primary and make it 10GB and mount it as /

The same with swap and /home,just make the / bootable.

Just read carefully and you should see how easy it is.

---

