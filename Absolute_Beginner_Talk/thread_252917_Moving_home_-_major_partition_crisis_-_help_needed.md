---
title: "Moving home - major partition crisis - help needed"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by stig on 2006-09-07
I've tried to move my Home folder to a separate hard drive and now can't boot properly.

I installed a spare hard drive as a slave (hdb) then followed the advice on: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)
to use the Ubuntu live CD and GParted to delete the old Windows software and replace it with an ext3 partition. This seemed to work OK.

Following the advice on the same web page (and still on the live CD), I tried to move my Home folder to this new disk. My first mistake was to use "hdb" instead of "hdb1" in the commands. So I used the recovery procedure given on the web page - but then I could not boot successfully into Ubuntu (it could not find /home/username).

So I repeated the commands to move the Home folder using hdb1 and  it all seemed to go OK. But when I removed the CD and booted from the hard disk I got the same warning: "Your home directory is listed as /home/username but it does not appear to exist: do you want to log in with / (root) directory as your directory?"

I have to admit that I don't really understand how the method is supposed to work. Directories are created called "old" and "new" but what happens to these after the home folder has been moved?

I would be grateful for any help in getting back my Home folder!

---

### Post by jimbren on 2006-09-07
Have you updated fstab with your new partition information for /home?

---

### Post by bulldog on 2006-09-07
Well,I never did such an operation myself,but I'll try to give you some help.

Got to administration--> disks and see what your partitions are called.
I presume your grub is working,so your boot is right and your swap isn't changed either so that's oke too.

See what the partitions are on your second hdd [hdb] and change your fstab so that all the existing partitons are listed.

Thus if I'm correct you have your /home on hdb1 so you must set it in fstab like this:

/dev/hdb1       /home           ext3    defaults        0       2

your existing and not changed partitions you can leave alone,only the new partitions must be put there so you can use them.

The thing with 'old' and 'new' doesn't mean anything to me,maybe is there some one out there who can tell you about that.

Hope you can use this to figure out your system.

---

### Post by bodhi.zazen on 2006-09-07
There are so many potential problems, details? Do you have an intact copy of home? where is it?

I would guess your problem is you have not updated fstab to mount you new home partition as /home.

---

### Post by stig on 2006-09-08
Thanks everybody for the suggestions. Sorry for the late reply but after posting the message last night (European time) the forums were very slow and I couldn't get back to the Beginners Forum. The problem seems to be resolved now - for anyone interested, more details are shown below (to understand it you really need to have read the first post in this thread).

Yes, the fstab was OK:
/dev/hdb1 /home ext3 nodev,nosuid 0 2

Some of the other questions I was unsure how to answer because, as a newbie with not much terminal experience, I didn't know how to find the information when I couldn't get into my Ubuntu.

Rather than posting back more questions I decided it was time for a steep learning curve.:-?   After more searching and reading I loaded the Ubuntu live CD again and found how to mount the two hard disks and examine what was on them. The second disk (hdb) had a folder called home_backup on hdb1 which contained a copy of my home folders, and a lost+found folder which was empty. The first (original) disk had / on hda1 and this had an empty home folder and a home-back-up folder with the expected folders/files in it plus - yet another home-back-up!

I think my original mistake with using "hdb" instead of "hdb1", followed by the recovery, had partly led to this wierd situation. Also it was partly due to a second attempt to move the home directory using, correctly, "hdb1". I think Ubuntu wasn't booting properly because it saw "home-backup" on hdb1 instead of "home/username". Somehow the folder had got onto the hdb1 partition instead of the folder contents.

Solution. I used gparted to format the hdb drive to get rid of the home-backup and lost+found folders, then used some of the original commands to copy the contents of the home-backup folder to this partition (the contents, not the folder).

Now the PC booted into Ubuntu OK and I had got back my home partition - and it was on hdb1. But some configuration was lost even though the config files should have been copied over (e.g. my Thunderbird messages and address books were missing and TB wanted me to set up a new account).

So I copied all the config files from the home-backup over those in the new home partition (a newbie's sledgehammer approach!). Now I've got TB working OK. The only problem now seems to be that the desktop is missing its launchers and customization, but that's easy to rectify.

For anyone ineterested in the method that I tried to follow to move my home partition, see aysiu's guide on:

[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

I guess it would have worked if I hadn't botched it first time around. But at least I've learnt more about Linux and the live Cd is a great tool :)

---

