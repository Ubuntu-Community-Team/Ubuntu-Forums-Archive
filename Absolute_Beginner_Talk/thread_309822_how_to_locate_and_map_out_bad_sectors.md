---
title: "how to locate and map out bad sectors"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by moshuptrail on 2006-11-30
I'm pretty sure I've got some bad sectors on one of my partitions, an ext3 partition with /home on it. I'm getting messages like:

```
[17180659.672000] ide: failed opcode was: unknown
[17180659.672000] end_request: I/O error, dev hda, sector 110545735
[17180665.696000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17180665.696000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=110545738, sector=110545735
[17180665.696000] ide: failed opcode was: unknown
[17180665.696000] end_request: I/O error, dev hda, sector 110545735
[17180671.848000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17180671.848000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=110545738, sector=110545735
[17180671.848000] ide: failed opcode was: unknown
[17180671.848000] end_request: I/O error, dev hda, sector 110545735
```

What Linux utility should be used to scan the partition for bad sectors and map them out?  Does it have to be un-mounted?  If so, will I be able to log in using Terminal when my home directory is missing?

---

### Post by bapoumba on 2006-11-30
Hi,
well, looks (to me, I may be wrong) like your partition  is in bad shape. Are your backups up to date ? If not, backup all your important stuff, from a live cd if you got one.
btw, what is on hda ? do you have a separate /home partition ?

**$ sudo shutdown -F -h now** will force the system to perform an fsck next boot up (see **man fsck** for details). 
Your partition will be mounted read only (it is mandatory), you'll get a screen explaining all of that, and how to remount it once the fsck is performed.

Please document yourself about fsck ;)

---

### Post by xyz on 2006-11-30
> **moshuptrail said:**
> I'm pretty sure I've got some bad sectors on one of my partitions, an ext3 partition with /home on it. I'm getting messages like:

```
[17180659.672000] ide: failed opcode was: unknown
[17180659.672000] end_request: I/O error, dev hda, sector 110545735
[17180665.696000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17180665.696000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=110545738, sector=110545735
[17180665.696000] ide: failed opcode was: unknown
[17180665.696000] end_request: I/O error, dev hda, sector 110545735
[17180671.848000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17180671.848000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=110545738, sector=110545735
[17180671.848000] ide: failed opcode was: unknown
[17180671.848000] end_request: I/O error, dev hda, sector 110545735
```

What Linux utility should be used to scan the partition for bad sectors and map them out?  Does it have to be un-mounted?  If so, will I be able to log in using Terminal when my home directory is missing?

I had exactly the same type of errors a few months ago; sorry but my HD was dead. Tried everything to "save" it but to no avail.
Try what bapoumba says to do! You never know.
[Recover Data From a Dead Hard Drive]("http://www.ubuntuforums.org/showthread.php?t=308821&highlight=hard+drive+dead")

---

### Post by moshuptrail on 2006-11-30
I've only got one physical disk and it's pretty well backed up. 
There are several partitions:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda5       none            swap    sw              0       0

