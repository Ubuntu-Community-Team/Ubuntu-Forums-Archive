---
title: "Ubuntu will not boot. Get an error in recovery mode. PLEASE HELP"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by revi_2003 on 2007-11-30
Hello all,

I have gone a few days without using Ubuntu on my desktop and I think it went on standby. When I turned it on it would not log into GNOME/X Server so I did a hard reboot.

Ever since when i try to start Ubuntu in normal mode it doesn't boot at all. I get a blank screen. So i tried starting Ubuntu in recovery mode and got the following error:

Begin: Running /scripts/local-bottom...
Done.
Done.
.: 195: Can't open /etc/default/rcS
error: '/etc/init.d/rc' exited outside the expected code flow.
init: rcS main process (2452) terminated with status 2
root@(none):~#

Thanks for any help in advance

---

### Post by Drate on 2007-11-30
You might could try running a liveCD, mounting your filesystem (if needed), and then run a fsck..  Exact details on howto do that someone else would be better to give, or else search for mount and fsck commands in the forums or google.

---

### Post by revi_2003 on 2007-11-30
Can anyone help with how to use fsck to correct this issue. Thanks Drate!

---

### Post by revi_2003 on 2007-11-30
Tried using fsck through a live CD and it does not work.

ubuntu@ubtuntu:~# fsck /media/disk

gives me an error:
The superblock could not be read or does not describe a correct ext2 filesystem.

I think my filesystem is ext3

Can anyone suggets something?

---

### Post by Drate on 2007-11-30
I am ASSUMING that your entire filesystme is mounted on hda1.  If that is the case, and it is ext3.. then this is what I would try from within your liveCD:

fsck /dev/hda1
if it's mounted on sda1 then adjust accordingly.  you can possiblycheck this by doing:
ls /dev/hda  OR  ls /dev/sda and whichever ones returns without error is yours.

if, perchance, you are dual booting with *sigh* windows or something... then it is probably going to be hda2 or sda2.

If you're using LVM... then... well I have no idea.

---

### Post by revi_2003 on 2007-11-30
> **Drate said:**
> I am ASSUMING that your entire filesystme is mounted on hda1.  If that is the case, and it is ext3.. then this is what I would try from within your liveCD:

fsck /dev/hda1
if it's mounted on sda1 then adjust accordingly.  you can possiblycheck this by doing:
ls /dev/hda  OR  ls /dev/sda and whichever ones returns without error is yours.

if, perchance, you are dual booting with *sigh* windows or something... then it is probably going to be hda2 or sda2.

If you're using LVM... then... well I have no idea.

Thanks Drate!

Ran:

sudo fsck /dev/sdb2

gave me a warning sign and i said yes to run

then got a clean message.

That did not fix my boot problem however. :-(

---

### Post by Drate on 2007-11-30
Hmm... well you are beyond me.  It'd e easier if I could look at it myself.

Are you able to access your files from the LiveCD?  If so then A: there is still hope to make it boot once more... and B: if you can't make it boot you have the opportunity to recover any files you need, start over, and be a wee bit more careful when acting as root.  With great power comes great responsibility.  Spiderman's great uncle or whoever taught me that.  :-D

Typically though you shouldn't have to reformat a linux system.  You must have done something special!  Or it's a fluke.  Fluke happens.  Use the farce fluke!

---

