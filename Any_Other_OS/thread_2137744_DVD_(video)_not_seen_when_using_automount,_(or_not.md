---
title: "DVD (video) not seen when using automount, (or not)"
date: 2013-04-21
forum: Any Other OS
---

### Post by codingman on 2013-04-21
I have setup and tested automount, but I am unable to see video DVDs. I am able to see other drives and DVD's with files only, but video DVDs are unable to be identified. Here is the output of dmesg | tail after putting the disc in:
```

    7.692160] EXT4-fs (sdd): VFS: Can't find ext4 filesystem
    7.693404] EXT4-fs (sdd): VFS: Can't find ext4 filesystem
    7.694744] FAT-fs (sdd): invalid media value (0xb9)
    7.694758] FAT-fs (sdd): Can't find a valid FAT filesystem
    7.770687] EXT4-fs (sdd2): unable to read superblock
    7.772454] EXT4-fs (sdd2): unable to read superblock
    7.774202] EXT4-fs (sdd2): unable to read superblock
    7.777263] FAT-fs (sdd2): invalid media value (0xb3)
    7.777277] FAT-fs (sdd2): Can't find a valid FAT filesystem
    8.228201] EXT4-fs (sdd5): mounted filesystem with ordered data mode. Opts: (null)

```
The square bracket at the beginning had to be removed, otherwise it gets mangled, thinking that it's BB Code.

Thanks in advance,
Codingman

---

### Post by matt_symes on 2013-04-21
Hi

It's looking for an ext4 filing system on the drive.

It should be looking for udf. 

I am not booted into Arch at the moment and this netbook has no CD/DVD drive, so i'm not sure how useful i can be.

If you manually mount the DVD does that read it ?

I can throw some generic, non Ubuntu related command your way though to check

What does this return 

```
grep udf /proc/filesystems
```

How's about this ?

```
modprobe -l | grep udf
```

On Ubuntu this returns
```

matthew-S206:/home/matthew/useful_commands_dir % modprobe -l | grep udf    
kernel/fs/udf/udf.ko
matthew-S206:/home/matthew/useful_commands_dir %
```

Is this module loaded ?

```
lsmod | grep udf
```

Here's the relevant part of the man mount page

```
man mount | less +/"Mount options for udf"
```

Hopefully that will get you started.

Kind regards

---

### Post by codingman on 2013-04-24
Thank you for the information, I will post the results.

---

### Post by codingman on 2013-04-24
> **matt_symes said:**
> Hi

It's looking for an ext4 filing system on the drive.

It should be looking for udf. 

I am not booted into Arch at the moment and this netbook has no CD/DVD drive, so i'm not sure how useful i can be.

If you manually mount the DVD does that read it ?

I can throw some generic, non Ubuntu related command your way though to check

What does this return 

```
grep udf /proc/filesystems
```

***This returns nothing.***

How's about this?

```
modprobe -l | grep udf
```

***There is no option for -l spitting the invalid operation error.***

On Ubuntu this returns
```

matthew-S206:/home/matthew/useful_commands_dir % modprobe -l | grep udf    
kernel/fs/udf/udf.ko
matthew-S206:/home/matthew/useful_commands_dir %
```

Is this module loaded ?

```
lsmod | grep udf
```

***This obviously returns nothing.***

Here's the relevant part of the man mount page

```
man mount | less +/"Mount options for udf"
```

Hopefully that will get you started.

Kind regards

I currently do not have the disc in, I will be able to get it tomorrow, so until then I can not test the setup. Good night!

---

