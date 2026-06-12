---
title: "Moving an installation to another disk?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by patik on 2007-03-09
I currently have Ubuntu (Feisty Herd 5) installed at the tail end of my hard drive along with Windows (partitions: ntfs, swap, ext3 root, ext3 home). I'm all out of space and I'd like to 'move' Ubuntu to a brand new unformatted disk. 

Is it possible to simply create the partitions then copy the root and home contents over (while running from the live CD or Windows)? I'm guessing it's not, but can I at least copy the home folder? How much of my configuration will I lose? What would be the cleanest way to make this transition? 

And if I do make a clean install on the new disk, what directories on the root partition of the old disk should I backup/copy?

I should mention that I will leave my current IDE hard drive in place and the new SATA drive will be added as the second drive.

---

### Post by wpshooter on 2007-03-09
Mind you that this is just a **GUESS**, but my thoughts are that you probably can move and preserve the home directory but as far as the rest of the O/S is concerned I am **DOUBTING** that it is going to like this.

---

### Post by Aneb on 2007-03-09
I solved my hard disk space problems by copying my /home/user dir to another hard drive and mounting that hard drive as /home.. same can be done with any folder on the hd.. don't know if this is the kind of solution you are looking for

---

### Post by cybrkup on 2007-03-31
Hey all,

>  Aneb  	I solved my hard disk space problems by copying my /home/user dir to another hard drive and mounting that hard drive as /home.. same can be done with any folder on the hd.. don't know if this is the kind of solution you are looking forrrent IDE hard drive in place and the new SATA drive will be added as the second drive.


How exactly did you move your /home to another drive? I'd actually like to do the same thing. I have my root on one drive and /home on another, but I'd like to have everything on hda and use hdb as a backup. 

Thanks.

---

### Post by freesitebuilder on 2007-05-16
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) has instructions - I'm wrestling with a similar problem, but I haven't tried it out yet.

---

### Post by laidback on 2007-05-16
I have done this but not with SATA drives, I only use IDE, but I don't see why it wouldn't work. See here for the idea:-
[http://ubuntuforums.org/showthread.php?t=432140](http://ubuntuforums.org/showthread.php?t=432140)
read through the posts and then you'll see the detail towards the bottom.

With some modifications for your own requirements I see no reason why it won't work. At the very least it'll give you encouragement. I have yet to do it with 7.04 (I was using 6.06LTS).

On my 7.04 installation I loaded from the Live CD and then copied over /home/myname from 6.06, all files including hidden. I actually copied from the latest USB drive backup which was made as per above idea. I use Gparted Live CD, but the Ubuntu Live CD will also do as it has Gparted albeit a different version.

---

### Post by alienexplorers on 2007-05-16
Boot from the live cd.  Run gparted to setup /, /home, and swap.  Mount the drive you are copying from along with the drive you are copying to.  Copy the data over to the new disc. Delete the data from the old disc. Now you will probably have to rerun grub to have it setup the correct drives for dual boot.

In terminal type sudo grub.

type find /boot/grub/stage1

You will get a message such as (hd#,#)

Type root (hd#,#)

Type setup (hd#)

exit grub editor

reboot machine and hopefully it will run and detect both drives & OS'es.

---

