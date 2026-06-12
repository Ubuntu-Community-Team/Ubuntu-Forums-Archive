---
title: "Access to drive partition"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by Patrissimo on 2005-09-24
I'm 4 hours into Ubuntu. I tried to mount my hda6, which is a FAT32 partition that I used in XP. It says it's already mounted. But I can't seem to find it!
How do I get access to it?

Also, I used the apt-get command to try to install some programs, as indicated in the online Ubuntuguide. but it said they weren't found, if the program isn't on the list in synaptic, does that mean I can't install it? Can I do something to get it there? I haven't done any compiling yet, is that what I need to do?

Sorry for the basic questions.  I could use a guide for Linux that assumes I know nothing, which is 99.44% true. I know I've got a lot to learn.

---

### Post by PsyberOneZero on 2005-09-24
>  I haven't done any compiling yet, is that what I need to do?
With Ubuntu and most major distributions you shouldn't have to do any compiling, atleast for all but the most bleeding edge or obscure programs.  It's something that is good to know but for the time being just get comfortable with linux itself, then you can go to more advanced stuff.

---

### Post by bored2k on 2005-09-24
[list=1]
[*]**Programs:** [How to add extra repositories?](http://ubuntuguide.org/#extrarepositories) 
Make sure you did that step correctly. That is vital for you to get some of the applications you want. 


[*]**Mounting Partitions.**
[list]
[*]Execute the commands in **Terminal mode** (Applications -> System Tools -> **Terminal**)
[/list] 
```
df -h
``` 
The above will show your already mounted partitions and their locations.


```
sudo fdisk -l
``` 
In case it is not mounted (or mounted incorrectly), the above will show you your entire partition table.

If it is not mounted and saying that the FAT32 drive is in /dev/hda2, you would do this set of commands.
```
sudo mkdir /media/Windows
``` ```
sudo gedit /etc/fstab
``` Append the following line at the end of the file:
```
/dev/hda2       /media/Windows  vfat    umask=000   0       0
``` Now save and
```
sudo mount -a
``` 

If you open your browser and go to /media/Windows, you should be able to see your drive.


[*]**Partition tip**:
```
sudo /etc/init.d/dbus-1 restart
``` [/list]
The above will place an Icon of your desktops:

---

### Post by Patrissimo on 2005-09-24
Thanks for replying so quickly.

What it says after    sudo fdisk -l    is:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              15G  1.8G   12G  13% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev                   15G  1.8G   12G  13% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
/dev/hda6              34G   20G   15G  58% /mnt

Can I assume it's mounted correctly?
Still, I can't find it to use the files.

---

### Post by Patrissimo on 2005-09-24
Oops, this is  the command I used.
I'm trying to get access to hda6, which is where I saved my files from XP, back when I was a Windows user yesterday
:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              15G  1.8G   12G  13% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev                   15G  1.8G   12G  13% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
/dev/hda6              34G   20G   15G  58% /mnt

---

### Post by PsyberOneZero on 2005-09-24
```
/dev/sda5              49G  3.5G   43G   8% /
tmpfs                 500M     0  500M   0% /dev/shm
tmpfs                 500M   14M  487M   3% /lib/modules/2.6.12-9-amd64-k8/volatile
/dev/sdb1             184G   88G   87G  51% /home
/dev/sda1              25G   18G  7.4G  70% /media/WindowsXP
/dev/sda6              38G  8.9G   29G  24% /media/Longhorn
``` 

Just to give you an example.

It looks like your fstab entry for /dev/hda6 is wrong, follow bored2k's instructions, It's all spelled out there.

You can post your /etc/fstab if you want us to help you with it

---

### Post by bored2k on 2005-09-24
I agree with PsyberOneZero, post your /etc/fstab, your fdisk -l, your df -h all in one post and tell us just what is it that you want. And for the love of the twinkies, please use ```
[code][ /code]!
```

---

### Post by Patrissimo on 2005-09-24
OK, here's this one

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

and sudo fdisk -l

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1021     8195008+  17  Hidden HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2            3050        9729    53657100    f  W95 Ext'd (LBA)
/dev/hda3            1153        3049    15237652+  83  Linux
/dev/hda4            1021        1152     1058400   82  Linux swap / Solaris
Partition 4 does not end on cylinder boundary.
/dev/hda5            3051        4874    14651280    7  HPFS/NTFS
/dev/hda6            5355        9729    35138848+   b  W95 FAT32
```

and df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              15G  1.8G   12G  14% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev                   15G  1.8G   12G  14% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
/dev/hda6              34G   20G   15G  58% /mnt
```


"I agree with PsyberOneZero, post your /etc/fstab, your fdisk -l, your df -h all in one post and tell us just what is it that you want. And for the love of the twinkies, please use
Code:

[code][ /code]!"

I have files on hda 6 that I want to access. as I said in my original post, I'm green at Ubuntu.
What the heck is "[code][ /code]!"?

---

### Post by bored2k on 2005-09-24
You have to read our instructions. I clearly explained how to do it, you just had to switch hda2 for hda6.

```
sudo umount /mnt
``` 
```
sudo mkdir /media/Windows
``` 
```
sudo gedit /etc/fstab
``` Append the following line at the end of the file:
```
/dev/hda6       /media/Windows  vfat    umask=000   0       0
``` Now save and
```
sudo mount -a
``` 
```
sudo /etc/init.d/dbus-1 restart
```

---

### Post by PsyberOneZero on 2005-09-24
> What the heck is "[code][ /code]"?

There is a button above the text area that looks like "#", that will wrap CODE tags around anything you want to show as code (terminal commands, terminal output, etc..)
or you can just type "[code]", paste your results, "[ /code]"

It's just much easier on the eye and easier to distinguish output from chatter :smile:

It gets easier, I promise, just take it slow and soon you'll be posting help for other people

---

### Post by bored2k on 2005-09-24
[QUOTE=PsyberOneZero]exactly what you did when posting all of your results.  It's just much easier on the eye and easier to distinguish output from chatter :smile:

It gets easier, I promise, just take it slow and soon you'll be posting help for other people[/QUOTE]
 Actually, I modified his post and coded all of his schtuff ;).

---

