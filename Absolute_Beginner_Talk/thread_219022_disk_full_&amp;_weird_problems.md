---
title: "disk full &amp; weird problems"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by GaijinOnline on 2006-07-19
Hi guys, I am currently having problems with my first partition, the "/" one. during the installation I've set it up to 5 Gb and my "/home" has 20Gb. Now the problem is that since the last time I boot up my computer, there is a message saying that the disk is fulll used at 99%, but I can't see how it happened. I've been installing a lot of software but those are installing in my "/home", right? 

I try to go in the "applications>Add/Remove" menu but when I try to remove an application I'm getting this kind of error
```
Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '48234508' '--set-selections-file' '/home/gaijin/tmpvqr-sd'

Unable to copy the user's Xauthorization file.
```

same thing whe I try to go in "System>Administration>Disk" it gives me another error message.
```
Failed to run disks-admin

Unable to copy the user's Xauthorization file.
```

What do I have done wrong...do I have to reformat my "/" partition?? If you guy could help me out (again) it would be awesome.

---

### Post by Kurt` on 2006-07-19
What is the output of this command?

# df -h

Should show something like this:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.8G  2.9G  7.0G  30% /
varrun                252M  168K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M   88K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-25-386/volatile
/dev/hda3              65G   14G   51G  21% /home
```

---

### Post by GaijinOnline on 2006-07-19
it give me this

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             4.6G  4.4G     0 100% /
varrun                252M   88K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  148K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  234M   8% /lib/modules/2.6.15-26-686/volatile
/dev/hda5              28G   11G   16G  40% /home
/dev/hda1              15G  2.5G   12G  18% /media/Windows
/dev/hdc              3.5G  3.5G     0 100% /media/cdrom0

```

---

### Post by risbac on 2006-07-19
When you install programs, they usually don't go in home. Home is for documents + personnal settings basically. So your software will rather go in your / partition.

To check if they are filling the disk, you can install a soft called "baobab", you will then see what takes space on your partitions. It's quite useful to see if there is not a huge file lost somewhere.

To clean some space, try ```
sudo apt-get clean
```

You can also try to remove some old kernels if you installed several.

---

### Post by philippe_carlo on 2006-07-19
```
sudo apt-get clean
``` may give you some breathing room.

To be more precise, all packages are saved in /var/apt/cache, which is cleared by the above command.

---

### Post by risbac on 2006-07-19
First first ;-)

---

### Post by avtolle on 2006-07-19
Here is a suggestion to try to open up some room (if you can get to the terminal): at the prompt, type in "sudo apt-get clean" (w/o the quotes, of course0.

---

### Post by GaijinOnline on 2006-07-19
yeah I think the autoupdate made me install like 3 kernel in one week, how do I remove them?

---

### Post by sean_ on 2006-07-19
Try reinstalling Ubuntu, because you made your linux HD 4 gb <_<

---

### Post by Sonofmoog on 2006-07-19
With a disk that's 100% full, your first priority is creating some wiggle room.  Do follow the suggestions of others in this thread about clearing out your cache.  I picked up about 300 MB from just that.  

If you installed wine, I'd remove it.

```
sudo apt-get remove wine
```

Make sure your trash is empty, and do so for both $USER and root .. 

Doing one or more of these should free up enough space where you can then load Synaptic and do a more orderly uninstall ..

---

### Post by deuce_ace on 2006-07-20
I am in a similar situation as the original poster.  I could easily clear up a bit of space but I am stuck with the default 4.5 gig root partition from setup and need something to change.  I was curious if there is an easy way to switch where my new packages and programs install to in order to keep the root partition as a system files only partition? (I have tons of free space on other drives).  Thanks!

---

### Post by zanoman on 2007-08-20
Hi,
I reopen this topic since I also have strange disk behavior with ubuntu feisty 7.04:
I had to install a second ubuntu on another disk to see what's going on my 2 partitions:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              15G   15G     0 100% /media/disk
/dev/sda2             139G   91G   41G  69% /media/disk-1

at normal startup sda1 is mounted as /
and sda2 as /home

now when I check with application>accessories>disk usage analyser (baobab) it says that disk (sda1) is 100% full at 4.4GB (!) and disk-1 (sda2) is 100% full at 90GB.
GParted says (like df -h) that sda1 (14.44GiB) is full (18MiB unused).

Where are the 10GB missing??

---

### Post by asmoore82 on 2007-08-20
> **deuce_ace said:**
> I am in a similar situation as the original poster.  I could easily clear up a bit of space but I am stuck with the default 4.5 gig root partition from setup and need something to change.  I was curious if there is an easy way to switch where my new **packages and programs** install to in order to keep the root partition as a **system files only** partition? (I have tons of free space on other drives).  Thanks!

There seems to be a philosophical disconnect here ...

UNIX systems are multi-user systems from the ground up.
Therefore, multiple users can access "installed" programs.
Therefore, properly installed programs are "system wide."

Ergo, Programs ARE System Files.

:KS

However, in an effort to be helpful, if you really want to go up to more advanced partition scheme,
I would say that you need more that just free space, you need a whole partition to devote to the cause.
Then, you copy the entire contents of '/usr' to this partition and set it to mount at '/usr'

---

### Post by zanoman on 2007-08-20
OK,

I looked for files more than 10MB (including hidden files) on sda1, only 32 appeared, nothing above 38MB. 

As I have unformated space on sda (250GB HDD), I made another 15GB paritition (sda3) and copied everything from sda1 (all partitions are ext3):
 cp -fR /media/disk/* /media/disk-2/

it fills ... 15GB (disk analyzer and nautilus didn't see it!! wow)

Now I'm sure it's file related not partition related.
So I deleted folders one by one on disk-2 and checked free space with "df -h"

it's in var/archives: on original disk it says it's unreadable folder. Then after some "fixing-by-itself" (don't ask me how I don't know, journaling?), I see a 9.4GB file ... that my recently installed backup manager created :-(
I think it simply created a backup loop (bakcup files including the backup file itself ... forever) until filling the partition (and maybe breaking the copy process).

Didn't get a message alert from system or backup-manager package...
End of investigation, [SOLVED]

---

### Post by Lylex11 on 2008-05-06
Hi, I installed backup manager and set archive folder to /media/sda4. When I activated backup-manager I forgot to mount /media/sda4 first. I now have a MASSIVE archive somewhere, but I can't find it. I've searched for it everywhere. Baobab reports I have 15.8GB files, but says I have used 33.0GB of space - I'm guessing that's my missing (hidden) backup archive. But baobab doesn't show where the archive is. Can anyone help me delete the archive files? Thanks

---

### Post by Joe_Ipsen on 2008-06-05
I have emptied the trash (freed up 6.6 GB) and have run baobab, but cannot explain what is using up all of my diskspace.

This machine is primarily used to download torrents using uTorrent running on Wine.  As my wife is the primary one using the system, she selects "delete .torrent and data".  This does not put the file into the trash so I suspect that the files are not actually being deleted, but I cannot see them so I'm not sure how to verify this.

I have removed/updated Wine but still am not sure how to reclaim or identify what is using all of the disk space.  The location where she places the downloads only has about 6 GB of files in it.

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             227G  209G  6.4G  98% /
varrun                474M   92K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   88K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   34M  440M   8% /lib/modules/2.6.22-14-generic/volatile

Anyone have any other recommendations on finding out what is going on with this space?

---

### Post by Joe_Ipsen on 2008-06-08
Anyone have any suggestions?  We're out of those 6 Gb that I freed up.

-Joe

---

