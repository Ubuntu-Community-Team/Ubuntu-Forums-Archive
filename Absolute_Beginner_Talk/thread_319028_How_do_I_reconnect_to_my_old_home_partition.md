---
title: "How do I reconnect to my old /home partition?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by eyemeansit on 2006-12-14
I installed Kubuntu 6.10 over the top of my former Mepis 6.0. My old /home partition from Mepis can't seem to be found anywhere. It was /dev/hda2, and I assume it still is, but I can't seem to navigate there.

Here's what I did during installation:
I had these partitions:
hda1 was Windows XP
hda2 was /home
hda3 was swap
hda4 was Mepis

Using the live Kubuntu 6.10 CD, I deleted the swap and Mepis partitions, and then installed, telling the installer to automatically create partitions as needed using the largest contiguous free space.

Any ideas would be greatly appreciated!

---

### Post by Sef on 2006-12-14
> I installed Kubuntu 6.10 over the top of my former Mepis 6.0. My old /home partition from Mepis can't seem to be found anywhere. It was /dev/hda2, and I assume it still is, but I can't seem to navigate there.


Open Konsole, then type

kdesu fdisk -l

that will show you what partitions you have.  If you want some more help, then just copy and paste the output of fdisk -l here.

---

### Post by eyemeansit on 2006-12-14
Here's the output of the suggested command:


les@les-laptop:~$ kdesu fdisk -l
kdesu: Unknown option '-l'.
kdesu: Use --help to get a list of available command line options.
les@les-laptop:~$

Not what we're hoping for, I assume!

---

### Post by goatflyer on 2006-12-15
KDE doesn't have sudo?!?

```

sudo fdisk -l

```

The -l is for sure a valid option to fdisk.  It means list the partition table from the (no disk specified so it chooses /dev/hda)

---

### Post by eyemeansit on 2006-12-15
That's better: (the "sudo fdisk -l" command)

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20480000+   7  HPFS/NTFS
/dev/hda2            3642        7296    29358787+  83  Linux
/dev/hda3            2551        3592     8369865   83  Linux
/dev/hda4            3593        3641      393592+   5  Extended
/dev/hda5            3593        3641      393561   82  Linux swap / Solaris

Partition table entries are not in disk order

So, yes, it appears my hda2 partition is still there and intact. Now... how to get Kubuntu to use it as the /home directory?

Thanks in advance!

---

### Post by steve.horsley on 2006-12-15
First run **df -h** to see where your system is. Hopefully it's on /dev/hda3 (4 Gig). Otherwise it's on /dev/hda2 (15 Gig) which is where your /home **was**.

Assuming your /hda2 is still instact and unused, add a line to /etc/fstab like this:
```
/dev/hda2  /home           ext2 defaults        0       2
```
then reboot.

---

### Post by eyemeansit on 2006-12-15
Here is the output of "df -h":

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             7.9G  2.9G  4.7G  38% /
varrun                601M   84K  601M   1% /var/run
varlock               601M     0  601M   0% /var/lock
procbususb             10M  124K  9.9M   2% /proc/bus/usb
udev                   10M  124K  9.9M   2% /dev
devshm                601M     0  601M   0% /dev/shm
lrm                   601M   18M  584M   3% /lib/modules/2.6.17-10-generic/volat                   ile

so, I assume that /dev/hda3 is my current Kubuntu system, and /dev/hda2 is my old /home partition. I will try the suggested change to fstab and let you know what happens...

Thanks!

---

### Post by szf on 2006-12-15
Alternately, leave /etc/fstab alone until you're sure. 

Start with ```
$ sudo mkdir /mnt/tmpmnt
``` and follow with ```
$ sudo mount /dev/hdx2 /mnt/tmpmnt
``` where 'x' is the IDE controller reference (i.e. hda or hdb; hdc or hdd; etc etc.)

You may need to specify the filesystem type with the -t switch, e.g. ```
$ sudo mount -t reiserfs /dev/hdx2 /mnt/tmpmnt
```.

---

### Post by eyemeansit on 2006-12-15
> **eyemeansit said:**
> I will try the suggested change to fstab and let you know what happens...

I copied and pasted the new fstab line exactly as shown (in steve.horsley's post), and now it goes through bootup until login screen, and after logging in it gives me a little white error window in the top left corner that says "Could not start kstartupconfig. Check your installation." When I click the "OK" button, it takes me back to login, and then back to the error message, and then back to login, etc.

I am now using the live CD, trying to figure out how to temporarily mount /dev/hda3 so I can get back to /etc/fstab and take that line out... then I shall try the next suggestion...

Thanks again!

---

### Post by eyemeansit on 2006-12-15
Got fstab back to this original shape, now I shall try "szf's" suggestions.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=347ec6a8-1933-4c21-b2ab-b1d6122c77ee /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0fc2129c-da17-412b-ab08-0eb99de2e585 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by eyemeansit on 2006-12-15
OK, now I have my old /home partition mounted at /mnt/tmpmnt... This is big progress! The data is safe, and visible/accessible. This is good!

And now... how to get Kubuntu to use this as /home...?

Thanks again to all who have helped me along on this! Y'all are a blessing from above!

---

### Post by goatflyer on 2006-12-16
non-dangerous experiment:

(do not modify /etc/fstab)

```

sudo umount /mnt/tmpmnt
sudo mount -t reiserfs /dev/hdx2 /home

```

are you still alive?  check your graphical environment, check your trash can, etc.

Then do ctl-alt-backspace, this will restart your xserver, you will relogin (hopefully still using the 'new' old home)

did it boot properly?  recheck all directories.
do
```

df -hT

```
to verify you are still using the /dev/hdx2 partition on /home.

If all this is good, then retry the /etc/fstab entry described earlier.


If there is a problems, what it means is possibly:
there are files in the new /home partition that kde can't live without, you will need to copy them onto your 'old' partition so that kde will be happy using the old.
 ---- OR -----
there are some files on the old /home partition that confuse the current kde.

---

### Post by eyemeansit on 2006-12-17
Well, the end of the story is this...

I wound up copying /dev/hda2 to an external hard drive, booted up from the Live CD, deleted all partitions on the master hard drive except for Windows XP, and did a fresh install of Kubuntu 6.10, using all the freed up space. Then I copied my data back into the new /home folder, (with the exception of the .kde folder because I didn't want conflicts with the new version of KDE).

Anyway, I am now happily enjoying the fine Kubuntu 6.10 distro, with all my data intact in the new /home folder. I still have some house cleaning to do, installing some apps, configuring some things, etc., but I'm a happy camper again! 

Thanks much to sef, goatflyer, steve.horsely, and szf for caring about the newbies!

---

### Post by eyemeansit on 2006-12-19
Just a quick follow up... Most of the housecleaning is done... things are humming along beautifully! I have even got suspend and hibernate, which is something I haven't had since I left Windows XP behind! I enjoyed Mepis, but I'm thinking I'm going to like Kubuntu even better! Thanks!

---