```

Fortunately I'm only getting errors from some files that I just added to /home - possibly in a physical area of the disk that has never been used before.

---

### Post by bapoumba on 2006-12-01
You can try to fix it with fsck or e2fsck (as it is ext3). Please read the man for fsck and e2fsck.
Be aware that you may loose data !!

Logout from your session.
<CRTL> + <ALT> + F2 will get you to a non-graphical session.
remount your /home read only : **sudo mount -n -o remount,ro /dev/hda7**
run e2fsck : **sudo e2fsck -f -y /dev/hda7**
note the error messages if applicable
remount your /home read-write : **sudo mount -n -o remount,rw /dev/hda7**
go back to the graphic session : <CTRL> + <ALT> + F7

---

### Post by The Mekon on 2006-12-01
I have had the same problems which I investigated using the advice given in this [link]("http://www.linuxjournal.com/article/0193").

If you use badblocks as instructed you can locate bad areas and then edit them out.

Unfortunately my hard disk was beyond redemption.

Brian

---

### Post by moshuptrail on 2006-12-02
I think my HD has had these bad sectors for a long time.  When I tried to re-size the orginal NTFS partition to load Ubuntu 6 months ago, I had problems because there were bad blocks.  I failed at that time to scan my Linux partitions for bad blocks.  Bad move.  ](*,)
This time it started when I was adding a whole bunch of data onto the HD and filled it beyond what it's ever been filled before.

At any rate, I ran fsck as follows:

1. I couldn't do it from a live system as suggested by bapoumba.  It kept saying: "/home is in use" so  I simply booted off the Gparted Live CD, opened an aterm, and worked from the command line there.
2. e2fsck -f -y /dev/hda7
3. fsck -cc -C /dev/hda7 (this took about 10 hours)
4. fsck -cc -k -C /dev/hda7 (another 4-5 hours)
5. e2fsck -f -y /dev/hda7

This seemed to clean it up pretty well, BUT, when I re-booted Ubuntu the contents of /home were completely gone!  No home directory to log in to, so now I can't get the Gnome desktop going.  It won't let me log in.  I can break out to a command prompt, but I'm not sure how to re-create all the dot-files in my home directory.  They were not backed up.

I was pretty sure the -cc would do a non-destructive read-write check.  In fact, fsck announced it was doing a non-destructive check.  It didn't give any indication it was clearing the inode list. (that I saw - there were a lot of messages)

(The -k is supposed to keep the existing bad block list and add to it)

Not sure what I did wrong.  Any ideas?

I can always re-install Ubuntu and reload the files from backup, but I'd like to learn something from this.

---

### Post by bapoumba on 2006-12-02
Did you do it on your **read only** mounted /home ? Please check post #5 procedure. I think that is the problem. Sorry for not pointing out this more precisely :/ Feeling quite bad about it.

So do not boot up your system, each time you have disk access, you are loosing more data. Check your partition with a live cd for ex., mount it **read only** and see what you can get out of it.

---

### Post by Ocxic on 2006-12-02
try doning a zero fill or low level format of your drive, with the manufactures utility or witht he ultimate boot cd. i had this exact same probleme today, and i can tell you it's only goin to get worse.

---

### Post by moshuptrail on 2006-12-02
By booting the live CD, /home was not mounted at all when I did this.  The steps I listed above are exactly what I did.

However, fsck says it is doing "non-destructive" checking.  Does it lie?

Another question: If /home is mounted read-only, how can fsck clone the bad sectors and add them to the Bad Block List inode?

note to Ocxic: Can't low-level format.  We are talking about one 30G partition on an 80G HD.  There are 4 other partitions including Windows XP NTFS which I kinda need.  None of those partitions are showing problems.

---

### Post by bapoumba on 2006-12-03
Well, my knowledge kinda stop here, I'm sorry  :/

But, this could be that your partition table or the /home file system are not declared (?) properly. Please check man fdisk, mkfs and/or parted.

Could a ubuntu/debian administration wiz stop by ?
And I agree, this is a good way to learn something ;)

---

### Post by moshuptrail on 2006-12-03
Well, I ended up re-installing everything.  BUT first I ran fsck to check for bad blocks on partitions / and /home.  I booted from the Gparted Live CD and opened an aterm and ran the following command:

```

e2fsck -c -k -v -y /dev/hda7

```

explanation:
-c does a read-only test of each block
-k keeps any existing bad block listed in the bad block list
-v verbose: prints a summary at the end
-y answer yes to all questions - run unattened

This command took about 10 hours to scan a 23Gb partition.  I ran it twice and it showed the same number of bad blocks the second time.

Next, I ran the following command on /home twice.
```

e2fsck -cc -k -v -y /dev/hda7

```

explanation:
-cc does a "read-write non-destructive test" according to the man pages
    After my earlier problems, I don't trust this.  I did not run it on the / file system.

comments:
According to everything I was able to find, you should not run fsck on a mounted partition.  If you try, it gives you dire warnings.  I heeded those warnings and ran it on unmounted partitions.

The badblocks program seems to be incredibly dumb.  It does not seem to heed it's own bad block list and re-tests the same bad blocks every time you run it.  When it hits a bad block it stops and sits there testing, sometimes up to a 1/2 hour on a single bad block.  By my reasoning, if it takes more than 2 retries to read a block, mark it bad and move on!  Does anyone know about the badblocks program?

---

### Post by bapoumba on 2006-12-05
Hi moshuptrail,

so I emailed a friend of mine, one of these debian wiz, and linked your thread ;)

Basically, his answer was :
[QUOTE=my friend]This probably was a hardware problem indeed. With **e2fsck -cc**, if there were badblocks, the situation is almost desesperate. When this kind of problem happens, it is better to check with the hard drive manufacturer tools to see if the drive is still in shape, or use [smartmontools]("http://smartmontools.sourceforge.net/BadBlockHowTo.txt").
If a test with badblocks is positive, it will take forever, will give an infinite bad sector list. Drive manufacturer tools are better for that.[/QUOTE]

I am not sure what you can make out of this (as far as the explanation goes).

---

### Post by moshuptrail on 2006-12-05
What your friend is saying may be correct, but is not consistent with my experience.  Although it took 10 hours to complete, badblocks only reported 236 bad blocks - out of a total of 5.7 billion.  I discovered later that the reason it wiped out the contents was that there were several bad blocks in the inode list itself.  I have re-installed xubuntu and loaded a bunch of data onto the filesystem in question.  If I run into difficulty it will be when I try to run a backup and can't read a block.  I'll let you know.

Meanwhile, I have ordered a new HD.

---

### Post by bapoumba on 2006-12-06
> **moshuptrail said:**
> Meanwhile, I have ordered a new HD.
Wise decision ;)

---

