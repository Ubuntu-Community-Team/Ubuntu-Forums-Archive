---
title: "[SOLVED] does not recognise linux-swap"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by shabs on 2008-03-20
Hi
I partioned my hard drive to create 10.69 gb for ubuntu gutsy including 509.84 mb for swap. Both of these are listed under the extended partition. I used a program called visparted, also called parted magic, a linux live CD partitioning tool. I've tried turning the linux-swap partition 'on' but in the system monitor, system->administration->system monitor, it still shows the swap as being 0. I've attached the following files: 

The output of sudo fdisk -l as file *ouput.txt*.
The output of ls -l /dev/disk/by-uuid/ as file *output1.txt*.
The output of cat /etc/fstab/ as file *output2.txt*.

I've also attached a word document of the information I see in the Parted Magic program as the file *PartedMagic.doc*

I have an 80Gb HDD.
Vista Home Basic Ubuntu Gutsy dual boot (Vista installed first)

If somebody can help please do, I've been as detailed as I could but let me know if any helpful information is missing.

Thanks a bunch.

EDIT1: When I try 'sudo swapon -a' I get this message:
swapon: cannot canonicalize /dev/disk/by/-uuid/85cc09ba-9e5c-4744-8600-934b1d46bbdf: No such file or directory
swapon: cannot stat /dev/disk/by/-uuid/85cc09ba-9e5c-4744-8600-934b1d46bbdf: No such file or directory

Also while I was looking around I changed the uuid of the swap to the one mentioned right above in the /etc/fstab

---

### Post by Irony on 2008-03-20
Try;

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c5973aa3-3c1f-4dfe-8587-9e1eca29c106 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
#UUID=85cc09ba-9e5c-4744-8600-934b1d46bbdf none            swap    sw              0       0
/dev/sda6	none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Then in terminal do;

```
swapon -a
```

If it works it should show in system monitor resources as used swap something of 509.84 Mb (currently it should show zero if swap isn't working). If swap on doesn't work try a re-boot.

---

### Post by shabs on 2008-03-20
Thanks for the reply Irony,
So I should edit the /etc/fstab to make it look like what you've mentioned?

---

### Post by shabs on 2008-03-20
Irony I tried that, I edited the file to add this new line 
/dev/sda6	none            swap    sw              0       0
and tried swapon -a as root
then rebooted but it still says that the swap is 0.
i tried swapon -a again but I'm getting the same error as documented in the original post.
what do u think?

---

### Post by Irony on 2008-03-20
Probably because you partitioned using whatever you used and so get;

```
Partition 1 does not end on cylinder boundary
Partition 2 does not end on cylinder boundary
```

See here;

[http://www.unixguide.net/linux/faq/09.16.shtml](http://www.unixguide.net/linux/faq/09.16.shtml)

I would copy my install to an external drive;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

And then just use gparted and fdisk to set up the partitions (ubuntu live CD) - then copy back the install.

---

### Post by louieb on 2008-03-20
The original configuration should work. Are you sure swap isn't being allocated? It may be that none is being used and that is what you are seeing.  

If all you did was add the line to /etc/fstab that* iron*y suggested then you have swap allocated twice - once by uuid and once by device. May have it confused now.

Restore the original /etc/fstab,  reboot and to check use the command
```
free -t 
```

If you think there is still a problem post the output of the free command here .

---

### Post by shabs on 2008-03-20
well irony if nothing helps I might have to try what you suggest.

Louieb:
I restored it to what it was before and rebooted. here is the output of ```
free -t
``` as an attachment. 
And I changed the UUID [http://louboldt.com/ilinuxmisc.htm#uuid](http://louboldt.com/ilinuxmisc.htm#uuid)

Thanks

---

### Post by Irony on 2008-03-20
> **louieb said:**
> If all you did was add the line to /etc/fstab that* iron*y suggested then you have swap allocated twice - once by uuid and once by device. May have it confused now.

No, I hashed the original - as I said its probably the cylinder boundary thing - a bit of googling should find a solution..

---

### Post by louieb on 2008-03-20
No swap and when you used Irony's fix it still did not work. I'm stumped. One or the other should have worked. 
1st try this in a terminal
```
sudo swapon /dev/sda6
```And if that works try Irony's fix again. Just make sure that 
this line is removed 

```
UUID=85cc09ba-9e5c-4744-8600-934b1d46bbdf none  swap sw 0 0
```and in its place  put 
```
/dev/sda6 none  swap sw 0 0
```Hope it works. Because about the only thing left is what Irony suggested and coping off the install, formating  and coping back. or maybe just a reinstall but don't see how that would help.

---

### Post by shabs on 2008-03-20
OMG! it worked!!
I first tried ```
sudo swapon -a
``` and then changed the file /etc/fstab exactly like irony said to do in the earlier post and it worked. Now under system resources I see 509.8 MB swap!
Thankyou so much guys. I appreciate it!
Just that I dont remember what I did different than when I was trying earlier :(
oh well :)

---

