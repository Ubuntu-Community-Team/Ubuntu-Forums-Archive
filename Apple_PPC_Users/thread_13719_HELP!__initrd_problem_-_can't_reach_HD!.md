---
title: "HELP!  initrd problem - can't reach HD!"
date: 2005-02-02
forum: Apple PPC Users
---

### Post by ronklob on 2005-02-02
Hi all, 

I've just begun what I hope will be a long journey into Linux with Ubuntu.  The beginning path has been a bit bumpy though. 

OK, I've got a blue & white G3/350 setup (for now) with a single 15GB drive, with Warty (2.6.8.1-3) on it.  Using Random Juju's tip [here](http://ubuntuforums.org/showpost.php?p=42546&postcount=14), I was able to get Ubuntu up and running, then used Synaptic to perform most of the upgrades, and did some custom installs.  

So I had it all set up the way I wanted, then shut it down to move into the next room.  On startup, I'm back to 

[B]pivot_root no such file or directory
/sbin/init/: 429: cannot open dev/console: no such file
Kernel Panic: Attempted to kill init![/B]

Apparently, there was a bit more to Juju's explanation that I missed.  A VERY [IMPORTANT bit.](http://www.ubuntuforums.org/showthread.php?t=8050&page=2&pp=10&highlight=429+initrd)   The bit about needing to patch initrd-tools to make sure that this doesn't happen again when a new kernel is used.  Which is what happened when I did my updates. 

So, now I've dl'd the Hoary Live image, and have been able to boot from that, but I can't find the partition that has my data, so I can change the initrd-tools and end this.  

**'mount'** gives me:

[B]/dev/mapper/casper-snapshot on / type auto (rw,noatime)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
tmpfs on /var/run type tmpfs (rw,nosuid,nodev)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,node=0755)[/B]

trying **'mount /dev/hda1 (or any #)'** just gives **'mount: you must specify the filesystem type'**

I also tried **'cat /etc/fstab'** which gave me:

[B]/dev/mapper/casper-snapsot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
tmpfs /var/run tmpfs nosuid,nodev 0 0
/dev/hdc4 swap swap defaults 0 0[/B]

So it looks like it can see the swap partition, as hdc4, but when I try to mount any hdcx, I get **'mount: can't find hdcx in /etc/fstab or /etc/mtab'**, including hdc4.

So, how should I go about this to get my partitions mounted and find the initrd-tools file, and edit it and restart?  

(Please remember I'm a noob, and most of the commands I've used are basic, or I don't REALLY understand what they are doing, so I'll need step-by-step -- THX)

---

### Post by ronklob on 2005-02-03
OK, now I'm REALLY confused.  I finally figured out how to mount the HD, and edit the mkinitrd file as Random Juju said (see link above), and the file is already set up 'correctly'.  

So why won't it boot?  

Any ideas?

TIA

---

### Post by ronklob on 2005-02-04
OK, does anyone have a solution?  

I can access the /, but I don't know what I need to check to figure out what is going wrong.  Can anyone help me out?

Oh, and also, why does Random Juju mention editing mkinitrd, and the bug fix is for initrd-tools, which I don't seem to have in my kernel.


TIA

---

### Post by betterok5 on 2005-02-04
>trying 'mount /dev/hda1 (or any #)' just gives 'mount: you must specify the filesystem type'<

Try 'mount -t [filetype(most likely ext2)] /dev/hda /mnt/ext2'.
So it should read 'mount -t ext2 /dev/hda(n) /mnt/ext2.
That assumes there is a directory 'ext2' in /mnt, if not precede it with 'mkdir /mnt/ext2'.
/mnt is kind of a temporary mount point if I understand correctly.

---

### Post by ronklob on 2005-02-04
Thanks betteroke, 

I've been able to mount the HD and root partition from the Live CD.  I just don't know what to look for to figure out why I can't boot normally, or what to do to fix it.  Juju mentioned that the mkinitrd might be messed up, but mine looks fine.  From there, I don't know where to look next.  etc/fstab?  initrd.img?  I'm completely clueless.

