---
title: "Can't see second hard drive"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by A. Noney Moose on 2007-03-26
Greetings All.

Have installed Feisty Fawn on an older PIII/450 with 327 mB using two smaller hard drives I had lying around.  This install is for a learning experience after playing with live cds for a while. Also, I chose 7.04 after experiencing many problems with Easy Ubuntu and multimedia packages being removed from the repositories.

Everything is working except that I cannot see drive hda1 with the file managers. Access to hdb1 is restricted "for security reasons".  These are very old, very small drives (hda is 4.3 and hdb is 3.8 gB) but both appear to be functioning.  Below is the output of mount, fdisk -l and my fstab:

moose2@moose3:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
tmpfs on /lib/modules/2.6.20-13-generic/volatile type tmpfs (rw,mode=0755)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

moose2@moose3:~$ sudo fdisk -l /dev/hda
Password:

Disk /dev/hda: 4325 MB, 4325529600 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         496     3984088+  83  Linux
/dev/hda2             497         525      232942+   5  Extended
/dev/hda5             497         525      232911   82  Linux swap / Solaris

moose2@moose3:~$ sudo fdisk -l /dev/hdb

Disk /dev/hdb: 3860 MB, 3860398080 bytes
255 heads, 63 sectors/track, 469 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         442     3550333+  83  Linux
/dev/hdb2             443         469      216877+   5  Extended
/dev/hdb5             443         469      216846   82  Linux swap / Solaris

FSTAB
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6186620e-7d56-4be7-b837-eec7d83a9c55 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=74a2ea88-0226-4bfe-8c1a-c39d8e57eda0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

My question is how to edit fstab (and mtab, I'm guessing) to reflect hda1. Given these drives are so small I need all the room I can get. As you can guess the mount command returns with an error that hda1 is not in fstab.

If it's of any consequence the Grub boot loader gives me the choice of about six different kernels to boot to (I only need the on AFAIK) so I believe that some clean up is in order but that's another subject, yes?

Thank you one and all for any help,

Brent

---

### Post by undertherift on 2007-03-27
I can answer both, i think.
To Mount:
Create a directory whereever (I suggest your home). Lets pretend that is /home/ubuntu/hdadrive

Append this to your /etc/fstab
```
/dev/hda1 /home/ubuntu/hdadrive ext3 defaults 0 0
```

I don't remember exactly what all those parameters mean, but that should solve your problem.  Its worth nothing that you have to have the appropriate filesystem type (ext2, ext3, resierfs, xfs) where it says ext3.  If you don't, it'll let you know. (bad fs type or something similar to that).

As far as grub, if you go into /boot/grub/menu.lst, you will see a bunch of blocks at the bottom corresponding to grub entries.
```
title Ubuntu blah blah
kernel blah blah blah
initrd blah blah 
boot
```

Don't Delete them, just comment them out (just in case you need the for any purpose.  Just add a # to the beginning of each line. 

This is a fairly concise explanation, if you have questions i'll elaborate. 

Regards,

---

### Post by A. Noney Moose on 2007-03-27
OK I tried that and using the mount command I get an error that the mount point doesn't exist.

As suggested I created the following
/home/moose2/harddrive/hda1

Then I added the following to my fstab,
/dev/hda1     /home/moose2/harddrive/hda1    ext3, defaults, 0       0

But there is nothing in that directory...should there be and if so what?

Thanks for the reply, I'll tackle the boot issue just as soon as I gain access to the hard drive.

Brent

---

### Post by undertherift on 2007-03-27
Try removing the commas in between ext3 and defaults and the 0 0.  It should look just like what i posted in the previous post.

---

### Post by A. Noney Moose on 2007-03-27
Nope.....still get thew mount point does not exist error

---

### Post by undertherift on 2007-03-27
ok show me the /etc/fstab, and the output of fdisk -l.  Oh and see if you use the code brackets, its easier on my eyes :) .  I'm just gonna double check for typos or anything like that.  Also, are you sudo mount -ing?  Permissions could be an issue?

---

### Post by A. Noney Moose on 2007-03-27
Here is the fstab,

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6186620e-7d56-4be7-b837-eec7d83a9c55 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=74a2ea88-0226-4bfe-8c1a-c39d8e57eda0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /home/moose2/hddrive/hda1 ext3 defaults 0       0
```

---

### Post by undertherift on 2007-03-27
Silly question, but can you verify that /home/moose2/hddrive/hda1  actually exists?  I've seen this error, but only when the folder location doesnt exist.

---

### Post by A. Noney Moose on 2007-03-27
Yes the folder exists but as I mentioned earlier there is nothing in that folder. Should there be and if so what?

Also I forgot to mention that yes I am using a  sudo  mount and I[ve tried both sudo mount /dev/hda and sudo mount hda

---

### Post by undertherift on 2007-03-27
I was just asking because this is the path in fstab
 /home/moose2/hddrive/hda1 

and this the one you said you created
/home/moose2/harddrive/hda1

Note the harddrive vs hddrive.

Are you having a problem initializing the swap?  (I'd imagine this would show up on startup).  I found this thread (its for fedora, but the principle should work just fine, if thats the problem).
[http://www.linuxquestions.org/questions/showthread.php?t=234054](http://www.linuxquestions.org/questions/showthread.php?t=234054)

---

### Post by undertherift on 2007-03-27
oh and, you should see the contents of that drive.  Whatevers on it would show up, as if it was in that folder.

---

### Post by A. Noney Moose on 2007-03-27
Thanks Vik for putting me on the right track.

Used your advice but created mount point as root in /media then edited fstab to create the permanent  automatic mounting of hda. 

I how have access to the drive with full permissions. Learned a little about chmod as well!

Thanks again

Brent

PS, also used your advice and edited the grub file to delete reference to those e other kernals which were located on hda and picked up by grub during the feisty install. Everything is smooth as silk now. thanks again.
B

---

### Post by A. Noney Moose on 2007-03-27
Thanks vik,

for putting me on the right track. I created, as root, a new mount point in /media and then edited fstab to give me the permanent auto mount at boot for hda. Learned a bit about chmod as well to gain full permissions to the drive. 

Also tacked the grub multi kernel issue by commenting out the offending lines. things are running smooth aa silk now. 

Thanks again
Brent

---

### Post by undertherift on 2007-03-28
Brent,

I'm glad it worked - i was out of ideas. :) 

Check out ubuntuguide.org  as well - that should give you a solution to 99% of the things you want to do. 

Enjoy your ubuntu, brotha.

Vik

---

