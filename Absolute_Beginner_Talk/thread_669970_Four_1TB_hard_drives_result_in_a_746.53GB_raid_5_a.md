---
title: "Four 1TB hard drives result in a 746.53GB raid 5 array? Please help."
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Squega on 2008-01-16
I am running into a problem where if I create a raid 5 array with 4 1TB drives in the system using mdadm, the resulting Raid 5 array only shows as being 746.53GB in size. I did a thorough google search on this and ran into someone who had the same problem (translated from German). This person's post can be found _[here.](http://translate.google.com/translate?u=http%3A%2F%2Fwww.debianforum.de%2Fforum%2Fviewtopic.php%3F%3D%26p%3D559345&langpair=de%7Cen&hl=en&ie=UTF-8)_

The solution for that person's problem was to switch to Ubuntu 7.04 with "CONFIG_LBD = y" enabled in the kernel. I am running Ubuntu 7.10 server and that kernel parameter has already been set to "y".

The four 1TB SATA drives are currently connected to a VIA SN18000 motherboard with the 8251 "fakeraid" controller. I originally ran into this problem when I set the SATA controller to raid mode and created a a raid 5 array using the controller's bios. The viaraid utility correctly detected the array as 2.8TB, but Gparted only showed the array as 746.53GB. I shut off the raid functionality of the motherboard in the bios and instead created the raid 5 array using mdadm using this command:

```
mdadm --create --verbose /dev/md1 --level=5 --raid-devices=4 --chunk=4096 /dev/sda /dev/sdb /dev/sdc /dev/sdd
```

But the resulting array only shows as 746.53GB in Gparted.

I am completely lost on what to do. I could definitely use some help on this problem. If there's another thread about this then I apologize since I searched through these forums for anything regarding raid issues and read through it all before I posted this.

---

### Post by Squega on 2008-01-17
Just giving this a bump before I go to sleep. I really hope someone can help me out on this one.

---

### Post by Squega on 2008-01-17
Bumping again to un-bury this post.

---

### Post by dstew on 2008-01-17
Are you sure the chunk size is correct? That is pretty big, 4 megabytes. You might also try the --auto option to create the device file, in case md1 is taken or not properly defined.

---

### Post by dgray_from_dc on 2008-01-17
Have you checked the sizes of the individual drives?

```
fdisk -l
```

746.53GB doesn't even sound right for 1 drive.

---

### Post by Squega on 2008-01-17
I don't have access to my file server since I am at work right now and forgot to setup SSH, but I can provide some answers.

When I was trying to create the array using mdadm originally I didn't specify chunk size and the resulting array was still only 746.53GB in size. I thought the chunk size I specified in my command above was 4K so i'll rerun the command later with a smaller chunk size.

I did do an fdisk -l yesterday to check the drives and Ubuntu recognizes each drive as having 931GB in size. I'll post a printout of the command when I get home from work today.

Thanks for the replies so far. :)

---

