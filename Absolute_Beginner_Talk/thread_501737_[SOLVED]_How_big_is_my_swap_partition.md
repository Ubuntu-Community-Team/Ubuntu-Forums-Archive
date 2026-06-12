---
title: "[SOLVED] How big is my swap partition?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by chris1974 on 2007-07-15
How do I find out how big my swap partition is?  The df command doesn't seem to indicate this, or maybe I don't know how to read it.

Chris

---

### Post by Jimmyfj on 2007-07-15
> **chris1974 said:**
> How do I find out how big my swap partition is?  The df command doesn't seem to indicate this, or maybe I don't know how to read it.

Chris

Try df --help to get a list of options

df -a -h 

With the -h parm. to make it readable to humans

---

### Post by Lolicon on 2007-07-15
You could look at your partiton table and look at the swap disk.

---

### Post by meierfra on 2007-07-15
sudo fdisk -l

---

### Post by viciouslime on 2007-07-15
Or for a nicer, gui option: install gparted.

---

### Post by jokoagung on 2007-07-15
try
**sudo free**

---

### Post by oilchangeguy on 2007-07-15
also try, system, admin, disks, partitions.

---

### Post by chris1974 on 2007-07-17
OK, according to gparted, I have a 1.4GiB swap partition.  But when I run free -m and top, it says I have zero swap space.

Newbie confused.

Chris

---

### Post by aktiwers on 2007-07-17
Type 
```
 gnome-system-monitor
``` 
in terminal and look under the Resources tap.

Or go to System => Administration => System Monitor
And look under Resources.

It should be there.

---

### Post by DBStevens on 2007-07-17
How about typing free -m in a terminal and pasting the output here.

---

### Post by chris1974 on 2007-07-17
> **DBStevens said:**
> How about typing free -m in a terminal and pasting the output here.

Here is the output of free -m.

                         total       used       free     shared    buffers     cached
Mem:                495        453          42                0               7           170
-/+ buffers/cache:        275        220
Swap:                   0             0             0

---

### Post by DBStevens on 2007-07-17
Yup there is zero bytes of swap currently setup on your system.

Could you zip up and attach dmesg.

It could be not mounted or turned off.

---

### Post by chris1974 on 2007-07-17
> **DBStevens said:**
> Yup there is zero bytes of swap currently setup on your system.

Could you zip up and attach dmesg.

It could be not mounted or turned off.

dmesg.txt.zip attached

---

### Post by DBStevens on 2007-07-17
Darn,

The dmesg buffer ran out before the boot finished, try cat /var/log/messages | grep "Adding"   

and 

cat /etc/mtab

and
 
cat /etc/fstab

---

### Post by chris1974 on 2007-07-18
> **DBStevens said:**
> Darn,

The dmesg buffer ran out before the boot finished, try cat /var/log/messages | grep "Adding"   

and 

cat /etc/mtab

and
 
cat /etc/fstab

I am not sure I did the first one right.

---

### Post by DBStevens on 2007-07-18
Ok, you have a swap partition defined as  /dev/sda5 according to the fstab entries

However swaping is not turned on since there was no output from:

cat /var/log/messages | grep "Adding"

I'd take a look through /var/log/messages looking for a message about not being able to add the swap partion or to turn on swapping.   That one is apt to be large so I won't ask you to zip and attach it. 

Something isn't right somewhere.

---

### Post by chris1974 on 2007-07-18
> **DBStevens said:**
> Ok, you have a swap partition defined as  /dev/sda5 according to the fstab entries

However swaping is not turned on since there was no output from:

cat /var/log/messages | grep "Adding"

I'd take a look through /var/log/messages looking for a message about not being able to add the swap partion or to turn on swapping.   That one is apt to be large so I won't ask you to zip and attach it. 

Something isn't right somewhere.

Actually, my /var/log/messages is quite small:

Jul 17 20:06:41 chris-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul 17 20:36:25 chris-desktop -- MARK --
Jul 17 20:56:26 chris-desktop -- MARK --
Jul 17 21:16:26 chris-desktop -- MARK --
Jul 17 21:36:26 chris-desktop -- MARK --
Jul 17 21:56:26 chris-desktop -- MARK --
Jul 17 22:16:26 chris-desktop -- MARK --
Jul 17 22:36:27 chris-desktop -- MARK --
Jul 17 22:56:27 chris-desktop -- MARK --
Jul 17 23:16:27 chris-desktop -- MARK --
Jul 17 23:36:27 chris-desktop -- MARK --
Jul 17 23:56:28 chris-desktop -- MARK --
Jul 18 00:16:28 chris-desktop -- MARK --
Jul 18 00:36:28 chris-desktop -- MARK --
Jul 18 00:56:28 chris-desktop -- MARK --

---

### Post by DBStevens on 2007-07-18
Chris,

It looks like you just picked a bad time to look at messages, the logs get rotated, and yours got restarted about 8.06 PM local time.

If you display the directory using your the file manager you should see a number of file that start off messages   that have .0 , .1.gz, .2.gz etc as suffixes,  pick one of the prior ones that actually has some size to it.

---

### Post by chris1974 on 2007-07-18
> **DBStevens said:**
> Chris,

It looks like you just picked a bad time to look at messages, the logs get rotated, and yours got restarted about 8.06 PM local time.

