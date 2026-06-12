---
title: "Post Installation Questions"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by steve70 on 2007-12-11
Here's the situation:

I got 7.10 installed on my 250 ext HD (good lookin' GeorgiaBoot) and it runs good.

A couple of questions I have to ask...

**_1. [B][U]How to resize my ext HD to half the size? _**[/U][/B](I don't think ubuntu needs all that space, so I would like to allocate some for XP backups)

**_2. How to partition after I resized my external HD?_**

_**2. How to setup the bios on my Dell Dimension 4550 to 'see' my ext HD?**_

The system boot priority setup has a generic HD selection (C: Drive).

However, there's a separate boot priority setup for hard drives, which gives me a choice on which HD should be booted first in the system's boot priority...

When I select the boot priority for the HDs I would set the USB HD to boot first, but when I highlight the selection, the follwing is displayed:

**USB device (not installed)**

The weird part is this: Although USB isn't 'noticed' on the BIOS, I installed ubuntu on my external with no problems!

Is there something else I need to pay attention to when it comes to the BIOS seeing my external HD?

---

### Post by natehall on 2007-12-12
Read this:
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

---

### Post by c0mp13371331337 on 2007-12-12
```
sudo apt-get install gparted

```

GParted is a great partitioning GUI for Ubuntu, that will take care of your disk re-allocation needs.

As far as getting the Dell to boot to USB from BIOS, I'm actually kind of surprised it works at all.  I work with Dell computers on a daily basis, and perhaps it's just the particular ones we have in work, but ours just don't have support for booting to a USB drive in the BIOS.  Like I said, not sure if it's all Dells or just certain models.  And we're not really even booting to an operating system on a full external HD, we would be booting to batch files for ntfschk and the like on a USB key.  So yeah, no help there unfortunately.

---

### Post by steve70 on 2007-12-12
Thanks for the link, natehall:

Tried to get on the site while at work, but to no avail. Got a proxy block on it...Have to check this link later on when I get home.

---

### Post by Amstell on 2007-12-12
You can't resize a mounted drive so just load up the live cd and gparted is located on the cd.  but I would be careful when reformatting partitions.  Once I did that and totally messed up the kernal.  Could not get back in for the life of me so I had to reformat again.  Wasn't that big of a pain, but big enough.

---

### Post by GeorgiaBoot on 2007-12-12
What is weird is I have a dell and I am fully able to boot via External Drive first. 

What dells are you using at work? Maybe they are older or something?

What is also weird is I can't find any HD bios in mine only system boot bios.

I will keep looking.

---

### Post by Presto123 on 2007-12-12
I would be careful messing with Gparted at times. Not knowing what you are doing can wipe a partition, so basically, do not hit "Apply" unless you are sure you want to do it.

Nonetheless, I have two excellent CD's that I would recommend: the Gparted disk (A larger .iso file that runs like a live CD) and SuperGrub. The SuperGrub disk is an excellent disk which is basically as it says: a "Super" version of Grub. I used it quite a bit to get things back in order on my dual-boot computer.

FYI: I had issues as well with the external drive being recognized in some fashion.

---

### Post by steve70 on 2007-12-12
> **c0mp13371331337 said:**
> ```
sudo apt-get install gparted

```

GParted is a great partitioning GUI for Ubuntu, that will take care of your disk re-allocation needs.

As far as getting the Dell to boot to USB from BIOS, I'm actually kind of surprised it works at all.  I work with Dell computers on a daily basis, and perhaps it's just the particular ones we have in work, but ours just don't have support for booting to a USB drive in the BIOS.  Like I said, not sure if it's all Dells or just certain models.  And we're not really even booting to an operating system on a full external HD, we would be booting to batch files for ntfschk and the like on a USB key.  So yeah, no help there unfortunately.

I installed GParted, and I have to admit, I just have to get a handle on using it. Can't grasp on how to mount partitions once I have the size adjusted...

 Is it: 
1.root partition, then swap partition 
     or
2. vice versa?

As far as my PC, I have to learn how to deal with it. I would think there was **SOME ** type of compatibility since Dell began to install ubuntu on their PCs.

---

### Post by steve70 on 2007-12-12
GeorgiaBoot

My PC is an older model ('03'- Can we say 'legacy?') so your BIOS setup might be different (and more up-to-date) than mine.

---

### Post by GeorgiaBoot on 2007-12-12
That is probably it. Mine is from early 2006, so I don't know what to do about that.

---

### Post by steve70 on 2007-12-12
> **Amstell said:**
> You can't resize a mounted drive so just load up the live cd and gparted is located on the cd.  but I would be careful when reformatting partitions.  Once I did that and totally messed up the kernal.  Could not get back in for the life of me so I had to reformat again.  Wasn't that big of a pain, but big enough.


Had the same problem with it just before I went to work last night. Had to wipe the whole HD before reformatting. I'm just glad this is on an external HD, room for error 'til I get it right.

---

