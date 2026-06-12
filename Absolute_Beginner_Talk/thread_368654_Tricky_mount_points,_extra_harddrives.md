---
title: "Tricky mount points, extra harddrives"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by edward4130 on 2007-02-23
Here goes.... I Installed a full ubuntu mythtv system and am loving it.  It is all running on a 320 IDE drive and I used a single 500SATA drive and mounted it as /var/lib/mythtv.  Workes great so every recording goes to the new SATA.

New question.  I want to use a third drive (500SATA)- sdb1 ,that is already formatted and recognized as two other mountpoints, both are in /var/lib/ one is mythdvd and the other mythvideo.  I would just mount all of /var/lib/ on the drive but obviously I'm doing /mythtv on sda1, as well there is much more in this that I would not like to offload form the drive. Is there a way to do this?
My second drive fstab clip:
```
/dev/sda1       /var/lib/mythtv     ext3    defaults    0   2 
```

can I do this?:
```
/dev/sdb1       /var/lib/mythvideo     ext3    defaults    0   2
/dev/sdb1       /var/lib/mythdvd     ext3    defaults    0   2
```

I know I can make it two partitions but i wanted them to use the space flexibly becuase one will likely be large while the other may be large the next week.

Thanks in advance, I know it is slightly more advanced, but I could not find the answer in a search.

-Edward

---

### Post by taurus on 2007-02-23
Why not have this line in /etc/fstab

```
/dev/sdb1       /var/lib/mythvideo     ext3    defaults    0   2
```
and link /var/lib/mythdvd to it, /var/lib/mythvideo?

```
sudo ln -s /var/lib/mythvideo /var/lib/mythdvd
```

---

### Post by bernied on 2007-02-23
If I understand you correctly, maybe this is what you want:
```
/dev/sdb1                     /var/lib/sdb1          ext3    defaults    0   2
/var/lib/sdb1/mythvideo /var/lib/mythvideo none bind 0 0
/var/lib/sdb1/mythdvd   /var/lib/mythdvd    none bind 0 0
```
This mounts the whole partition at /var/lib/sdb1, then mounts those directories at /var/lib/mythvideo and /var/lib/mythdvd, using the bind option.

Your choice of mountpoints is quite novel to me. In my experience drives are usually mounted at /mnt or /media. This of course just an arbitrary standard and you can do what you like on your own system, but I am curious...

---

### Post by edward4130 on 2007-02-23
just did that and it was not foolproof, or one of us was confused.

now I have a folder "alias" inside of mythtdvd that is mythvideo, the system sees the directory for mythdvd as only 187GB avaialble (must still be on hd3) the mythvideo is 435GB (definitely is on sdb1) I wanted both directories to use sdb1 as free space.  Is this still possible?

-Edward

---

### Post by bernied on 2007-02-23
Which exactly did you try - the two options above are quite different. One or both of us (Taurus and I) are also confused. What is your fstab now?
Also the output from 
```
mount
```
and
```
df -h
```
might be useful

Can you explain a bit more clearly what you want?

---

### Post by edward4130 on 2007-02-23
Ok tried the first option and now on to the second for clarification.  I was not attempting to mount the full drive.  If so I would mount it in /media/ like you are supposed to.  I only want the space to be used by the mythdvd and mythvideo programs, also to have the full pace of the drives flexible for the two directories.

-Edward

Thanks for the help so far i do get it, just not sure on the excact way to get there.

---

### Post by edward4130 on 2007-02-23
My "mount" output:
```
edward@mediacenter:/var/lib/mythdvd$ mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-386/volatile type tmpfs (rw)
/dev/sda1 on /var/lib/mythtv type ext3 (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /var/lib/mythvideo type ext3 (rw)

```
My "df -h" output:
```
edward@mediacenter:/var/lib/mythdvd$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1             291G   89G  188G  33% /
varrun                474M  144K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   18M  456M   4% /lib/modules/2.6.17-11-386/volatile
/dev/sda1             459G   60G  376G  14% /var/lib/mythtv
/dev/sdb1             459G  201M  435G   1% /var/lib/mythvideo
/dev/sdc1             1.9G  224K  1.9G   1% /media/BLUE2GB_02
```
As you can see above my sdb1 now has /var/lib/mythvideo.  I want the sdb1 partition to hold both (and only) the /var/lib/mythvideo and /var/lib/mythdvd as those mountpoints for the mythtv-plugins to work as they natually do.

Sorry to confuse things, I'm sure this is not the average useage of mountpoints.

-Edward

---

### Post by edward4130 on 2007-02-23
Here is what I did and it was actually the original part of the post.  I added the mountpoints of both directories to the sdb1 and it actually worked.  Open space and each doesn't know one another, and I belive mythtv will see it just as if both were on the original harddrive.

My fstab complete:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=25b83f09-cc6c-4225-a083-3fc3033764a3 /               ext3    defaults,erro$
# /dev/hdc5
UUID=a13a2096-df6a-4435-b191-adc7a7974789 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /var/lib/mythtv ext3    defaults        0       2
/dev/sdb1       /var/lib/mythvideo      ext3    defaults        0       2
/dev/sdb1       /var/lib/mythdvd        ext3    defaults        0       2


```

Thanks for the input guys, we got it done.  Now I'm off to rebuild a MacG3 laptop I'm using right now as an Ubuntu.  There may be a thread on this later. lol.

-Edward

---

### Post by bernied on 2007-02-23
Have you tested this? I think if you create a file in /var/lib/mythvideo it will appear in /var/lib/mythdvd.
```
touch /var/lib/mythvideo/test_it_now
cd /var/lib/mythdvd
ls
```
Or is this exactly what you wanted?

My first way will give you two separate folders on that drive, but you would have to create them, after the first mount, but before the second and third could be done.

---