If you display the directory using your the file manager you should see a number of file that start off messages   that have .0 , .1.gz, .2.gz etc as suffixes,  pick one of the prior ones that actually has some size to it.

I looked at all of them.  None of them contain "Adding".

Chris

---

### Post by DBStevens on 2007-07-20
Chris,

Yep no swap space being added it may have been turned off but we are going to try turning it on.
Need the messages that get generated.


Try the following:

sudo swapon /dev/sda5 

followed by a 

swapon -s

---

### Post by chris1974 on 2007-07-20
> **DBStevens said:**
> Chris,

Yep no swap space being added it may have been turned off but we are going to try turning it on.
Need the messages that get generated.


Try the following:

sudo swapon /dev/sda5 

followed by a 

swapon -s

/dev/sda5                               partition       1481720 0       -1


Yea! It worked.

DBStevens is the king!

My free -m now shows

Mem:           495        487          8          0          4        243
-/+ buffers/cache:        239        255
Swap:         1446          0       1446

Out of curiosity, how would that have been turned off?  I am quite sure that I did not run a swapoff command!

Thanks so Much!!  Ubuntu forums rule!

Chris

---

### Post by DBStevens on 2007-07-20
Chris,

I'm not the king,

That title I reserve for Linus, Andrew, Alan, and many, many  others who brought us the core of this  operating system.

I have no idea what turned it off, we still don't know if it will be on after a reboot.   If it isn't on after the reboot we have to do some more poking around.

---

### Post by chris1974 on 2007-07-21
> **DBStevens said:**
> Chris,


I have no idea what turned it off, we still don't know if it will be on after a reboot.   If it isn't on after the reboot we have to do some more poking around.

You're right, it turned back off after reboot.  I already marked this thread resolved, and the issue doesn't really match the thread title. Should I start a new thread?

Chris

---

### Post by DBStevens on 2007-07-21
I need to know what your system init process actually runs.

Something got moved or turned off in that chain.

From  /etc

sudo grep -r "swapon" *

---

### Post by chris1974 on 2007-07-21
> **DBStevens said:**
> I need to know what your system init process actually runs.

Something got moved or turned off in that chain.

From  /etc

sudo grep -r "swapon" *

output

init.d/checkroot.sh:                    swapon -a -e >/dev/null 2>&1
init.d/checkroot.sh:                    swapon -a -v
init.d/mountall.sh:     # Execute swapon command again, in case we want to swap to
init.d/mountall.sh:             swapon -a -e 2>/dev/null || :  # Stifle "Device or resource busy"
init.d/mountall.sh:             swapon -a -e -v || :
rcS.d/S20checkroot.sh:                  swapon -a -e >/dev/null 2>&1
rcS.d/S20checkroot.sh:                  swapon -a -v
rcS.d/S35mountall.sh:   # Execute swapon command again, in case we want to swap to
rcS.d/S35mountall.sh:           swapon -a -e 2>/dev/null || :  # Stifle "Device or resource busy"
rcS.d/S35mountall.sh:           swapon -a -e -v || :
readahead/boot:/sbin/swapon

---

### Post by DBStevens on 2007-07-21
Ok, everything is there that I have on my working system.

I think that narrows it down to:

# Entry for /dev/sda5 :
UUID=64c45200-2bd9-4c48-8738-e1894154b96e none swap sw 0 0

in /etc/fstab

could you change that line to read 

/dev/sda5 none swap sw 0 0

Then reboot.

---

### Post by chris1974 on 2007-07-22
> **DBStevens said:**
> Ok, everything is there that I have on my working system.

I think that narrows it down to:
# Entry for /dev/sda5 :
UUID=64c45200-2bd9-4c48-8738-e1894154b96e none swap sw 0 0
in /etc/fstab
could you change that line to read 
/dev/sda5 none swap sw 0 0
Then reboot.

Seems to work after reboot!

free -m now shows
  
Mem:           495        486          9          0         23        190
-/+ buffers/cache:        272        222
Swap:         1446         33       1413


Thanks! again!

Chris

---

### Post by DBStevens on 2007-07-22
Number one on my short list of what got in the way:

#  -- This file has been automaticly generated by ntfs-config -- 

Which is what is different between your fstab and mine and mine doesn't use the uuid form for swap why the uuid form doesn't work I haven't a clue.

---

### Post by louieb on 2007-07-22
Feisty has changed the uuid on my laptop a couple of times. Don't know why. Just know it happens. At startup the next time can't find the swap partition  so it says no problem I just won't use swap and goes on and boots up.   To find a partitions uuid use. 

```
ls -l /dev/disk/by-uuid/
```

Well i think I just found out why.
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/90526](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/90526)

---

### Post by DBStevens on 2007-07-22
Ubuntu isn't the only one with issues in this area.   Dave Jones of RH was wondering what changed in this area on 07/20/2007 in a post entitled in part film at 11: kernel update .... on LKML, it turned out that RH was rolling its own udev rules and they were shall we say not in conformace with things as they were supposed to be.

Couple that with all of the configuration routines that play with things and it is a certainty that some folks are going to get into some funny situations. 

The same basic thing happens with my tuner cards and heaven help me if I allow my bios to see usb hard drives during boot.

---

