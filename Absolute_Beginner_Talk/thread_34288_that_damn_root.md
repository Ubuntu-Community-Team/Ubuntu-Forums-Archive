---
title: "that damn root"
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by shador on 2005-05-14
i have a shared partition between ubuntu and WinXP. While i'm in WinXP i can do whatever i want with the partition. But when i'm in ubuntu i can't do anything. The rights to the partition is set to root. 

How can i change the rights from root to my account?

---

### Post by Gandalf on 2005-05-14
[QUOTE=shador]i have a shared partition between ubuntu and WinXP. While i'm in WinXP i can do whatever i want with the partition. But when i'm in ubuntu i can't do anything. The rights to the partition is set to root. 

How can i change the rights from root to my account?[/QUOTE]
look at this usefull links, i put all cases....

 [How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only?](http://ubuntuguide.org/#mountunmountntfs) 
[How to mount/unmount Windows partitions (FAT) manually, and allow all users to read/write?](http://ubuntuguide.org/#mountunmountfat) 
[How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?](http://ubuntuguide.org/#automountntfs) 
[How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write?](http://ubuntuguide.org/#automountfat)

hope it helps

---

### Post by shador on 2005-05-14
I was able to change the permission on /mnt from root to my username. 

But the partition inside /mnt (/mnt/lager) was still adressed to root. Shouldn't the ownership change for subfolders too?

---

### Post by poofyhairguy on 2005-05-14
[QUOTE=shador]I was able to change the permission on /mnt from root to my username. 

But the partition inside /mnt (/mnt/lager) was still adressed to root. Shouldn't the ownership change for subfolders too?[/QUOTE]


Use 

/media

instead of

/mnt

trust me.

---

### Post by shador on 2005-05-14
well uhm. okay thanks i'll remember that. But how can i fix it now? can i move it to /media or what?

---

### Post by Gandalf on 2005-05-14
/etc/fstab
```

/dev/hdaX       /wherever_the_mount_point_is            vfat    defaults,uid=XXX,gid=YYY,umask=000        0       0

```

this will give you a partition with umask 000 which means read/write to all users
if you still insist to have it in your uid/gid then fill the XXX and YYY with your uid/gid if not just remove the uid=XXX and gid=YYY

---

### Post by shador on 2005-05-14
I'm sorry. But i don't quite understand you.   

I just saw that the whole filesystem is set to root. How can i change that to my username

---

### Post by Gandalf on 2005-05-14
[QUOTE=shador]I'm sorry. But i don't quite understand you.   

I just saw that the whole filesystem is set to root. How can i change that to my username[/QUOTE]
 by changing the line in /etc/fstab as i described aboce

---

### Post by shador on 2005-05-14
I  wrote "/dev/hdaX       /mnt/lager         vfat         defaults,uid=XXX,gid=YYY,umask=000       0      0"  But it still didn't work.

Im guessing  i did something wrong with the uid/gid thing

---

### Post by fng on 2005-05-15
Did you reboot after adjusting /etc/fstab?

---

### Post by adun on 2005-05-15
No need for a reboot its not xp =), just umount und mount the hd again.

Shador did you read and understand 'man mount'?

Hope you replaced all x and y....

---

### Post by Gandalf on 2005-05-15
man!!!!!!!!!!!!!!! not /dev/hdaX, X and Y are letters to replace!
ok you should say from the beginning that you are a noob, ok here's a full guide
first you need to know where is your fat partition, so
```

sudo fdisk -l /dev/hda

```

you will see a table of partition look at the left there's the filesystem note the name of the fat one
for example
in my case i have
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/hda2            1306        4952    29294527+  83  Linux
/dev/hda3            4953        9703    38162407+   f  W95 Ext'd (LBA)
/dev/hda4            9704        9729      208845   88  Linux plaintext
/dev/hda5            4953        9414    35840983+   b  W95 FAT32
/dev/hda6            9415        9703     2321361   83  Linux

```

so it's /dev/hda5 in my case



now it's turn to decide where to mount it like /fat or maybe /home/shared or maybe /i_am_a_fat :lol: just decide wherever you want to... let's say (just for the guide) that it's /fat

so we must create it first
```

sudo mkdir /fat

```
now everything is ready let's prepare the partition,

```

gedit /etc/fstab

```

instert into
```

/dev/hdaX       /wherever_the_mount_point_is            vfat    defaults,umask=000        0       0

```
replace X with the partition number, in my case it will be

```

/dev/hda5       /fat            vfat    defaults,uid=XXX,gid=YYY,umask=000        0       0

```

now you have tou mount it, in my case i type
```

sudo mount /fat

```

i hope it helps now

---

### Post by shador on 2005-05-15
Thank you Gandalf for explaining this to me. Now i got it mounted on /fat. 

But the rights to /fat still belongs to root :( Why does the root hate me? I would like to change the rights of /fat to my username

---