---

### Post by betterok5 on 2005-02-04
Yeah, after re-reading the thread I saw that my post was superfluous.  I will keep watching it though because I have not yet been able to boot from the live cd.  This is on a beige g3.
later
kk

---

### Post by adamw on 2005-02-04
Just out of curiosity, what does your /etc/yaboot.conf file look like?  Are you sure you set up yaboot properly? (making some assumptions here, I know).  FWIW, here's what my yaboot.conf file looks like:

boot=/dev/hda13
device=/pci@f4000000/ata-6@d/disk@0:
partition=10
root=/dev/hda10
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda9

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"


the initrd.img is actually a link which points to the real initrd.img as such:

initrd.img -> initrd.img-2.6.8.1-3-powerpc

as well as the vmlinux file:
vmlinux -> vmlinux-2.6.8.1-3-powerpc

although it doesn't matter if the REAL file or the link is called vmlinux - that's just a way of helping you see what version of the kernel and initrd you're using.

---

### Post by ronklob on 2005-02-05
Thanks adamw, 

Mine looks much like yours, to a point.  

boot=/dev/hd**c2**
device=/pci@**8**000000/**pci-bridge@d/**ata-1@**0**/disk@0:
partition=**3**
root=/dev/hd**c3**
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot


image=/boot/vmlinux
label=Linux
read-only
initrd=/boot/initrd.img
append="quiet splash"

[B]image=/boot/mvlinux.old
label=old
read-only
initrd=/boot/initrd.img.old
append="quiet splash"[/B]

What's up with the .old files? 


Thanks

---

### Post by ronklob on 2005-02-06
OK, I was 'toying' around with things a bit, and I noticed that I was in the wrong folder, looking at the wrong mkinitrd file, so my actual file WAS wrong, and I corrected it.  But it still won't boot.  Does anyone know what I should be trying next?

Thanks

---

### Post by ronklob on 2005-02-08
Bumping to see if anyone is still watching.  I've run out of ideas.  Anyone?

If there are no more ideas on what to check to fix my problem, how do I rescue or reinstall without wiping out all the custom installs and setup that took me a week to figure out and finish?  

Thanks

---

### Post by FLeiXiuS on 2005-02-08
When asked to reboot, push ctrl option F2 then press enter to enable the terminal.  Enter in the following commands.

```

chroot /target
mkdir /mnt/initrd
mount -o loop /boot/initrd.img-2.6.8.1-3-powerpc /mnt/initrd
cp -a /mnt/initrd /tmp
cd /tmp/initrd
mkdir devfs mnt proc scripts sys tmp var

```
```

nano loadmodules

#  Enter in the following, in this complete order!
	modprobe -k  unix 2 > /dev/null
	modprobe -k  sd_mod
	modprobe -k  pdc202xx_new > /dev/null 2>&1
	modprobe -k  aec62xx > /dev/null 2>&1
	modprobe -k  cmd64x > /dev/null 2>&1
	modprobe -k  generic > /dev/null 2>&1
	modprobe -k  hpt34x > /dev/null 2>&1
	modprobe -k  hpt366 > /dev/null 2>&1
	modprobe -k  ns87415 > /dev/null 2>&1
	modprobe -k  pdc202xx_old > /dev/null 2>&1
	modprobe -k  sc1200 > /dev/null 2>&1
	modprobe -k  siimage > /dev/null 2>&1
	modprobe -k  sl82c105 > /dev/null 2>&1
	modprobe -k  trm290 > /dev/null 2>&1
	modprobe -k  via82cxxx > /dev/null 2>&1
	modprobe -k  ide-disk

```
```

cd /tmp
mkcramfs initrd initrd.img-2.6.8.1-3-powerpc
mv /tmp/initrd.img-2.6.8.1-3-powerpc /boot/initrd.img-2.6.8.1-3-powerpc
rm -rf /tmp/initrd

```

Now press control option f1 to return you back to the reboot option.

---

