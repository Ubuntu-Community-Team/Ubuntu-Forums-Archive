---
title: "External harddrive input/output error"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by rtrdom on 2008-01-20
I have Gutsy Gibbon version installed. Also, ntfs-3g is installed and updated. Am trying
to get read-write for an external harddrive. The harddrive can be mounted, and can
read a lot of stuff there. Can CD to it by cd /media/usbdisk. When in /media/usbdisk
trying to ls -l. Cannot. Result is " ls: .: Input/output error"
df -h yields
 Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             107G  8.8G   93G   9% /
varrun                633M  100K  633M   1% /var/run
varlock               633M     0  633M   0% /var/lock
udev                  633M   84K  633M   1% /dev
devshm                633M     0  633M   0% /dev/shm
lrm                   633M   34M  599M   6% /lib/modules/2.6.22-14-generic/volatile
/dev/sdc1              38G   20G   18G  54% /media/usbdisk
/dev/sdc1              38G   20G   18G  54% /mnt
/dev/sdb1              38G   20G   18G  54% /media/disk-1
   Any help appreciated.

---

### Post by lgambett on 2008-01-20
in the df output you reported /dev/sdc is present twice, as if your hdd was mounted on /mnt and /media/usbdisk. This should not be possible; could you check ?

---

### Post by rtrdom on 2008-01-20
Thank you for the response.
I just did a df -h and it is indeed listed twice. OK, it is now listed only once. Had to
do a sudo umount on it. Still cannot get there as you can see from this.
jim@Bravo:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             107G  8.8G   93G   9% /
varrun                633M  100K  633M   1% /var/run
varlock               633M     0  633M   0% /var/lock
udev                  633M   84K  633M   1% /dev
devshm                633M     0  633M   0% /dev/shm
lrm                   633M   34M  599M   6% /lib/modules/2.6.22-14-generic/volatile
/dev/sdc1              38G   20G   18G  54% /media/usbdisk
/dev/sdb1              38G   20G   18G  54% /media/disk-1
jim@Bravo:~$ cd /media/usbdisk
jim@Bravo:/media/usbdisk$ ls -l
ls: .: Input/output error

Just tried cd to /media/usbdisk-1 and then ls-l.  All the files are listed there.
Will try ntfs-3g there.

---

### Post by rtrdom on 2008-01-20
OK. while in /media/disk-1 did the following with result shown.
:/media/disk-1$ sudo ntfs-3g /mnt/win -o force
ntfs-3g: No mountpoint is specified

The statement ntfs-3g /dev/sdc1 yields "No such file or directory"
Another try:  ntfs-3g /dev/sdc1 /mnt/media/disk-1/win -o force
Failed to access '/dev/sdc1': No such file or directory

Thanks for helping.

---

### Post by rtrdom on 2008-01-20
Moderator, please remove this post. Problem solved.

---

### Post by cmittle on 2008-01-21
Could you please post some details to  the solution to this problem you were having, how you figured out what was wrong, and how to fix it?  I'm sure this will come in handy for someone else trying to use ntfs-3g later on.  

Thanks,
Cory

---

### Post by rtrdom on 2008-01-26
Cory, the problem wasn't really "solved". I removed the harddrive, did a couple things,
discovered I was using wrong command (sdc1 wasn't there) so I removed everything
and did a total wipe of the machine and started all over. On the way, I have removed
my ipw2100 driver for the wireless portion of my computer and am now trying to get
that working before I attempt the ntfs-3g thing again. Lesson: don't do a wipe/reinstall
unless it is absolutely necessary (paraphrased: if you're alive, it probably isn't necessary.)  I'll be back when I have the other problems solved and when I get it done
I'll post again.  
Thank you for your interest and help.

---

