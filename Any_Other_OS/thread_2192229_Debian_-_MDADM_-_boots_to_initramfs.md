---
title: "Debian - MDADM - boots to initramfs"
date: 2013-12-06
forum: Any Other OS
---

### Post by collisionystm on 2013-12-06
Hey guys, once again I could use the help of the community.

I am at a customer location working on a Debian 6 server with 6 drives all assembled in an MDADM array.

A month ago the server lost a drive. I added a new disk with the help of [http://globalblindspot.blogspot.com/2011/06/how-to-replace-failed-disk-of-raid-5.html](http://globalblindspot.blogspot.com/2011/06/how-to-replace-failed-disk-of-raid-5.html)

The drive was in slot 0 on the server (dell R610).

So the drive rebuilt with no problems and the server has been humming along until last night when the power went out. As of this morning the server would boot with 'No boot devices found'. I have zeroed this in to be a software problem. If I remove the drive from slot 0, the system will then attempt to boot LILO but ends at initramfs
The message states that root cannot be mounted and[COLOR=#000000][FONT=Segoe UI]target file system doesnt have requested /sbin/init[/FONT][/COLOR]

from initramfs I can cat /proc/mdstat and see that MD1 is assembled and active with 5 drives. The problem is, if I type exit I am prompted with a kernel panic.

Previously mdstat showed MD0 as well as MD1. MD0 contains the root and is now missing. 

When I added the new disk a month ago, I used mdadm --manage /dev/md0 --add /dev/sde and then mdadm --manage /dev/md1 --add /dev/sde1

Both rebuilds finished without error.

Did I somehow break this? Is there any MDADM experts that can help me get this back online?

---

### Post by howefield on 2013-12-06
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by SaturnusDJ on 2013-12-07
Are you able to post examines for all partitions?
```
mdadm --examine /dev/sd*
```

---

### Post by collisionystm on 2013-12-07
I wasn't able to fix the problem. I currently just have a work around.

So pretty much what happened is I grew the mdadm but did not modify /etc/mdadm/mdam.conf with the updated information. Following that I should have ran update-initramfs.

The result of me NOT doing those steps was the system booting with an mdadm.conf in its initramfs that was NOT compatible with the current state of the raid array.

To try to fix the issue, I would boot to a live usb and install mdadm then assemble the array
```
# apt-get install mdadm
```

```
# mdadm --assemble --scan
```

```
# cat /proc/mdstat
Personalities : [raid1] [raid6] [raid5] [raid4]
md1 : active raid5 sdg5[0] sdc5[5](S) sdf5[4] sde5[3] sdd5[2] sdb5[1]
     1949615872 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]

md0 : active raid1 sdf1[0] sdb1[5](S) sdc1[4] sde1[3] sdd1[2] sdg1[1]
     979840 blocks [5/5] [UUUUU]
```
     
Okay. I can see both array's intact.

I then mounted the md0 (root) array on /mnt

```
# mount /dev/md0 /mnt
```

initramfs has its mdadm.conf as

```
ARRAY /dev/md0 level=raid1 num-devices=4 UUID=d0719570:5a1e00ab:e038674a:2925917c   spares=2
ARRAY /dev/md1 level=raid5 num-devices=5 UUID=9e726ab9:03da8a81:3695e7d7:46423ef6   spares=1
```

What it should have read was

```
ARRAY /dev/md0 level=raid1 num-devices=5 UUID=d0719570:5a1e00ab:e038674a:2925917c   spares=1
ARRAY /dev/md1 level=raid5 num-devices=5 UUID=9e726ab9:03da8a81:3695e7d7:46423ef6   spares=1
```

SO, I checked my /mnt/etc/LILO.conf and verified the image it was booting

```
lilo.conf
default=Linux

image=/vmlinuz
       label=Linux
       read-only
#       restricted
#       alias=1

       initrd=/initrd.img

image=/vmlinuz.old
       label=LinuxOLD
       read-only
       optional
#       restricted
#       alias=2

       initrd=/initrd.img.old
```

Ok, lets check the symlink for initrd.img

```
# cd /mnt
# ls -lh

lrwxrwxrwx  1 root root   30 Nov  4  2010 initrd.img -> boot/initrd.img-2.6.32-5-amd64
```

```
# mkdir /tmp/init
# cp /mnt/boot/initrd.img-2.6.32-5-amd64 /tmp/init/
```

Then I gunzipped the initrd, modified /etc/mdadm/mdadm.conf and put it back together.

I renamed my file in /mnt/boot with a .old extension and copied over my new initrd.img-2.6.32-5-amd64

After all this, the system STILL would boot with an initramfs that contained the WRONG mdadm.conf

Inside of initramfs I also modified the mdadm.conf, assembled the raid and CTRL+D to continue boot only to get an immediate kernel panic.

---

Here's how I got the system back online.

1. Installed a new OS to a USB drive
2. Set the server to boot from the USB drive
3. Installed ssh, xrdp, mdadm, lvm2, kvm and virt-manager
4. Reconnected virt-manager to the volume groups on the mounted raid array and launched my VM's.

The plan now is to assemble another server and use virt-manager's integrated migrate feature to transition the VM's to a permanent home that has not suffered a bad mdadm setup.

Anyways, thanks for the help.

---

### Post by SaturnusDJ on 2013-12-08
You should be able to fix this with chroot if this truly is the problem.
The how to in my sign contains the needed steps.

---

### Post by collisionystm on 2013-12-08
> **SaturnusDJ said:**
> You should be able to fix this with chroot if this truly is the problem.
The how to in my sign contains the needed steps.

chroot to run update-initramfs is one of the first things I tried. Unfortunately the command wasn't even available to run. I'm not 100% what the problem regarding that was.

---

### Post by SaturnusDJ on 2013-12-09
That's strange. Maybe try a older distro.

---

