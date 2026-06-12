---
title: "Installing on MacBook - need Partition help!"
date: 2008-04-17
forum: Apple Intel Users
---

### Post by JoJerome on 2008-04-17
Been searching other threads but haven't found an answer yet.

I've got a MacBook Santa Rosa and have been using the wiki at [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa) to split the hard drive down the middle; Keep Lepoard on one half, put Gusty on the other.

As per the instructions, I installed rEFIt, which seems to work great.

I used BootCamp to partition the hard drive.

I dowlnoaded Gusty and burned it to a CD which so far seems to be installing just like it should.

I get to the bit about partitioning and choose 'manual partition' as per the wiki instructions. It shows:

EFI on /dev/sda1
79g available on /dev/sda2 (which I'm guessing is OSX)
80g available on /dev/sda3 (which I'm guessing is the free space)

How exactly do I proceed? The instructions say to create an /ext3 partition but doesn't say how to do that or if that's where I'm putting Gusty. When I try simply choosing /dev/sda3 it tells me "no root system is defined." How do I do that?

Thanks in advance ...

- Jo

---

### Post by cyberdork33 on 2008-04-17
you have to tell it how to use the partition in the manual partitioner.

The easier method is to boot from the livecd, start the partition editor from the menus, select your new partition and delete it (leaving free space) then start the installer. When given the option, choose to install to the largest free space and the installer will take care of the rest.

---

### Post by JoJerome on 2008-04-17
Ok, I think I got the partitioning sorted out. I chose "edit partition," and from the pull down menus chose "ext3" and changed the mount name to /. 

It seems to have installed ok. I restart, it spits out the CD, rEFIt gives me the option to boot to Linux, I opt for it ... and it says something to the effect of "no bootable device, insert disk."

I've tried re-installing a couple of times but no good. I'm currently on the third re-install but haven't restarted it yet.

Is there something I can be setting up/troubleshooting in Gusty from this point in the install to make sure it will boot from the hard drive?

Thanks again

- Jo "I know I can I know I can" Jerome

---

### Post by guj4_n3b3sk4 on 2008-04-18
I don't want to repet myself again. Similar problem was mentioned in some other thread, so here's a link to my answer there, maybe it will help you.

[Link to the answer.]("http://http://ubuntuforums.org/showthread.php?p=4732890#post4732890")

Make swap partition sized like MB's of your memory (I have 1G memory, so I made 1024M swap place) just in case. Dunno if that's a problem, but try making that partition also if you haven't done that.

---

### Post by cyberdork33 on 2008-04-18
a swap is not required.

if refit is not finding something bootable, then grub is likely installed badly. I would try again using the method I mentioned. use gparted to delete the partition, then install to the free space.

---

### Post by JoJerome on 2008-04-18
Thanks again for the help.

While waiting for replies I re-installed again and it appears to have faith healed itself. Don't think I did anything differently.

So now the issue is that Adept Installer crashes when I try to apply updates. Today's adventures include going through the many fix-it wikis to tweak Kubuntu to play nice with this MacBook. Hopefully, somewhere in the process of that tweaking, Adept Installer will also faith heal itself.:KS

---

### Post by Dave Loschi on 2008-05-07
Hello!

I have a macbook with penryn 2,4 GHz processor.

Unfortunately I can't install Ubuntu 8.04 beside Mac OS X on my macbook.
I already did everething written in this thread:

- install refit
- use bootcamp to make free space
- create new "ext 3" with mount point "/" in the free space
  swap with 2048 MB (my ram size is 2GB)

When I restart my macbook after installation of 8.04 and refit starts to boot ubuntu from hd this message appears: "no bootable device - insert disk"

Does anybody has another suggestion?
thanks

dave

---

### Post by cyberdork33 on 2008-05-07
There is a new Apple forum. Please look there.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

Specifically your problem is related to a bug in the Hardy Heron release. The solution(s) are here:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by Dave Loschi on 2008-05-08
thanks that really helped!

---

