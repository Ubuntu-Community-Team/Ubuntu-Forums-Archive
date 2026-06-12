---
title: "No space left on device"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by jaredssix on 2007-05-01
Since upgrading to Feisty, I've not been able to install any new aps.

A Maxima download led to a ~crash, where I had to command line in and remove it before I was allowed to enter the Ubuntu interface again.

I just attempted to download graphvin (?), a graphing ap (OpenOffice graphing is weak), and it failed to launch. 

A quick study of my System Log and I see that many of the failures are due to "No space left on device"

Ideas?

--Just tried to close out of OpenOffice, and I can't save my work. Apparantly I have insufficient free disk space at /home/jared/.openoffice.org2/user/backup . . .. I can't even find this location!

I wasn't having these issues before the upgrade.

--and now got an additional error message
Failed to run /usr/sbin/synaptic as user root.
Unable to copy the user's Xauthorization file.

What a mess!

---

### Post by joft on 2007-05-01
At least one of your partitions seems be full - "no more storage room". Look at your syslogs again and try to identify which partition (device) it is ("/dev/XXX").

Usually you have one partition only, which is mounted as the / (root) filesystem. apt (package management system) caches downloaded packages somewhere in /var . Sometimes this caches occupies a much space, so you could try to delete them, open a terminal window and do:
```

sudo apt-get clean

```

---

### Post by Michaelt74 on 2007-05-01
Have you done  a backup recently? If so, Ubuntu backups at times use a huge amount of disk space. Check out this link for more information. If you didn't do a backup you can still use the commands to clear out the files using up your space. 

