---
title: "fdisk -l"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-08-19
If i run the command
```

fdisk -l

```

and it returns something like this

> 
Device boot   Start   End       Blocks            Id     System
/dev/hda1 *    1      16708   134206978+     7     HPFS/NTFS

 and that is it.

does this mean that only window is installed on my system? :confused:

---

### Post by huggies15 on 2007-08-19
try
"gedit /etc/fstab"
then u get a list of all partitions formats mount points etc

---

### Post by HunkirDowne on 2007-08-19
This is the only partition that fdisk sees.  Are you doing this as 'user' or as 'root'?  Try:
$ sudo fdisk -l

If the preceding works, you might see a different output.

I'm running persistence right now and when I type "fdisk -l" from the $ prompt I get only the USB stick that my desktop is sitting on.  But when I type "sudo fdisk -l" I get all the hard drive partitions that exist on this particular system.

---

### Post by pgar23 on 2007-08-19
> **HunkirDowne said:**
> This is the only partition that fdisk sees.  Are you doing this as 'user' or as 'root'?  Try:
$ sudo fdisk -l

If the preceding works, you might see a different output.

I'm running persistence right now and when I type "fdisk -l" from the $ prompt I get only the USB stick that my desktop is sitting on.  But when I type "sudo fdisk -l" I get all the hard drive partitions that exist on this particular system.


I was working as root...I hope that this does not suggest that XP is the only operating system.
Is there another command I can use?
the gedit /etc/fstab didnt work for me (possibly because I am not in Ubuntu, I am working from a system rescue cd, it has a command line that runs as root.)

---

### Post by fredj on 2007-08-20
So you are not in Ubuntu. What made you think that you didn't need to tell us that in your first post?

---

### Post by HunkirDowne on 2007-08-20
There is a distinct possibility that your original concern has been realized.

Do not login as root -- use sudo -- there is a slight chance that logging in as root may have blown away your linux partition(s) if you did it just right (wrong?).

Can you provide a relative timeline of events?  Such as: (0) had windows box; (1) installed ubuntu from (be specific, please); (2) had problem ...  Specifics, if recalled, will go a long way to help troubleshoot the problem.  Sometimes, just the exercise of methodically recounting the details is enough to realize where the (original) problem lies.  Nevertheless, the ultimate solution may be to cut your losses and reinstall.

Get / use an Ubuntu CD ([http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")).

At this point decide to troubleshoot or install.  Assuming you are still wanting to troubleshoot...

Open terminal and run "sudo fdisk -l".

The beauty of using the Ubuntu LiveCD as a system rescue disk is that it is much closer to the installed system.  However, not all of your favorite apps will be accessible but most everything you need to affect repair is either there already (probably) or easily installed.  Note that unless you use persistence, the installation will go away after you reboot, but this is a small manner as you can simply reinstall (or figure out how to do the persistence bit).

:popcorn:

---

### Post by StooJ on 2007-08-20
Maybe you only have Windows installed?

You're using a system rescue CD, which is a live CD. It doesn't install anything on your hard drives.

What were you *expecting* to see with fdisk?

---

