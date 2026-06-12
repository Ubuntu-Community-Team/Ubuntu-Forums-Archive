---
title: "Help in reinstalling Ubuntu 6.10"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by raysircher on 2007-03-12
I installed Ubuntu 6.10 from a live CD.  It automatically partitioned the hard drive and resulted in a dual boot between WindowsXP and Ubuntu.  While setting up various options in Ubuntu, I mistakenly changed the password for "root" and eliminated the system administration options from the first user account (thinking that "root" was like "Administrator" in WindowsXP).  That means I can no longer access "Groups and Users", "Add/Remove Programs", or any other system administration features from my user account.  And I haven't been able to use "root" to change things back the way they were. I've gotten suggestions on the forum about how to rectify this (to restore "root" privileges to the original first user account and to restore the graphical menu options for system administration functions), but nothing has worked.  I think I may need to reinstall Ubuntu.

Question:  If I reinstall using the live CD, do I select option #1 (partition the hard drive), or option #2 (reformat the hard drive)?

If I select #1:  Will it re-partition the whole hard drive between WindowsXP and the Ubuntu reinstallation like it did the first time, or will it add yet another partition in addition to the WindowsXP and the Ubuntu that are on there now?

If I select #2:  Will it reformat the entire hard drive, wiping out my WindowsXP along with Ubuntu, or will it reformat only the partition that Ubuntu is now on?

What's the easiest and safest way to reinstall?

Any help about how to proceed would be appreciated.  I don't want to do any more damage than I've already done.  Please bear in mind that I am brand new to Linux.

Thanks.

---

### Post by buuntuu! on 2007-03-12
the option "manually edit partition table" will be best for you, as gparted has already created the linux- and swap partition on your previous install. if you just select "resize hda1 you will make your xp-partition even smaller, which you might not want. DONT select numer 2 if you want xp to survive ;)
follow psychocats [howto]("http://www.psychocats.net/ubuntu/installing") for everything else.
have fun

---

### Post by buuntuu! on 2007-03-12
doublepost, sorry

---

### Post by dptxp on 2007-03-12
I think that you go for manual partitioning, let installer (gparted) reformat all drives that do not have Windows and carry on. It will be exactly as your first one. You will have to reformat your
root '/' drive (EXT3 format) and SWAP drive (SWAP format). The formats you will see shall
be these anyway, you need not change them.

---

### Post by yamel on 2007-03-16
Hi, I'm tagging along on your thread if you don't mind.  I'm to the point of reinstall, too.

So, when I get to the "prepare partitions" window in GRUB I have:

/dev/hda2 - fat32 - 4.31 GiB
/dev/hda1 - ntfs  - 37.26 GiB
/dev/hda3 - ext3 - 49.46 GiB
/dev/hda4 - extended - 2.12 GiB
--/dev/hda5 - linux-swap - 2.12 GiB

I'm assuming my XP partition is the ntfs and the ubuntu is the ext3.  Do I edit anything here?  If I select "Forward" will it reinstall over top of ext3 automatically?  I don't see how to select where I want to put this installation, only how to change the size of each.  (I know, it might be the next step, but I'm afraid to hit "Forward" until I know what to expect.

Thanks,
yamel

---

### Post by dstew on 2007-03-16
It looks good, go forward. Next, you prepare the mount points that tell the installer where things will go. See also:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

for a graphical tour of installing.

---

### Post by yamel on 2007-03-16
Sorry for the extra post.  I reread the above, bit the bullet, and followed the directions at [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing).  Everything worked swimmingly; XP is still in tact and somehow my GRUB menu is much more orderly as a result.

Thanks for the help.
yamel

---

### Post by utkjamie on 2007-03-16
I'm getting ready to reinstall Ubuntu following a crash that left some things a bit screwy after fschk did its work. I placed my home directory on its own partition in expectation that at some point I'd probably have to reinstall (or perhaps just try a different distro) so I wouldn't lose that data.

Once I reinstall, how do I go about "moving" the current user account to the new install? Will creating a new user on the fresh install of the same name give me access to all the files on the /home partition? Or will trying to do so cause those files to get overwritten? 

Are there any permission settings I should make before the reinstall? Under WinXP, I previously ran into problems where my "home folder" data was inaccessible on the fresh install because of permission problems.

Thanks!

---

