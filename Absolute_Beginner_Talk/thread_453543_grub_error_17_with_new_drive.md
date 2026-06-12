---
title: "grub error 17 with new drive"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Nicholas Craig on 2007-05-24
First off, sorry if this is posted a billion times elsewhere but im doing this in between class and dont have internet at home at the moment.

 I recently put together a new computer with XP and Feisty and everything is running great. I had all my music and movies on a hard drive dedicated to such in my old computer so I was just going to move it over into the new one now.. but now it gets stuck in GRUB with error 17. If I disconnect the drive everything runs like it did before.  I have one 150gb drive that XP is on and a 500gb that ubuntu is on, both sata. the new drive is ide and shows up in bios as a slave drive. it has a ntfs partition and a small fat32 partition.

My old machine was dual booting xp and feisty too if that changes anything.

If its too far over my head i can just no do it. I dont want to keep it in there permanently anyway.

Thanks!

---

### Post by matburton on 2007-05-24
I'm guessing the problem is because by adding the new hard disk your BIOS has decided to label the drives differently and grubs can't find where it was installed anymore.

What you can do is, with both hard disks in, use the live CD to reinstall grub.

Take a look at [[COLOR="Blue"]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=24113"), I'd use the second method personally

Hope that helps ;)

---

