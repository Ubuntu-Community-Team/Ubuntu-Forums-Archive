---
title: "I think an easy question(?)"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by kubfann on 2008-01-08
Hi, I had someone else install my ubuntu but we split my 80 gig HD 40/40 ubuntu/vista. Unfortunately, I have the Lenovo T61 with the nvidia quadro nvs that is (from what i've seen here) driving people crazy. I tried to put in the proper resolution manually but not when i log in, it's just a bunch of blurry lines... so I can't see or do anything.

Basically, I need to get the HD space back to Vista :( for the time being. Either I need to reset the default settings so I can do it in the OS or I need to completely remove ubuntu.

To remove Ubuntu, should I download ubuntu, put it on a CD, and then put it in when booting? I appreciate anyone who could help or could link me to a thread of the same topic (I searched but couldn't quite find what I needed).

Thanks!

---

### Post by blueridgedog on 2008-01-08
You will need a tool that can delete a partition and resize another, gparted on the live CD will do that.  I suggest you boot on the live CD as you suggest then delete the Ubuntu partitions then resize the vista one.  You will need to unmount all of the partitions prior to deleting and resizing.  Perhaps the friend that installed Ubuntu can help.

People here on the forums can help if you are left on your own.  Once/after you are up on the live CD, post the output of:
```

sudo fdisk -lu 
```

and
```

mount
```

That will help identify the partitions to unmount, the ones to delete and the ones to resize.

---

### Post by rune0077 on 2008-01-08
You can do this from Vista, via the Disk Manager - reformat the Ubuntu partition to delete it, then grow the Vista partition to use the freed space. Any way you do it, it's going to mess up GRUB and you won't be able to boot probably, so you need to have a Windows CD at hand to repair the boot sector.

---

### Post by kubfann on 2008-01-08
Thanks. Is there a way I can actually totally remove Ubuntu (for now)? If so, what commands should I enter. Thanks again for your replies.

---

### Post by rune0077 on 2008-01-08
Once the ubuntu partition is reformatted, ubuntu will be gone completely. As said, when you try to boot up, GRUB will still look for it, be unable to find it, and give you an error, which is why you need to be able to boot from the Windows CD instead.

---

