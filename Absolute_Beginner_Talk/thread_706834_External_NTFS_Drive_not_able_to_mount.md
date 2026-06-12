---
title: "External NTFS Drive not able to mount"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by WebSiteGuru on 2008-02-24
I am not able to mount my external drive.

And sudo fdisk -l gives me this:

> Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb00fb00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14759   118551636   83  Linux
/dev/sda2           14760       14946     1502077+   5  Extended
/dev/sda5           14760       14946     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 20.4 GB, 20490979328 bytes
64 heads, 32 sectors/track, 19541 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00cfc6c0

Disk /dev/sdb doesn't contain a valid partition table


And yes I tried using the ntfs-config tool. And it still donesn't work. PLZ HELP!

---

### Post by Rocket2DMn on 2008-02-24
The line "Disk /dev/sdb doesn't contain a valid partition table" indicates that something is a little messed up with the drive.  If you can, you should plug the drive into a windows computer and run the chkdsk command on it.

---

### Post by Tprice on 2008-02-25
Thanks very much!

Should have thought about that but didnt! it word and now back on track!

---

### Post by WebSiteGuru on 2008-02-28
Well, Windows device manager see it, but I can not see the drive. How can I scan it? :confused:

---

### Post by Rocket2DMn on 2008-02-28
Normally you open a command prompt (start->run and type out "cmd" without quotes).  Then run "chksdk k:" where k is the drive letter.  Since none appears, you'll have to look up alternate   methods on how to do it.
You can also try using ntfsfix in ubuntu which requires the ntfsprogs package.
```
sudo ntfsfix /dev/sdb
```

---

### Post by superprash2003 on 2008-02-28
@websiteguru
 go to windows device mangar right click on the drive and clik on properties.. you should find an option called "populate" somewhere there.. in one of those tabs.. im not sure.. this may work!!

---

### Post by oedha on 2008-02-28
here's what i did
install gparted...from add/remove program
re-scan the disks
point to /dev/sdb1
create a partition....i chose fat32

this is the funny thing.........
after this......i can mount/unmount it manually but not automatically
then..i went to a windows machine...i rename that disk.....
back to ubuntu.....WALAH.......it's mounted automatically

question : can we just rename the disk from ubuntu ?

---

### Post by WebSiteGuru on 2008-02-29
Thanks everyone for the options. 

> **superprash2003 said:**
> @websiteguru
 go to windows device mangar right click on the drive and clik on properties.. you should find an option called "populate" somewhere there.. in one of those tabs.. im not sure.. this may work!!

Now that did NOT work from the windows machine. :(

@ Rocket2DMn - I'll try your option tonight (I hope) if I havd time to get to it tonight. ;)


@ oedha - I'll also try your too.

Hopefully it will work on one of the option.

---

### Post by WebSiteGuru on 2008-03-06
> **Rocket2DMn said:**
> Normally you open a command prompt (start->run and type out "cmd" without quotes).  Then run "chksdk k:" where k is the drive letter.  Since none appears, you'll have to look up alternate   methods on how to do it.
You can also try using ntfsfix in ubuntu which requires the ntfsprogs package.
```
sudo ntfsfix /dev/sdb
```

This is what I got when I ran your command.

> Mounting volume... Failed to startup volume : Invalid argument
FAILED
Attempting to correct errors... FAILED
Failed to startup volume : Invalid argument
Volume is corrupt. You should run chkdsk.


---

### Post by Rocket2DMn on 2008-03-06
Well, if you can't get it to show and fix under windows, it doesn't seem like you have much hope for it in linux either.  Sounds like your drive may just be broken.  If you don't have any important data on it, you can try wiping it clean with GParted to see if it can, or you can try to reformat it in windows if possible.  If neither of these work, then the drive would appear to be physically damaged and should be trashed.  If you ARE able to format it, then it means the drive is just corrupt or had physical defects that were recognized and worked around during the reformat.
Other than that, I don't think you have too many options.

---

### Post by WebSiteGuru on 2008-03-12
The drive is corrupted for sure. I am able to run propagate on my Vista Laptop. But since it is (I think) a FAT partition. Vista didn't like it. I do have data on there that I wants out. So, I will keep trying.

---

