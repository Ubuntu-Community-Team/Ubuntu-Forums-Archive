---
title: "Partition trouble, presario v5000"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Chappo on 2007-05-16
Hi, I want to install ubustu on a presario v5000 laptop without removing the existing xp installation. It currently has 2 partitions - one containing the recovery files (which i cant seem to access) and one for everything else.

So I defraged 3 times, ran chkdsk, rebooted twice, popped in a live cd and ran gparted. Now at this point, gparted can only see one partition. And when i try to resize this partition, i get an error telling me that it cannot force the resize, and to run chkdsk again.  So I do.  I've been through this three times with no luck.  

I'm a noob, but I have dual boot installed dapper alongside xp on a different machine with no problems, which makes me think this is a problem specific to my laptop (or its current partitioning). Any ideas? I have created recovery disks for xp, so should I just go ahead and format the recovery partition and hope that that solves the problems?

---

### Post by overdrank on 2007-05-16
> **Chappo said:**
> Hi, I want to install ubustu on a presario v5000 laptop without removing the existing xp installation. It currently has 2 partitions - one containing the recovery files (which i cant seem to access) and one for everything else.

So I defraged 3 times, ran chkdsk, rebooted twice, popped in a live cd and ran gparted. Now at this point, gparted can only see one partition. And when i try to resize this partition, i get an error telling me that it cannot force the resize, and to run chkdsk again.  So I do.  I've been through this three times with no luck.  

I'm a noob, but I have dual boot installed dapper alongside xp on a different machine with no problems, which makes me think this is a problem specific to my laptop (or its current partitioning). Any ideas? I have created recovery disks for xp, so should I just go ahead and format the recovery partition and hope that that solves the problems?

Hi have you tried the alternate cd
[http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)
Scroll down to the alternate cd and be sure to follow the how to in burning the cd
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Hope this helps good Luck !:)

---

### Post by dstew on 2007-05-16
Sometimes a Windows swap file will prevent GParted from shrinking a partition if it happens to be in the zone that you want to shrink. They are usually green bars on the de-fragmenter picture. If you think this might be the problem, you need to disable the swap file from within Windows, defragment again, and try to resize again. Also, you ran chkdsk with the **/f** switch, to repair any bad sectors, right? One more thought: the GParted Live CD might work better than the one inside the Ubuntu Live CD. It seems to me that since the partitioner did not see the recovery partition, you might do better with the GParted Live CD.

---

### Post by Chappo on 2007-05-16
Thanks for the suggestions, champs.  

So, the unmovable files are near the from of the partition, and i used chkdsk /f, so no problems there. I tried running gparted from a linux system rescue system cd as well, same outcome.  And just to make me pull my hair out, the preinstallation does have a feature that should remove the recovery partition and resize the big one, which may have solved the problem, but it doesn't want to play.

I read something about LVM, could that be why gparted cannot see the partitioning?  If so, how do i get at it? really starting to get out of my depth here...

---

### Post by dstew on 2007-05-16
GParted cannot work with LVM (logical volume management) partitions. To manipulate an LVM, you need to use command line tools from within the system to which the LVM belongs. See this GParted Bug discussion: [http://bugzilla.gnome.org/show_bug.cgi?id=160787](http://bugzilla.gnome.org/show_bug.cgi?id=160787)

---

### Post by pearlie on 2007-06-15
I had the same troubles with my V5000 when I first got it - never did solve it, even though the Windows install was still fresh.  I tore my hair out trying, and finally just used that as an excuse to upgrade to a 160G hard drive... meh, I was going to need the room eventually anyway, and had another use for the original hard drive.  Not very helpful advice for you, is it? but I thought you'd like to know you weren't alone in having troubles with this specific machine.  I can't remember if it's possible to format the entire drive, including the recovery partition - if it is, you might was to consider doing that and reinstalling Windows from the disks you got with it.  (In all the years I've owned Compaqs, I've never used that partition to recover from a disaster anyway.)

---

### Post by jmusso on 2007-06-27
by no means am I an expert, in fact i don't know jack about Ubuntu... but anyways, i had a similar problem on my Compaq Presario V5000 as well, and just recently fixed it. The LiveCD, alt cd, and gparted wouldn't partition my main NTSF partition. So I defragged 3x, ran chkdsk about 3 times, did disk cleanup a few times... what I did that eventually fixed it was run a different kind of check disk, a more thorough one... You need to find the Microsoft Management Console. Open up "Computer Management," i think I found it under Control Panel >> and I forget what goes here.. anyways just look through your control panel and youll find somethign with a "Computer Management" app, run that, then find the partition you're trying to resize (probably the NSTF one or whatever,) and run a check disk with all the options clicked. It should take a long time, but it fixed it for me and i was able to load a dual-boot with ubuntu (Feisty Fawn) just fine.

---

