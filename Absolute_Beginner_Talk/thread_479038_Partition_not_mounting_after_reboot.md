---
title: "Partition not mounting after reboot"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by altralosix on 2007-06-19
I ran into the problem with the Ubuntu installer where you can't make partitions larger than 200GB, so I searched around and figured out how to make a large partition manually.  I then followed the info in this thread [http://ubuntuforums.org/showthread.php?p=2857450](http://ubuntuforums.org/showthread.php?p=2857450) and managed to mount the partition and have it accessible like any other drive.  Well, when I reboot its all gone.  I have to re-do the last couple of steps IntuitiveNipple posted to get the drive mounted again.  What do I have to modify so the partition is available every boot?

I've searched all around and found a billion threads, but nothing that seems to help this exactly.  I'm such a noob.

I'm not sure what system data would be helpful to you, so just tell me what to run and I'll post up the info.

Thanks!

---

### Post by confused57 on 2007-06-20
Maybe this guide will help:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

---

### Post by altralosix on 2007-06-20
Nada.  I followed those instructions as well.  The best I can get is the partition being mounted, and accessible in the shell, but nothing ever shows up in Gnome, and its still all gone when I reboot.

---

### Post by molly_001 on 2007-06-20
After unmounting, then mount -a again.

Then add the force mount tag to your /etc/fstab

The all-knowing 100% success path is [here]("http://ubuntuforums.org/showthread.php?t=217009"):
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

