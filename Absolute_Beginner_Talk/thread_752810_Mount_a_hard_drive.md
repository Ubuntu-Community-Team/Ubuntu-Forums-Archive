---
title: "Mount a hard drive"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Mustey on 2008-04-12
Sorry guys, I know this is absolute newbie talk. I did search it but the 3 first pages didn't give me anything I can use.

I have recently moved from XP to Ubuntu. My machine has one fast hard drive on which I install games, OS and work stuff and a slower, bigger one on which I store files. Both are inside the machine, SATA (maybe SATA2? I can't tell) drives.

When installing Ubuntu I somehow managed to free 200GB (deleted some of the pr0n) from both drives so that my first drive could be backed up on the second and I could install Ubuntu on the first, faster drive. Now I need my second drive, I miss my music files and homework. The second drive was formatted in NTFS.

How do I bring it back - while keeping the information in it?

Thanks.

---

### Post by joshrobinson on 2008-04-12
could you post the output of the following command

```
fdisk -l
```

---

### Post by thisiam on 2008-04-12
[QUOTE=managed to free 200GB (deleted some of the pr0n)[/QUOTE]

wow, i'm sure 200GB is about normal with a lot of people but i just can't save it for someone to find
streaming pr0n works great or worked i should say, i have a g/f now.

---

### Post by Mustey on 2008-04-12
Joking about the pr0n... I don't know what I deleted that's worth 200GB. It was a frenzy, my amigo was around - to help me install Linux - and I was in a rush to delete stuff so to not waste his time.

I think around 100 GB were my serials: Top Gear, Simpsons, Futurama, Brainiac.
Another 40GB would be my MS software (I wouldn't be using it, of course)

Anyway, should I really type fdisk -l? it doesn't sound like something healthy.

I know there are people around who would make us noobs screw up our computers just for fun.

May someone please confirm that fdisk -l is a safe command?

---

### Post by joshrobinson on 2008-04-12
ive been a user here for 2 years now, if i was trying to screw up peoples computers, i would have been banned by now

```
sudo fdisk -l
```
sorry i forgot to add the sudo on it when i posted it earlier, this will LIST all of your disk's filesystems, its safe to run, just to prove it, heres the output of when i run it

```
joshua@laptop:~$ sudo fdisk -l
[sudo] password for joshua: 

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004a960

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8523    68460966   83  Linux
/dev/hda2           11811       12161     2819407+   5  Extended
/dev/hda3            8524       11810    26402827+  83  Linux
/dev/hda5           11811       12161     2819376   82  Linux swap / Solaris


```

---

### Post by Mustey on 2008-04-12
Didn't intend to insult you. You know, it's a penguin eat penguin world out there, gotta keep my beak sharp :)

Besides, what would you expect an M$ user like me to think fdisk does (in XP, it would format your disk)?

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19c8c0d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2678     1975995   82  Linux swap / Solaris
/dev/sda3            2679       19457   134777317+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb838ed79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       30400   141789690    f  W95 Ext'd (LBA)
/dev/sdb5           12749       25496   102398278+   7  HPFS/NTFS
/dev/sdb6           25497       30400    39391348+   7  HPFS/NTFS

Wad'ya think?

---

### Post by SnakeHips on 2008-04-12
Please post the oputput oif the following command.

```
mount
```

edit:
here's a useful guide (scroll down for NTFS)
[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Mustey on 2008-04-12
/dev/sda1 on / type reiserfs (rw,notail)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by SnakeHips on 2008-04-12
OK ,looks like we need to *mount* your second drive /dev/sdb

The link i posted earlier details how to mount NTFS partitions ,to begin with tho you may need to installl some tools

```
sudo aptitude install ntfsprogs
```

---

### Post by joshrobinson on 2008-04-12
woah, thats alot of partitions, do you know what ones you want to mount? or would you like to mount all of the NTFS partitions on the 250gig drive?

---

### Post by Mustey on 2008-04-16
I don't see anything really :)
I am kinda smart but too much to do and can't start learning Linux now!

I recall having 3 partitions on the storage drive (the 250GB one). All NTFS from win XP SP2 32bit (my CPU is 64). I would like to have them all.

I think if you tell me how to mount one, I would be able to do the rest myself.

I installed the ntfs progs package. What next?

---

### Post by joshrobinson on 2008-04-16
make sure you have ntfs-3g installed

```
sudo apt-get install ntfs-3g
```

now backup your fstab file
```
sudo cp /etc/fstab /etc/fstab.backup
```

now edit your fstab file
```
sudo gedit /etc/fstab
```

add these lines at the bottom

```

/dev/sdb1   /media/ntfs1   ntfs-3g rw,defaults,umask=0000 0 0
/dev/sdb5   /media/ntfs2   ntfs-3g rw,defaults,umask=0000 0 0
/dev/sdb6   /media/nfts3   ntfs-3g rw,defaults,umask=0000 0 0

```

save and close it

now we have to make the folders to mount the drives to
```
sudo mkdir /media/ntfs1
```
```
sudo mkdir /media/ntfs2
```
```
sudo mkdir /media/ntfs3
```

run this command
```
 sudo mount -a
```
they should mount, if theres a problem, output the error

---

### Post by Fzang on 2008-04-16
Pr0n can be viewed online if you're low on disc space:KS

---

### Post by skigemit on 2008-04-16
hey josh, for those three lines of code starting with /dev/sdb*  what parts of that line are specific to that system, for example, i have   /dev/hdb1, so would the line be:

/dev/hdb1   /media/ntfs1   ntfs-3g rw,defaults,umask=0000 0 0

or is there some other thing i need to change?

---

### Post by joshrobinson on 2008-04-16
> **skigemit said:**
> hey josh, for those three lines of code starting with /dev/sdb*  what parts of that line are specific to that system, for example, i have   /dev/hdb1, so would the line be:

/dev/hdb1   /media/ntfs1   ntfs-3g rw,defaults,umask=0000 0 0

or is there some other thing i need to change?

the /dev/hdb1 is where the partition you want to mount is located, and the /media/ntfs1 is where you want the partition to be mounted

the ntfs-3g is where you would put the filesystem type

so if you are trying to mount an ntfs drive, located at /dev/hdb1 in folder /media/ntfs1 then your line you typed is correct

---

### Post by Mustey on 2008-04-20
I did that, there were no errors.
I couldn't find the folder but after a lot of searching I have spotted something in the dev>disk>by label folder - there I saw the three labels of my old disk.

Also, in media folder, I see the ntfs1, 2 and 3 [B]but there are no files inside.
[/B]
Do you have an idea what's going on?

---

