---
title: "Mount Hard Drive from Live CD"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by jonkanon on 2007-09-16
Hi everyone, I'd be so glad for help.

I want to access (and rescue) files on the Hard Drive of a (crashed) Windows Computer.

I start up with Ubuntu Feisty Live CD, the problem is I don't find the Hard Drive. When I click on Computer, only DVD-ROM and Filesystem is visible. I understand I need to mount the Hard Drive. So I've read some threads here and tried:

[I]sudo mkdir recovery
sudo mount /dev/hda1 /recovery
[/I]
I get the error message:
mount: hda1 already mounted or /recovery busy

I also tried some variations like
*sudo mount -t reiserfs /dev/hda1 /recovery*
(and)
*sudo mount t- ext3 -o defaults /dev/hda1 /recovery*
(and)
*sudo mount -t ntfs /dev/hda1 /recovery -o nls=utf8,umask=0222*
(all of which I found in threads, but the output is still)
mount: /dev/hda1 already mounted or /recovery busy


The Output of sudo fdisk -l is:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         509     4088511   12  Compaq diagnostics
/dev/hda2   *         510        3871    27005265    c  W95 FAT32 (LBA)
/dev/hda3            3872        7296    27511312+   c  W95 FAT32 (LBA)


It's probably very simple... please tell me what to do to find my files. Thanks.

---

### Post by zbot on 2007-09-16
what is the output of your /etc/fstab file ?

Cheers,
-Cisco (zbot)

---

### Post by jonkanon on 2007-09-16
Hi Cisco, thanks.

The output of /etc/fstab is
[I]
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0[/I]

I dont think I can change it since it is on the live CD?

By the way, the output of mount is:

[I]ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
ubuntu@ubuntu:~$ 
[/I]

---

### Post by kfrance on 2007-09-16
So it might be the disk formats that are messing you up. You have been trying to mount a drive that is formatted with Compaq diagnostics (which I don't know what that is exactly but it is probably some compaq utilities). Your data is probably on hda2 given its size.  Try 
>  mount -t fat32 /dev/hda2 /recovery

---

### Post by jonkanon on 2007-09-16
I tried sudo mount -t fat32 /dev/hda2 /recovery

I got:

[I]mount: unknown filesystem type 'fat32'
maybe you meant 'vfat'[/I]

So I tried that to, and got the same old unclear message:

*mount: /dev/hda2 already mounted or /recovery busy*

More suggestions? thanks

---

### Post by kfrance on 2007-09-16
Yeah, sorry. I forgot that fat32 was mounted as vfat. It is weird that you try and mount the /dev/hda2 and you get an error about /dev/hda1.  Are you sure you have everything correct there?  Also try mounting hda3 if that doesn't work.

---

### Post by jonkanon on 2007-09-16
sorry, my mistake! sorry. the error message concerned hda2. I will edit.

and I get the same error message for hda3:

*mount: /dev/hda3 already mounted or /recovery busy*

---

### Post by jonkanon on 2007-09-16
Maybe this has something to do with it... I now noticed an error message on startup from the Live CD:

[I]Loading hardware driver...
Unable to load drivers - hardware revision not supported....[/I]

Or something similar. Sonds like a problem, huh? But I don't know, the restricted drivers manager seems to work fine when Ubuntu has started.

Does someone have any suggestions in mounting the Hard Drive please....

---

### Post by kfrance on 2007-09-16
I imagine that it is an old hard drive. What kind of hard drive is it? If you can see the hard drive through fdisk than it seems unlikely that you don't have the correct driver for it. That missing driver might be for something else.

---

### Post by kfrance on 2007-09-16
What does cat /etc/mtab give you?

---

### Post by jonkanon on 2007-09-16
Here is the output:

[I]ubuntu@ubuntu:~$ sudo cat /etc/mtab
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.20-15-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.20-15-generic/volatile tmpfs rw,mode=0755 0 0
/dev/bus/usb /proc/bus/usb none rw,bind 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
ubuntu@ubuntu:~$ 
[/I]

Sorry to say I dont know what kind of hard drive it is but it shouldnt be old, it is an Acer computer only 1 year old.

Thanks for your time. Suggestions?

---

### Post by jonkanon on 2007-09-17
Help, someone?

---

### Post by jonkanon on 2007-09-17
When I open Gnome Partition Editor, it says that hda1, hda2 and hda3 are mounted at mountpoint /realcdrom. 

But I cant find any files there.
What could this mean?

---

### Post by jonkanon on 2007-09-17
OK, now I tried a Kubuntu Live CD instead of Ubuntu Feisty Live CD.

--> No problem mounting there! So now I've saved my files.

EDIT: I managed accessng my Hard Drive the first time with Kubuntu Live CD, but when I tried one more time, just for curiousity, I got the same error message as before: hda2 already mounted or /recovery busy.

Odd.

Well, anyway, I solved my problem but I'm sure there's still a problem with Ubuntu, maybe even Kubuntu.

---

