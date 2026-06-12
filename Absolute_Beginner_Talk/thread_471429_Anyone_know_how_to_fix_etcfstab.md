---
title: "Anyone know how to fix /etc/fstab?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2007-06-12
As stated in [this post]("http://ubuntuforums.org/showthread.php?p=2826095#post2826095") I'm trying to install Dapper over Hoary on an IBM ThinkPad A20m. For some reason the Dapper Live CD hates the partitions that Hoary is just fine with, and I think it has something to do with the mtab and fstab files in /etc/. I *know* fstab isn't reading the way it's supposed to. Currently on Dapper it displays as this:

> unionfs / unionfs rw 0 0
tmpfs / tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0

The main partition is called hda1, not unionfs, and needs to read "errors=remount-ro", besides. But directly editing the files doesn't seem to work. Anyone know how to fix this? Until Dapper can access hda1, it won't let me install it.

---

### Post by Inxsible on 2007-06-12
Could you post your sudo fdisk -l ?

---

### Post by Najand on 2007-06-12
Post the whole [FONT="Courier New"]/etc/fstab[/FONT] file. 
Also post the output of your "[FONT="Courier New"]sudo fdisk -l[/FONT]" command.

---

### Post by Halfling Rogue on 2007-06-12
Sudo fdisk -l returns:

> Disk /dev/hda: 12.0 GB, 12068904960 bytes
255 heads, 63 sectors/track, 1467 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1421 11414151 83 Linux
/dev/hda2 1422 1467 369495 5 Extended
/dev/hda5 1422 1467 369463+ 82 Linux swap / Solaris

And /etc/fstab is exactly like how I quoted in the first post. Three lines, that's it.

---

### Post by Inxsible on 2007-06-12
backup your fstab 
```
sudo cp /etc/fstab /etc/fstab.bak
```
and then replace the contents of fstab with the following:
```
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
``` Save and restart.

---

### Post by Najand on 2007-06-12
Ok... Backup it. Then Copy and Paste the following and save it a new fstab file:
```
proc /proc  proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0

```

---

### Post by Najand on 2007-06-12
> **Inxsible said:**
> backup your fstab 
```
sudo cp /etc/fstab /etc/fstab.bak
```
and then replace the contents of fstab with the following:
```
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
``` Save and restart.

It won't work as it has no /proc

---

### Post by Halfling Rogue on 2007-06-12
Will I need to reboot after that? I'm using the Live CD (I'm trying to install Dapper but it won't let me since it can't find the necessary GB), and rebooting seems to wipe any changes I make.

---

### Post by Inxsible on 2007-06-12
> **Najand said:**
> It won't work as it has no /proc

You are right, i missed that line.

---

### Post by Najand on 2007-06-12
> **Halfling Rogue said:**
> Will I need to reboot after that? I'm using the Live CD (I'm trying to install Dapper but it won't let me since it can't find the necessary GB), and rebooting seems to wipe any changes I make.

That is why it doesn't work. Try to mount your /dev/hda1 manually:
```

sudo mkdir /media/hda1
sudo mount -t ext3 -o defaults,users /dev/hda1 /media/hda1

```

---

### Post by Halfling Rogue on 2007-06-12
No good, Filesystem still says there's only 13 MB, and unionfs is still mounted. You want the return for mount?

**ETA:** Fstab is still reading the same, too.

---

### Post by Halfling Rogue on 2007-06-12
Is there a way I can use Gnome Partition Editor to fix it?

---

### Post by Najand on 2007-06-12
Can you explain the situation there?  You have Hoary installed and you want to upgrade it to Dapper and you are trying to do it using the Live CD; So you tried to edit the /etc/fstab file, right?

---

### Post by Halfling Rogue on 2007-06-12
Yes. I installed Hoary, which works fine, with no problem, and no partition problem. When I run Hoary, it says there's 8.9 GB of free space. But I want to install Dapper. The Dapper Live CD will *run*, but it can't install, because it needs 2 GB of free space to do that, and it can only find 13 MB because it's partitioning hda1 away where it can't get at it for some reason. If that makes sense?

---

### Post by Najand on 2007-06-12
You want to refomat the partiton and istall it on it or you want to install dapper on the free space?

---

