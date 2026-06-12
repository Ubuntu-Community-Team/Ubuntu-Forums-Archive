---
title: "reinstalling; trouble"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by raequin on 2007-05-11
Well, due to the apparent lack of options for someone that doesn't have a correct password to log in, I started to reinstall.

I can't get past the partitioning step.

In the original install, I left my old windows install on the hd. Now I want to use the remaining space for the new install, but it appears that this windows partition is under the root file system (forgive my unknowlegeable use of these terms) so I don't know what to do. The options provided to me are to a) resize /dev/hda2/ (where the current install of ubuntu is) and use the free space (an option that would lose 1.5 gig to the old install), b) use the entire hd (losing my windows data), c) manual (but I have tried deleting the two partitions made by the old install, hda2 and swap, but I can't procede because installer says I haven't specified a root filesystem).

Help would be appreciated; greatly.

---

### Post by Ianman on 2007-05-11
To successfully install Ubuntu you need two partitions
/ = the root partition and will be a Linux EXT3 file system
/swap = is the swap parition. Usually about twice your memory size.

When you use the manual option for partitioning, you need to manually set the EXT3 partition as the root by giving it a "name" of /.

Does that make sense?

If you are re-installing, why not just install over your old Linux installation? Or do you have information on that disk you want to keep?

---

### Post by jkeyes0 on 2007-05-11
lack of options for someone without the password? I'm confused.

So I take it you lost/forgot the password for your username, right?
Did you ever set up a root password?

If not, you should be able to reboot into recovery mode (hit ESC when Grub gives you the option, and select the line that says "Recovery mode"), and reset your password.

Once you've loaded up recovery mode, you'll be at a command line. From there type
```
passwd USERNAME
``` and it should ask you to input a new password for your username.

---

### Post by raequin on 2007-05-11
Thanks.  I followed the solution posted by jkeyes0 because that answered my original problem ([http://ubuntuforums.org/showthread.php?p=2635210)](http://ubuntuforums.org/showthread.php?p=2635210)).

---

