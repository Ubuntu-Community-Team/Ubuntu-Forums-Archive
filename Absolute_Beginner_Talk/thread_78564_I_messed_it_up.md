---
title: "I messed it up"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by Minyaliel on 2005-10-18
I really need some help here. I finally got my Ubuntu cd's in the mail some days ago and was eager to try it out of ourse. So I installed it. Note that I've never used Linux before, all my previous computer experience is with various windows systems. So of course I screwed up. I didn't know what partitioning meant, so now I can't find my old Windows XP (I didn't delete anything as far as I know, so it should be in there somewhere...) and, worst of all, I don't know the password for my root user. Do I have to install it all over again? I don't really feel like going through all that once more...

---

### Post by SilentCacophony on 2005-10-18
> and, worst of all, I don't know the password for my root user.

Hello. If you did a normal install, then you have only one password, and that is for the your user account. Anything that needs root access then needs to be run through **sudo**, and applications that ask for your password should work fine with that password. See [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo").

If you did an expert install (by entering 'expert' at the first boot prompt from the install disk), then it could be a problem if you weren't sure what was going on.

> I didn't know what partitioning meant, so now I can't find my old Windows XP (I didn't delete anything as far as I know, so it should be in there somewhere...)

If you open a terminal (Applications > Accessories > Terminal, in the desktop menu) and enter this:

**sudo fdisk -l**

It should prompt you for a password. Try the password that you set up on install (it's a blind entry,) and if it works, that's the way it's supposed to work. It will also output your harddrive/partition setup. If it works, copy and paste that back here.

---

### Post by Minyaliel on 2005-10-18
minyaliel@minyaliel:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7215    57954456   83  Linux
/dev/hda2            7216        7296      650632+   5  Extended
/dev/hda5            7216        7296      650601   82  Linux swap / Solaris
minyaliel@minyaliel:~$


Password's alright now :)

---

### Post by SilentCacophony on 2005-10-18
Sorry to say, if you only have one harddisk (fdisk shows only one,) then you erased your Windows installation and installed Ubuntu over it.

At the the point in the installation where it has the [COLOR="Red"][!!] Partition disks[/COLOR] dialog, you must have chosen the 'Erase entire disk:' option, because your setup matches what that option does. The 'Manually edit partition table' option is what I use, but some knowledge of partitioning helps.

```
 Device Boot Start End Blocks Id System
/dev/hda1 * 1 7215 57954456 83 Linux
/dev/hda2 7216 7296 650632+ 5 Extended
/dev/hda5 7216 7296 650601 82 Linux swap / Solaris
```

This shows that most of the drive is hda1, which is your Ubuntu partition, and hda5 is a small extended partition for linux swap space (virtual memory.)

If you want to try and set up a dual-boot with Windows and Ubuntu, here are some links you should read through:

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://www.ccs.neu.edu/home/jabra/breezy-docs.html](http://www.ccs.neu.edu/home/jabra/breezy-docs.html)

Also, some info on partitioning:

[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

---

### Post by Pausanias on 2005-10-19
Note to devs: ask twice before allowing the installer to erase an HD whose sole partition is windows.

Now, where would I file a suggestion like that? Bugzilla?

---

### Post by poofyhairguy on 2005-10-19
[QUOTE=Pausanias]Note to devs: ask twice before allowing the installer to erase an HD whose sole partition is windows.

Now, where would I file a suggestion like that? Bugzilla?[/QUOTE]


Yep, Bugzilla.

---

### Post by Minyaliel on 2005-10-20
Oh nooooooo.......... :cry: ](*,) Well, thanx guys :)

---

### Post by az on 2005-10-20
It does ask twice.

It offers you the options.  You pick one. It tells you that this will erase everything.  It calculates the partitions and then it asks you yes or no.

Probably, your setup was not partitionable (sometimes, if you partition with windows partition tools, GNU parted can no longer work on the partition table - it is mangled) and it cannot offer the option to shrink current partitions.

---