### Post by Halfling Rogue on 2007-06-12
I just want enough free space to install Dapper. Once it's installed, I figure it'll be easier to make the rest of the space accessible, if I have to.

---

### Post by Halfling Rogue on 2007-06-12
Bumping for solutions~ Is there a way I could maybe boot the Live CD that would acknowledge hda1?

---

### Post by Najand on 2007-06-12
When installing ubuntu, at the partitioning stage, there is a stage it asks for mountpoints. Did you select partition /dev/hda1 as "/" (root partition)?

---

### Post by Halfling Rogue on 2007-06-12
Not with Dapper; Dapper can't get past the (3rd) Keyboard Layout Select stage, since it's only got the 13 MB to work with. Hoary does it, but Hoary mounts it to / anyway, so.

---

### Post by Najand on 2007-06-12
I see, what was the error for the mount command?
```

sudo mkdir /media/hda1
sudo mount -t ext3 -o defaults,users /dev/hda1 /media/hda1

```

---

### Post by Bohlio on 2007-06-12
Sorry im not much help here but...
Is there any reason why you dont wanna go to Fiesty instead of Drapper??
and wouldn't it be easier to wipe your hoary partition (backing up your data you want of course) then install drapper (or fiesty) over it? then you wont have the problem finding free space. Just curious :-) Im relatively new to Ubuntu and don't really see the benefits in having an older version. :)

---

### Post by Halfling Rogue on 2007-06-12
> **Najand said:**
> I see, what was the error for the mount command?
```

sudo mkdir /media/hda1
sudo mount -t ext3 -o defaults,users /dev/hda1 /media/hda1

```


No errors when I put in the actual sudo mount command, but after I put it in, if I check mount again it returns this:

```
unionfs on / type unionfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/hda1 on /media/hda1 type ext3 (rw,noexec,nosuid,nodev)
```

Going into computer:/// shows that the 10.9 GB Volume **has** disappeared, but Filesystem apparently still isn't acknowledging the extra space, and GPE still shows three partitions.

What's really weird is GPE is clearly stating that hda2 and hda5 are (mounted?) partitions that I can't unmount, but as I just showed, running "mount" in the terminal doesn't return either of them in the listing, and hda2 doesn't show up in /dev.

---

### Post by Halfling Rogue on 2007-06-12
> **Bohlio said:**
> Sorry im not much help here but...
Is there any reason why you dont wanna go to Fiesty instead of Drapper??
and wouldn't it be easier to wipe your hoary partition (backing up your data you want of course) then install drapper (or fiesty) over it? then you wont have the problem finding free space. Just curious :-) Im relatively new to Ubuntu and don't really see the benefits in having an older version. :)

Don't have Feisty on me, actually, and don't currently have a good way of downloading it, since the laptop I'm using for internet doesn't have a CD burner, and I can't set up the problem laptop because I only have one wireless card. Plus I'm more used to Dapper, I've been using it for about half a year now.

I've thought of wiping Hoary's partitions, but when I'm in Hoary the extra partition (hda2) isn't even *there*, and when I'm in the Dapper Live CD it says I can't deactivate or affect the hda2 and hda5 partitions because they're being used. So. :?

---

### Post by Halfling Rogue on 2007-06-12
I reinstalled Hoary with only the most basic system (text based) to see if it made the Live CD cooperate; no luck. But running mount in Hoary returned this:

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
```

Is there anything I could do to the mountings in Hoary that might let the Dapper CD work?

**ETA:** When I got to the "start or install Ubuntu" menu for the Dapper CD, I checked F6 for options, and it reads:

```
Boot Options boot=casper initrd=/casper/initrd.gz ramdisk_size-1048576 root=/dev/ram rw quiet splash --
```

Should I change /dev/ram to something else or what?

---

### Post by Halfling Rogue on 2007-06-12
Also, according to GPE, hda2 is in /dev, but when I look in the /dev folder it's not there; only hda1, hda5, and hdc. I have no idea where GPE is pulling hda2 from.

---

### Post by Halfling Rogue on 2007-06-12
delete

---

### Post by Halfling Rogue on 2007-06-13
Bump for solution.

---

### Post by Halfling Rogue on 2007-06-13
Bump for solution.

---

### Post by Halfling Rogue on 2007-06-14
Bump for solution.

---

