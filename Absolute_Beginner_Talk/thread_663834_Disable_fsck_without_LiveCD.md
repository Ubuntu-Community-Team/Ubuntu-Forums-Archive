---
title: "Disable fsck without LiveCD"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Jugney on 2008-01-10
Is there a way to disable fsck without the LiveCD? The check started trying to run last night, but it froze and on every subsequent hard boot it freezes. 

Since the Gutsy LiveCD doesn't work for me (I have nVidia graphics card), I know of no way to disable this feature, since I can't get into ubuntu. Can I edit etc/fstab from a command line? Can I even get a command line?

THank you,
Jugney

---

### Post by philinux on 2008-01-10
You're going to need a live cd to sort this out. As taurus mentioned in your other post.

fsck is trying to check out your ntfs partition and getting locked up somehow.

---

### Post by Jugney on 2008-01-10
Thanks for the response.

Since my Windows wasn't working anyway, I used a GParted CD to delete the NTFS partition it was on and reformatted it to ext3. However, on retrying the fsck still freezes at the same point. 

Come to think of it, I don't see why the NTFS partition would have been a problem. Fsck said it was checking dev/sda6, which is my Linux ext3 partition.

Any other ideas? Perhaps there's a way to edit the boot commands so that fsck is disabled?

I would try to make an Edgy 6.06 LiveCD, as I've read those work with HP laptops, but I can't get into ubuntu to make the disc! Are there any utilties to boot into a DVD burning program?

Jugney

---

### Post by philinux on 2008-01-10
Ok I tried rebooting my machine into recovery mode. I guessed right. Before it gives you the command prompt it checks the file system. 

From the live cd you can really sort things out. See if you can burn another.

---

### Post by Jugney on 2008-01-12
Hi everybody,

Well, the same solution worked as last time - I just rebooted and let the test run (and freeze) enough times until it actually finished. I really hope that this utility will be improved so it works better in the future.

And as far as the live CD, just for the benefit of anyone who may read this in the future, I was able to get it to load by using "Safe Graphics Mode" It may seem obvious, but it wasn't to me at that time! And so maybe it will be helpful to others.

Take care,
Jugney

---

### Post by philinux on 2008-01-12
ok so now use

cat  /etc/fstab 

and post the output

---

### Post by Jugney on 2008-01-12
/dev/sda6 had been set to 1, but I changed it to 0 (as reflected below)

Is there a way to schedule fsck to run while I'm in ubuntu? I'd like to keep doing this check because I understand it's important, but I want to do it in a way that will actually work!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=9042158f-7085-48be-b56f-cce9007c5aef /               ext3    defaults,errors=remount-ro 0       0
# /dev/sda7
UUID=67a5e6a4-e50a-4d34-8e2e-be85da928a4e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

