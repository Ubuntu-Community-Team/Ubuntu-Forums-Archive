---
title: "Problems with SATA Raid How To"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by FriscoZR on 2007-10-21
Hi,

My deviation is that I'm not installing the OS on the raid. This probably should make things easier, but apparently not for me. I'm just adding the drives as mirrored storage.

When I get to the part about adding the directory and mounting - that doesn't seem to work.
I also don't have gparted where the tutorial says it should be so I just used fdisk to add a partition.  All that seems to work and when I do the mkfs.ext3 both drive lights go. So I'm guessing that went ok - but I can get no further.

Anyone with some ideas? Should this be easier without the image install?  What steps are different? Etc...

Thanks in advance for the assistance.
Ciao,
Matt

---

### Post by taygull on 2007-10-21
I'd sure like to know the answer to this as well.

---

### Post by taygull on 2007-10-23
Can't any of you masters help with this?

---

### Post by LinuxNewb_22 on 2007-10-23
I've installed Feisty over a RAID 0 configuration and know how to install over a RAID 1... which is what, I believe, both of you want, correct?

I don't know how to install a "mirrored" drive once the OS has been installed... merely during installation.

If you would like to know how to set up a RAID 1 configuration, please let me know.

Upon thinking about your query further, I'm guessing the reason why you're asking about "adding the drives as mirrored storage" is that you have data on the original drive that you do not want to lose... ?

Anyway, as I wrote, above, please post back if you'd like to know how to install RAID 1 on a fresh install... you probably already do, but, as you can tell by my handle, I'm just happy to be able to pass on anything I've learned in the short while that I've been on Ubuntu. :)

---

### Post by FriscoZR on 2007-10-23
Thanks for the reply - all help is desirable.
I believe that it's Raid 1 - mirror -> data is same on two drives.

I've done:
 the setup in the bios.
 don't have gparted so used fdisk to add partition
 did mkfs.ext3

All this seems to have worked.

I next tried to add dir using mkdir and that didn't seem to work.
Don't know if I was pointing to the right place.
The tutorial assumes root - but I don't think that's the case here since I'm just adding on to an existing system. So the mkdir just added the dir to my existing hard drive not the new mirrored ones.
So couldn't do mount either...

Any ideas on what I'm missing or doing wrong?

---

### Post by LinuxNewb_22 on 2007-10-23
I did NOT set up RAID option in bios. That part has remained disabled.

The way I did it was to use the Alternate ISO cd to install a fresh copy of Ubuntu and use the partitioner to configure the RAID.

Remember: you WILL LOSE all of the data you have on both drives by following these instructions. So, if you'd like to keep any data, make sure that you back it up to a different drive (that you are, obviously, not using as part of your RAID system).

Again, do NOT set the option in BIOS. If you have set the RAID option in BIOS, disable it.

The following is what I did to configure RAID 0. I will modify the instructions for RAID 1.
--------------------------------------------
Boot up with the Alternate ISO install cd/dvd for Ubuntu.

Select the first option, which I believe is "text-based installer" or something to that effect...

Go through the usual install options (language configuration, keyboard layout, etc) until you get to the partitioner...

...Select MANUAL partion.

Then make 4 partitions as follows:
1) (beginning),150MB, format for RAID, boot flag ON [this will be your /boot] (this will be named sd*1 by the partitioner)
2) (end) 2GB, format for RAID [this will be your swap] (this will be named sd*4 by the partitioner)
3) (beginning) 10GB [or 20GB, depending on the size of your hard drives], format for RAID [this will be your /root] (this will be named sd*2 by the partitioner)
4) (beginning) max, format for RAID [this will be your /home] (this will be named sd*3 by the partitioner)

Once you have made those partitions, select "Confgure software RAID". This will configure the 4 partitions across both drives.

You will create a series of MD partitions with the following attributes.
1) RAID-1 for sd*1, Ext2 file system, yes format, mount point: /boot
2) RAID-1 for sd*4, swap file system
3) RAID-1 for sd*2, Ext3 file system, yes format, mount point: /root
4) RAID-1 for sd*3, Ext3 file system, yes format, mount point: /home

Once you have done that, select "Finish". Check to see that the partitioner created the 4 partitions. You may have to individually select the partitions and give them the attributes, just above, again. (For some reason, sometimes it doesn't keep them...)

Once you've made sure that you can see the 4 RAID partitions with the above attributes for the respective partitions... select the option that basically means you are done using the partitioner. The next screen will show you a review of the 4 RAID partitions that you created and will ask you if you want to write these changes. Select "Yes".

You will then go through the rest of the OS install process as normal.

I hope that helps.

---

### Post by FriscoZR on 2007-10-23
Thanks again for the reply.

Please note - I am not wanting to install an image to these drives - already have the image on its own drive. These drives are for data storage only. Not even wanting to put my 'home' on them - they will be used for mass file storage and it's desired to be hot swappable with other data drives(sets) in the future.

I will look over and consider all your information - it looks very useful - I'm sure it will help someone out - but at first read it doesn't seem to be applicable to what I'm trying to do.

Thanks again - if you have any other ideas as to what I might be doing wrong, please feel free to add on.

Much Thanks,
Matt

---

