---
title: "Mounting a partition as /usr"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by wortel on 2007-02-20
Hi..

I left a large partition open when I installed Ubuntu, to use as my data disk. I want to set it so that basically everything is on that folder, and new applications installed using the synaptic package manager etc. go there as well.  After asking around a bit I was told to move /usr to the root of the partition, and remount the partition as usr. Is this the right way to go about it? And what should my entry be in fstab? currently I have

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda6
UUID=351cb1f7-0fbf-4809-a09f-9cd9e80a2af9 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda8
UUID=8dd50b6e-358d-4175-80b9-3990a410a866 /media/hda8 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda7
UUID=cb644fdd-d750-4243-a8ab-929eda5c4bfa none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda5 /media/windata auto users,umask=000,atime,auto,rw,nodev,exec,nosuid 0 0
/dev/hda8       /usr    auto    default   0       0

```

but this actually causes the machine to fail to boot. After loading for a while it simply hangs at a screen where the drives had been checked, but there aren't any error messages.

Any help would be appreciated, thanks in advance :)

---

### Post by igknighted on 2007-02-20
I think /usr needs to be on the root partition because there are binaries there that are needed to boot.  I think the person may have been suggesting you put /home on a separate partition instead (/usr is "unix system resources", not "user").

EDIT: You also have two entries for /dev/hda8.  I think this will screw the computer up too.  Erase the second one and edit the top one to say what you want.

---

### Post by m94mni on 2007-02-20
> **wortel said:**
> Hi..

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda6
UUID=351cb1f7-0fbf-4809-a09f-9cd9e80a2af9 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda8
UUID=8dd50b6e-358d-4175-80b9-3990a410a866 /media/hda8 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda7
UUID=cb644fdd-d750-4243-a8ab-929eda5c4bfa none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda5 /media/windata auto users,umask=000,atime,auto,rw,nodev,exec,nosuid 0 0
/dev/hda8       /usr    auto    default   0       0

```

but this actually causes the machine to fail to boot. After loading for a while it simply hangs at a screen where the drives had been checked, but there aren't any error messages.

Any help would be appreciated, thanks in advance :)

You mount /dev/hda8 twice. One time as /usr, one time as /media/hda8. Note that there are (at least) two ways to refer to partitions - by /dev/ name or by UUID.

So, remove the /media/hda8 line, and try again. Also, I'd copy the options line "nouser,defaults,atime,auto,rw,dev,exec,suid" to the /dev/hda8 line.

Also, what's the /dev/ line? I would remove that.

Actually, I've been using linux since 1995, and I've started using a single partition for my desktop/laptop systems. It might be reasonable to keep a separate /home partition, but I don't feel a great need. Why do you want /usr separately?

---

### Post by m94mni on 2007-02-20
> **igknighted said:**
> I think /usr needs to be on the root partition because there are binaries there that are needed to boot.  I think the person may have been suggesting you put /home on a separate partition instead (/usr is "unix system resources", not "user").


The FHS (filesystem hierarchy standard) actually specifies that "/usr, /opt, and /var are designed such that they may be located on other partitions or filesystems.".

The system should be able to boot without /usr (and Ubuntu is.)

---

### Post by igknighted on 2007-02-20
> **m94mni said:**
> The FHS (filesystem hierarchy standard) actually specifies that "/usr, /opt, and /var are designed such that they may be located on other partitions or filesystems.".

The system should be able to boot without /usr (and Ubuntu is.)

Thank you for the correction.  It must be the two entries in fstab that are causing the issues.

---

### Post by wortel on 2007-02-20
> **m94mni said:**
> You mount /dev/hda8 twice.



err, yes. Was aware of that, I had fixed that, but posted my backed up fstab after recovering with the last line added in, and didnt erase the previous one by accident when posting  :)

> 
Actually, I've been using linux since 1995, and I've started using a single partition for my desktop/laptop systems. It might be reasonable to keep a separate /home partition, but I don't feel a great need. Why do you want /usr separately?

I had assumed it was 'user', and just wanted my linux base seperate from installed apps etc.

I guess I can just mount it as home, but can I set that apps that are installed via apt-get,synaptic package manager etc. to install to there, rather than on my root partition?

---

### Post by m94mni on 2007-02-20
> **wortel said:**
> err, yes. Was aware of that, I had fixed that, but posted my backed up fstab after recovering with the last line added in, and didnt erase the previous one by accident when posting  :)

I had assumed it was 'user', and just wanted my linux base seperate from installed apps etc.

I guess I can just mount it as home, but can I set that apps that are installed via apt-get,synaptic package manager etc. to install to there, rather than on my root partition?

