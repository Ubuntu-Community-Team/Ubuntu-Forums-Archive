---
title: "I need to use FSCK"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Xorg.conF on 2007-09-10
I want to know how to use fsck, not by the live cd or any other method that includes booting    from some disk.  I want to use the most powerful check, not just a quick scan for little errors.  I have two partitions, / and /home, and they are both reiserfs.  I was thinking to type something into the terminal so the  next time I boot it does it.


Thank you for all your help.

---

### Post by Tatty on 2007-09-10
According to this thread : [http://ubuntuforums.org/search.php?searchid=26936822]("http://ubuntuforums.org/search.php?searchid=26936822")

Just type this, then on the next boot fsck will run.

```
sudo touch /forcefsck
```

---

### Post by Xorg.conF on 2007-09-10
When I entered that it gave no errore when entering it into the terminal, but when I rebooted it just started normaly no check, so what happend?

---

### Post by Beggar on 2007-09-10
That is the proper way to force a fsck if you have fsck enabled on bootup.

To do this you need to edit your fstab file, and change the entry for your filesystem to end with a 1

```

sudo gedit /etc/fstab

```

find the entry for the partition you want to fsck and change it to
uuid=blah / ext3 defaults 0 0
to
uuid=blah /ext3 defaults 0 1

---

### Post by overdrank on 2007-09-10
> **Xorg.conF said:**
> When I entered that it gave no errore when entering it into the terminal, but when I rebooted it just started normaly no check, so what happend?

Hi I believe the command is 
```
sudo touch /forcefsck && sudo reboot
```

---

### Post by bodhi.zazen on 2007-09-10
Hmmm ....

Are you just curious or are you having some problems ?

A few general comments , 

Linux file systems do not need to be defragmented the way FAT/NTFS do :

	[http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html](http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html)
	[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

Second, what do you want to know about fsck ? You might want to start with the man page :

[http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

You need to run fsck on an UNMOUNTED PARTITION, which is why you run at the time of boot, before the partition is mounted, or from a live CD.

I an not aware of "powerful check" options.

---

### Post by Xorg.conF on 2007-09-10
Thanks for the posts, but I still need help referring to the enabling the fsck on boot up, dont know where your referring to with the 0 1 stuff, and no I do have a problem because it says the system is not clean when I boot in failsafe/recovery mode.  


heres what my fstab tab looks like:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=368f2e12-dfdd-4afe-b5af-8c319a0f7c83 /               reiserfs notail,noatime,data=writeback          0       1
# /dev/sda1
UUID=41e36a83-4e82-4df6-9ab1-d58f56417ca4 /home           reiserfs defaults,noatime,data=writeback        0       2
# /dev/sda5
UUID=5511523c-76e0-44bd-a3b0-93a56a9e6224 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by bodhi.zazen on 2007-09-10
Best to run from a live CD

fsck -y dev/hdxy # from a live CD, partition unmounted
[indent]# -y = auto fix[/indent]

		OR
		
fsck -rfv dev/hdxy # from a live CD, partition unmounted
[indent]# -rfv = manual fix[/indent]

so, in your case, from a live CD, 

```
fsck -y /dev/sda1
fsck -y /dev/sda2
```

If that fails, you have some serious problems, post back the output ...

---

### Post by Xorg.conF on 2007-09-10
ok well the impression I got when I used the live cd to fix things was that there wasn't anything wrong in the first place, I hope that I didn't make myself look like a fool posting up stuff that has no point, but I know what I saw in Fail-safe it said the file system was not clean and the previous posts didn't work when I tried them.

here's the output, tell me if I still have a problem thanks for all your help, all of you.  This community has yet again earned my full respect and gratitude, and I will delicate myself to help others and to benefit all who are included in this organisation for the sake of brotherhood.   


ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck 1.40-WIP (14-Nov-2006)
reiserfsck 3.6.19 (2003 [www.namesys.com](www.namesys.com))

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to [email]reiserfs-list@namesys.com[/email], **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  [www.namesys.com/support.html](www.namesys.com/support.html). **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sda1
Will put log info to 'stdout'
###########
reiserfsck --check started at Tue Sep 11 01:46:51 2007
###########
Replaying journal..
Reiserfs journal '/dev/sda1' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Comparing bitmaps..finished
Checking Semantic tree:
finished
No corruptions found
There are on the filesystem:
        Leaves 543
        Internal nodes 5
        Directories 635
        Other files 2395
        Data block pointers 87261 (315 of them are zero)
        Safe links 0
###########
reiserfsck finished at Tue Sep 11 01:46:55 2007
###########
ubuntu@ubuntu:~$ sudo -y /dev/sda2
sudo: illegal option `-y'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck 1.40-WIP (14-Nov-2006)
reiserfsck 3.6.19 (2003 [www.namesys.com](www.namesys.com))

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to [email]reiserfs-list@namesys.com[/email], **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  [www.namesys.com/support.html](www.namesys.com/support.html). **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sda1
Will put log info to 'stdout'
###########
reiserfsck --check started at Tue Sep 11 01:48:02 2007
###########
Replaying journal..
Reiserfs journal '/dev/sda1' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Comparing bitmaps..finished
Checking Semantic tree:
finished
No corruptions found
There are on the filesystem:
        Leaves 543
        Internal nodes 5
        Directories 635
        Other files 2395
        Data block pointers 87261 (315 of them are zero)
        Safe links 0
###########
reiserfsck finished at Tue Sep 11 01:48:07 2007
###########

---

### Post by bodhi.zazen on 2007-09-10
That output looks fine to me

You ran it on sda1 twice, :)

Check out sda2

sduo fsck -y /dev/sda2

---

### Post by Xorg.conF on 2007-09-10
.

---

### Post by Xorg.conF on 2007-09-10
srry that was a mistake, i ment thx for all your help, no more problems.

---