[http://opensourceroolz.wordpress.com/2007/02/01/backing-up-and-the-driver-space-eater/](http://opensourceroolz.wordpress.com/2007/02/01/backing-up-and-the-driver-space-eater/)

Good luck!

---

### Post by jaredssix on 2007-05-01
I am a noobie . . .
And I think Joft is on to something.

I initially installed 6.06, and then upgraded to 6.10, then 7.04 last weekend. When I start up my dual-boot, I am allowed to select from several Ubuntu listings, and one Windows listing.

I checked the system log again, and so no clues as to which partition is active. /home/jared/.gconf appears to be especially active, if active includes especially failing!

I ran your suggested code . . .  hard to say right now if it had any effect.

Thanks for your prompt responses.

---

### Post by trak87 on 2007-05-01
Sounds like your /home directory is full. If your Ubuntu is on one big partition, then what the previous poster says about running 'sudo apt-get clean' will free up some space.

On the other hand, if you have a separate /home directory partition you can find out where most of the space is being used with this:

```
cd
du -c --max-depth=1 | sort -n
```


When you find out which directory is using the most space, cd into that directory and run the du command again. If you find stuff you no longer need, delete it.

---

### Post by jaredssix on 2007-05-01
./.mozilla-thunderbird has 260148 um . . . bytes (?)--that's 260 KB--not so drastic, is it?

Or, are my numbers wrong. The list also states the total to be 335104 . . .

Or, my partitioning has gone awry, and my total playing field is just 335 KB!!

---

### Post by jaredssix on 2007-05-01
./.mozilla-thunderbird has 260148 um . . . bytes (?)--that's 260 KB--not so drastic, is it?

Or, are my numbers wrong. The list also states the total to be 335104 . . .

Or, my partitioning has gone awry, and my total playing field is just 335 KB!!

As stated, I have an inkling that my upgrades have led to over-partitioning.

fdisk reads:

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        4469    35841015    7  HPFS/NTFS
/dev/sda3            6890        7295     3261195   db  CP/M / CTOS / ...
/dev/sda4            4470        6889    19438650    5  Extended
/dev/sda5            4470        4596     1020096   82  Linux swap / Solaris
/dev/sda6            4597        6381    14337981   83  Linux
/dev/sda7   *        6382        6863     3871633+  83  Linux
/dev/sda8            6864        6889      208813+  82  Linux swap / Solaris
```

Futher ideas?

---

### Post by joft on 2007-05-01
Your partitioning is a little bit strange, but still "legal". The question now is, which partition (device) is mounted where? I guess sda6 or sda7 is your "root" partition. Hmmm, can you show as the output of:
```

df -h

```
and simply:
```

mount

```
I forgot about that in my last post, it should give us a better overview of your situation.

---

### Post by mozetti on 2007-05-01
You could try to clean up your linux partitiions using a Ubuntu LiveCD. I've had a couple crashes that messed up the journalling, so I just load up my Ubuntu Live/InstallCD and run:
```
e2fsck -f /dev/sda#
```

I run this on all my ext3 partitions. The "-f" flag forces a check even if it appears clean. Before you run it, check ```
man e2fsck
``` to look at all the options. It's very handy.

---

### Post by jaredssix on 2007-05-01
In response to Joft, the df -h out put is:
```
jared@jared-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             3.7G  2.8G  731M  80% /
varrun                502M  228K  502M   1% /var/run
varlock               502M  4.0K  502M   1% /var/lock
procbususb            502M  152K  502M   1% /proc/bus/usb
udev                  502M  152K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   34M  469M   7% /lib/modules/2.6.20-15-386/volatile
/dev/disk/by-uuid/1A50C0ED50C0D125
                       35G   28G  6.8G  81% /media/windows
jared@jared-laptop:~$ 
```

I should add (if it isn't obvious) that I've just begun to use Ubuntu--I have practically no files stored on this partition, though Thunderbird pulled in ~400 emails when it started up. (I removed Thunderbird in command line to re-enter the Ubuntu interface when I had been rejected once--I am since able to use Thunderbird, and all of the emails are there, but I can no longer find Thunderbird in the filesystem!)


and Mozetti, the mount output is:
```
jared@jared-laptop:~$ mount
/dev/sda7 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-386/volatile type tmpfs (rw)
/dev/disk/by-uuid/1A50C0ED50C0D125 on /media/windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
jared@jared-laptop:~$ 
```

Mozetti, I will burn myself a LIVECD tonight.
It appears I have the one ext3 partition, /dev/sda7 .  . . correct?

---

### Post by joft on 2007-05-01
Yes, your root ("/") filesystem is on partition (device) /dev/sda7 . And as you can see, ATM 80% are in use - so the error messages about no disk space, are more than strange. Hmmm.
BTW: It theory it should be possible to boot into _recovery mode_ and run Mozetti's fsck commands there. But anyway, if your LiveCD download is already done, use it.

---

### Post by psusi on 2007-05-01
Do you have two separate linux installs?  Because you seem to have two different linux partitions, and two swap partitions, but you are only using one.  With your root partition at 80% full, it looks like you could use some more space, but unless you were trying to install something larger than 400 megs or so, you should not have seen such an error.

---

### Post by jaredssix on 2007-05-01
I'm thinking I have two installs. I initially installed from a 6.10 disk, and found the partitioning steps more frightening for a newb than what 6.06 provides--so I installed from 6.06.

How can I get rid of the duplicated(/triplicate!) installs? I am not using them--can I wipe them out with the partitioning functioning I hope the 7.04 LIVECD will provide?

Also, Mozetti--
The e2fsck -f frightens me, with its threats of "SEVERE DAMAGE"--do you advise that I continue (by entering Y)? and do I continue on all partitions, or just the ext3?

---

### Post by psusi on 2007-05-02
Yes, you can use gparted on the livecd to repartition the drive, though if there isn't anything of value on it, you may have an easier time just reinstalling from scratch and telling the installer to format the whole disk and partition it automatically.

---

### Post by jaredssix on 2007-05-03
Sounds terrifying . . . I'll do it!

There are items of value on the Windows partition of the dual boot  (they have been backed up, but . . .)

The automatic partitioner will recognize the Windows area and leave 'er be? Or should I do it "by hand" to ensure that partition is left alone?

---

### Post by mediax on 2007-05-03
> **jaredssix said:**
> --Just tried to close out of OpenOffice, and I can't save my work. Apparantly I have insufficient free disk space at /home/jared/.openoffice.org2/user/backup . . .. I can't even find this location!

I know this is a bit late, but I suspect the reason you can't find that location is that a name beginning with a period (such as .openoffice.org2/) means that item is hidden, so you'll only be able to see it if you tick the option to view hidden items.

---

### Post by joft on 2007-05-04
> **jaredssix said:**
> The automatic partitioner will recognize the Windows area and leave 'er be? Or should I do it "by hand" to ensure that partition is left alone?

I can't say how "good" the automatic installer in this case is. But, well, doing it by hand is not that hard -  and you can tell the installer exactly what you want. First remove the 4 (old) Linux partitions and then create a swap partition and at least one further partition - the root partition (mounted on "/", e.g. with ext3). A good value is 6 or 8GB, if you want to install a lot of stuff.

If want to use the automatic partitioner, I suggest to remove the existing Linux partition with LiveCD/gparted or something else and then boot start Ubuntu installation (with autmatic partitioning). But, as I said - no experience with the automatic thing.

---

### Post by Herman on 2007-05-13
> Yes, your root ("/") filesystem is on partition (device) /dev/sda7 . And as you can see, ATM 80% are in use - so the error messages about no disk space, are more than strange. Hmmm.Probably it's too late for this now, but when the partition seems full and you don't expect it to be, it could be that th file system is not as big as the partition it is inside. This causes false readings to be reported, you know it's not really full, but it seems like it's full.
You can use a [GParted -- LiveCD]("http://gparted.sourceforge.net/"), boot it and right-click on the partition and click 'check'. That will run a file system check on the partition for you and automatically resize the file system to fill up the partition. 
It works really well in most cases, it solves the problem very easily. I hope it isn't too late to tell you that, maybe someone else will read it though.
Regards, Herman :)

---

### Post by jaredssix on 2007-05-16
Thanks everyone--
I was using only a small portion of the partition set aside for Ubuntu--I'll call it a sub-partition. I used the LiveCD gparted to sort things out . . . easier said than done.

You can't resize a partition's ultimate sub-partition to larger size. So, I copy/pasted the Ubuntu sub-partition to move it the front, where it could be expanded--but this wouldn't boot. Ultimately, I backed up the bit I had from the Ubuntu sub-partition, erased it, and installed right over it.

Perhaps a bit drastic, but she works like a charm now!

---

### Post by Herman on 2007-05-16
Okay jaredssix,
Thanks for the feedback, I'm glad you got it fixed! :)

It would have saved you a lot of time and effort if you had downloaded and made yourself a [GParted -- LiveCD]("http://gparted.sourceforge.net/") though. GParted Live CD can resize linux ext3 and reiserfs filesystems from the start of the partition. It can also do a filesystem check on a partition and a few other things as well. 
This is because the version of GParted on the LiveCD is a much more modern and advanced version that the one Ubuntu uses. GParted in the Ubuntu Live CD and [GParted -- LiveCD]("http://gparted.sourceforge.net/") are not the same thing.  It's okay to use the one in Ubuntu, it is good enough for some jobs, but it isn't fair when you then complain it was a lot of work. I'm not surprised. :)
Just so you know for next time and others reading this post will know too. I hope they give us an updated version of GParted in Ubuntu sometime soon though. Sorry for not emphasing that point enough earlier, maybe it's my fault, I didn't mean to cause you so much work. There is a big difference between '[GParted -- LiveCD]("http://gparted.sourceforge.net/")' and 'GParted in the LiveCD', they are both GParted, but they are not the same GParted.
Regards, Herman :)

---

