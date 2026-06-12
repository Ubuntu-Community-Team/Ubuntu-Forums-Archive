---
title: "Missing memory, missing swap space"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Ralph Boland on 2006-11-24
I originally posted this in the installation forum but got no responses 
so I am hoping someone using this forum can help.

I recently moved from Fedora core 1 to ubuntu 6.06.
On boot up I got messages (not exact):

DosSegMgr: Warning:
using an alternate geometry (cylinders, heads, sectors) for drive hda

The kernal reported drive geometry is: C=4865 H=16 S=63

The partition records report a geometry of C=4865 H=255 S=63

Using the alternate geometry reported by the partition records

No volume groups found
alert does not exist

Dropping to a shell

/bin/sh: can't access tty. job control turned off

I didn't know what to do at this point so I just rebooted again
and got the same messages.

On my third (I think) try, ubuntu 6.06 came up successfully
and everything seemed ok as far as I can tell.

Among the things I did was run the command:

squeak -memory 150m squeakImage

which runs squeak (a version of Smalltalk) with an initial allocation
of 150 megabytes of memory.

This worked for a few day until I upgraded to unbutu 6.10.

Then, when I ran the above command ubuntu reported that not enough
memory was available. However the command:

squeak -memory 110m squeakImage

worked fine.

MY FIRST QUESTION IS:
What is it about ubuntu 6.10 that is using the
extra memory since (AT LEAST) 40 megabytes of memory is no longer
available to applications that I run?
Is there anything that I can (and should) do to free up this memory?

I then ran a df command.
I noticed that no swap space was reported by df.
(on Fedora core1 the df command reports the size
of my swap space which was set to 512m on my 256m machine.)

MY SECOND QUESTION IS:
What happened to my swap space?
I am assuming that I need to repartition so that I have a swap space.
If so, where do I go to find the documentation on how to do this?
I don't want to lose the data currently on the disk drive of course.

Thanks, and sorry for the long post.

Ralph Boland

---

### Post by christhemonkey on 2006-11-24
Could you give us the output of:
```
fdisk -l 
```

---

### Post by Ralph Boland on 2006-11-27
> **christhemonkey said:**
> Could you give us the output of:
```
fdisk -l 
```
This is the result of running fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4775    38355156   83  Linux
/dev/hda2            4776        4865      722925    5  Extended
/dev/hda5            4776        4865      722893+  82  Linux swap / Solaris

This seems to suggest that my swap space is there and is bigger than
the 512M it was set to when I was using Fedora Core 1.
My lack of memory remains unexplained though.
Bye the way, this is what df gives me.

 df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             37752556  12926928  22907872  37% /
varrun                  123660        88    123572   1% /var/run
varlock                 123660         4    123656   1% /var/lock
procbususb               10240       104     10136   2% /proc/bus/usb
udev                     10240       104     10136   2% /dev
devshm                  123660         0    123660   0% /dev/shm
lrm                     123660     18132    105528  15% /lib/modules/2.6.17-10-386/volatile

Note that no mention of the swap space is mentioned (which df on
Fedora 1 did)

Ralph

---

### Post by taurus on 2006-11-27
What about

```
free
```

---

### Post by Ralph Boland on 2006-11-29
> **taurus said:**
> What about

```
free
```

The result of running free was:

 free
             total       used       free     shared    buffers     cached
Mem:         247324     225180      22144      0         2844       96980
-/+ buffers/cache:     125356     121968
Swap:            0          0          0


I think this means that I lost my swap space when I upgraded from
Fedora I.

So how do I add a swap space to my partition without losing any of my
data?.  Is there documentation on how I should do this somewhere?

Also, is there a way too tell who is using all of this memory?
I am particularly concerned with the 40M I lost when I switched
from  ununtu 6.06 to  6.10.

Note that my memory is shared with my graphics card.
Is there a way to tell how much my graphics card is actually using?

Thanks again

Ralph

---

### Post by taurus on 2006-11-29
What does your /etc/fstab look like?

```
cat /etc/fstab
```

---

### Post by Ralph Boland on 2006-11-30
> **taurus said:**
> What does your /etc/fstab look like?

```
cat /etc/fstab
```


 cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=7b5dd719-a018-4d02-8b6a-417327d44607 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=f342f304-d287-494e-b179-b393b9c81378 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/flash1   vfat    noauto,user     0       0


Note: The only line changed from what was installed initially
is the last line.  This line is essentially the same as when
I was running Fedora Core I.
I don't know what you are looking for here.
I have very little on my system other than  6.10 itself.
I use: 
   Squeak: a version of Smalltalk
   Lyx:  (a latex based word processor) not part of 6.10 itself but 
         a fairly standard apt-get-able package.
   dnswrapper:  I tried to install for a wireless adapter but it failed
                to install.  I did an uninstall.

I tried installing Cincom's  non-commerical version of Visualworks 
Smalltalk) but it didn't install properly.

I see no reason why any of these packages would use any memory when
they are not running.  I have rebooted several times since these
installs so any orphan processes from the failed installs should be long gone.

Ralph

---

### Post by Crakie on 2006-11-30
UUID=f342f304-d287-494e-b179-b393b9c81378 for your swap-drive. Does this match /dev/hda5?

What's the output of swapon -s?

---

### Post by taurus on 2006-11-30
Do you connect and disconnect your flash drive, /dev/sda1, all the time while using Ubuntu?

Maybe you can try changing this line in /etc/fstab

```
UUID=f342f304-d287-494e-b179-b393b9c81378 none swap sw 0 0
```
to 

```
/dev/hda5   none   swap   sw   0   0
```
and reboot.  See if that mounts your swap partition or not!

---

### Post by Crakie on 2006-12-01
I had problems with swap not being mounted at boot as well. I followed the fix [here]("https://launchpad.net/distros/ubuntu/+bug/66637") and everything was ok :)

---

### Post by Ralph Boland on 2006-12-06
> **Crakie said:**
> I had problems with swap not being mounted at boot as well. I followed the fix [here]("https://launchpad.net/distros/ubuntu/+bug/66637") and everything was ok :)

I followed the instructions given there and now I have a swap space!

Thanks everybody.

I am still not sure how to determine who is using my main memory,
in particular the 40M+ of additional memory that 6.10 uses that
6.06 does not.

Ralph

---