This will not do what you want. It's a common mistake when coming from windows that it's easy to separate "base" from "apps", but you won't be able to do that easily. /usr is certainly part of "base", AND contains apps. Thanks to the easy package management, it's very easy to reinstall a set of apps if you ever do a reinstall (that is *very* seldom necessary, though).

First, what went wrong? A) Did you format /dev/hda8? B) Did you copy the contents of the old /usr into that partition?

Second, what about /home? That contains all user files, settings and documents. but no apps. Might be good to keep separate if you think you might want to reinstall later, or install another distribution, etc. But it's mostly not necessary. If I ever need to do any of that, I usually copy everything to an external HD first...

If you *do* want to do /home on /dev/hda8, you need to:

1. Format /dev/hda8
2. Move contents of current /home to that partition after mounting it
3. Modify fstab to map /dev/hda8 to /home
4. Reboot.

Also, in any case, make sure the directory /usr or /home exists before trying to mount anything on it. Mounting WILL NOT create the directory.

---

### Post by wortel on 2007-02-20
I guess in retrospect it was a mistake to have a seperate partition for root and data, would've been so much simpler to just make one big partition. Will I be able to merge the two partitions now (using gparted?), and at least not lose the data on root partition (seeing as the other one is effectively empty atm). Otherwise I would have to reformat and reinstall which would just be such a waste as I just got everything set up how I want it :)

Or what would be the best way to mount/structure my large partition so that I can get the most data on it?

Thanks for the help so far.

---

### Post by wortel on 2007-02-20
> 
First, what went wrong? A) Did you format /dev/hda8? B) Did you copy the contents of the old /usr into that partition?

I've actually got the partition to work as /usr since. Just cp -a 'ed everything onto it, added it to fstab and rebooted.

Sorry for double post. clicked quote instead of edit :)

Edit again: I see I have my swap partition in between my root partition and data partition (using qparted). I'm guessing this is a bad thing...?

---

### Post by m94mni on 2007-02-20
For resizing, boot from a live CD and check this:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

I assume qparted is similar. So, first make sure you take out all the data you need from the extra partition and put it on the right one, then reboot from LiveCD, delete data partition, resize/move other partion, make sure fstab is correct, reboot.

Swap can be placed anywhere, does not really matter. Some always place it near the end, as disk access is theoretically faster there, but I don't think it really matters (and faster disk is useful for other things...)

If you have only one big partition there is no real need to structure it. ext3 does not need defragmenting (it's automatic), and the package manager keeps track of installed programs etc. 

So I suggest to just mount it as / and be done with it... :-)

---

### Post by wortel on 2007-02-20
Sounds good.

Just one issue - I won't lose any data currently on root if I increase it's size? It's not crucial but will save a lot of effort.

---

### Post by m94mni on 2007-02-20
> **wortel said:**
> Sounds good.

Just one issue - I won't lose any data currently on root if I increase it's size? It's not crucial but will save a lot of effort.

I don't think so.... at least not if it's ext3 (which it seems to be). Worth a try!

---

### Post by wortel on 2007-02-20
I think it worked! I just rebooted and changed my partitions with my live CD. I had edited my previous large partition out of fstab, but didn't change anything else, was stressing a bit at reboot but I think because they are being mounted by UUID it mounted them just fine. I'll play around for a bit and see if anything broke. So far so good though :)

Thanks a lot for your help.

---

### Post by m94mni on 2007-02-20
No problem, glad to be of help. Seems you learned quite a bit in the process!

---

### Post by wortel on 2007-02-20
There is one problem - My swap partition isn't being used.
free returns:

```

             total       used       free     shared    buffers     cached
Mem:       1025860     532852     493008          0      11816     280448
-/+ buffers/cache:     240588     785272
Swap:            0          0          0

```

I'm guessing the problem lies with fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda6
UUID=351cb1f7-0fbf-4809-a09f-9cd9e80a2af9 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda5 /media/windata auto users,umask=000,atime,auto,rw,nodev,exec,nosuid 0 0
/dev/hda7 none   swap noauto 0 0

```

I'm 99% sure the mount point is incorrect, but man mount doesn't specify where it should be mounted.

---

### Post by m94mni on 2007-02-20
swap is mounted in a special way. This is my swap entry:

# Entry for /dev/sda6 :
UUID=304c7c1b-3a63-491b-a779-a09fa46d4ae8 none swap sw 0 0


Are you sure /dev/hda7 is the swap partition? You should see it in qparted.

Also, If the swap partition was moved/resized, you need to do 

sudo mkswap /dev/hda7

---

