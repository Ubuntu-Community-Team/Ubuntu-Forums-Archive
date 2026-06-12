---
title: "[SOLVED] Bad HD partitoning , on setup ?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Silvain on 2008-01-08
In my system monitor, it shows only one partition. I have at least 5, Need to know some bash commands to tell whats going on with the HD, 

```
silvain@wet-athlon:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5              21G  3.2G   17G  17% /
varrun                506M   92K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   72K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm

```

This is like a 160 Gbyte HD so I must have some partitions not being used , This does not add up to anyways near 160 Gbyte.

```
silvain@wet-athlon:~$ sudo fdisk -l
[sudo] password for silvain:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4cc051fb

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       12000    96389968+  83  Linux
/dev/hda2           12001       15500    28113750   83  Linux
/dev/hda3           15501       16643     9181147+  82  Linux swap / Solaris
/dev/hda4           16644       19457    22603455    5  Extended
/dev/hda5   *       16644       19334    21615426   83  Linux
/dev/hda6           19335       19457      987966   82  Linux swap / Solaris

```

Can someone tell me what command to use to investigate the "/dev/hda1" space used on the different partitions by my system ?

---

### Post by hyper_ch on 2008-01-08
just mount it:

(1) create a mount point 
```

sudo /media/sda1

```

(2) mount the partition
```

sudo mount /dev/sda1 /media/sda1

```

(3) there you go

---

### Post by Silvain on 2008-01-08
Hi Hyper_CH, tried step 1 and got this.
```
silvain@wet-athlon:~$ sudo /media/sda1
sudo: /media/sda1: command not found

```

ok, what now?

---

### Post by hyper_ch on 2008-01-08
my mistkae

```

sudo mkdir /media/sda1

```

---

### Post by Silvain on 2008-01-08
> **hyper_ch said:**
> my mistkae

```

sudo mkdir /media/sda1

```

ok that got step 1, still trying on step 2 , got this output.

```
silvain@wet-athlon:~$  sudo mount /dev/sda1 /media/sda1
mount: special device /dev/sda1 does not exist

```

Ok, what now ?

---

### Post by forestpixie on 2008-01-08
Perhaps the references to sda* should be hda*

```
sudo mount /dev/hda1 /media/sda1
```

Would I think mount hda1 in the driectory you made called sda1

which could probably get confusing - maybe redo the mkdir to reflect hda*

```
sudo mkdir /media/hda1
```

then

```
sudo mount /dev/hda1 /media/hda1
```

---

### Post by hyper_ch on 2008-01-08
yeah, another typo....

well, I'm sick so I'm excused ;)

follow the advice above and also do

```

sudo rmdir /media/sda1

```

---

### Post by forestpixie on 2008-01-08
let you off that one then :) - would the op need to add this to fstab to get it each time

this mkdir and mount stuff is all a bit new to me?

---

### Post by hyper_ch on 2008-01-08
the OP wouldn't need to add the mkdir to his fstab but the actualy mounting...

Entries like this:

```

/dev/hda1       /media/hda1     ext3    defaults        0       2

```

---

### Post by forestpixie on 2008-01-08
thanks - one more little bit of knowledge assuming I can remember, perhaps I'll add it to little book of stuff :D

---

### Post by Silvain on 2008-01-08
Ok, did this:
 ```
silvain@wet-athlon:~$ sudo mkdir /media/hda1
silvain@wet-athlon:~$ sudo mount /dev/hda1 /media/hda1
```

So now with :
```
silvain@wet-athlon:~$  df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5              21G  3.2G   17G  17% /
varrun                506M   92K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   72K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/hda1             150G   14G  136G  10% /media/hda1

```

I get this.

Sweet, now I see that theres some trash left in there from prior use from another computer setup, that I am wanting to delete.But I cannot, so there must be some steps needed to take the folders ownership. Time to do a little searching on forum , unless someone knows. :lolflag:

---

### Post by forestpixie on 2008-01-08
try adding it to your fstab - hyper's last post I think - reply to a question from me

```
sudo cp /etc/fstab /etc/fstab.bak
```

```
gksudo gedit /etc/fstab
```

add the line he shows to the end of the file in a new line, save and close then reboot

---

### Post by Silvain on 2008-01-08
Tried this:
```
silvain@wet-athlon:~$ sudo chown -R silvain:silvain /media/hda1
[sudo] password for silvain:
chown: changing ownership of `/media/hda1/System Volume Information': Operation not permitted

```

Oh, also had a whole lot of variations on that Operation not permitted message for everything else on that  partition. I am still on the uphill part of the learning curve it appears. Maybe I can just format the Hda1 partition to clean it off?

---

### Post by Silvain on 2008-01-08
> **forestpixie said:**
> try adding it to your fstab - hyper's last post I think - reply to a question from me

```
sudo cp /etc/fstab /etc/fstab.bak
```

```
gksudo gedit /etc/fstab
```

add the line he shows to the end of the file in a new line, save and close then reboot

Ok did that then added this per hyper's post to end of fstab:
 ```
/dev/hda1       /media/hda1     ext3    defaults        0       2
```

Ok, off to reboot and see what happens. :popcorn: Thanks for the helps :)

---

### Post by Silvain on 2008-01-08
Ok, the "Fsck died while trying to open /dev/hda1 ". Says the superblock could not be read. 

Sounds like we need a format. Is that right? I have not done that before in Ubuntu or Linux yet here. What would that be command wise ? Or is there something better to do still ?

---

### Post by Silvain on 2008-01-08
Update, found a site with format instruction. Here is what my terminal said.

```
silvain@wet-athlon:~$ sudo  mke2fs -j /dev/hda1
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
12058624 inodes, 24097492 blocks
1204874 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
736 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 28 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```

Wow , will see what happens on reboot, Hope this is a fix, I still have a few more systems here, if not .

---

### Post by Silvain on 2008-01-08
Ok this system still works, and is booting up with the hda1 mounted now. But its owned by root. Tried some commands still it belongs only to root, Please help, 
TIA
Silv

---

### Post by Silvain on 2008-01-08
Update, evidently not all changes done to permissions show up immediately. Had done this:

```
silvain@wet-athlon:~$ sudo su
root@wet-athlon:/home/silvain# umount /dev/hda1
root@wet-athlon:/home/silvain# sudo chown -R silvain:silvain /hda1
chown: cannot access `/hda1': No such file or directory
root@wet-athlon:/home/silvain# sudo chown -R silvain:silvain /media/hda1
``` 

And checked on the file, still had permissions set to owner at the time. After reboot they show as owned by silvain now

In terminal on entry now:```
filesystem            Size  Used Avail Use% Mounted on
/dev/hda5              21G  3.2G   17G  17% /
varrun                506M   92K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   84K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/hda1              91G  188M   86G   1% /media/hda1

```

On adding up the spaces used by my file system, This only amounts to 114 Gigabytes. So still my system is missing out, on making use of some HD space it seems. Looks like something like 46 something Gigabytes of space is still not listed. Maybe not done yet here, but some very real progress at least :guitar:

Thanks for all the helps :)

Silv

---

### Post by forestpixie on 2008-01-09
perhaps the remaining space is in hda2 - you maybe need to do the same process for that partition

---

### Post by Silvain on 2008-01-09
Have been trying to repeat , prior process on /dev/hda2. But it refuses to allow permissions to be changed, ](*,) 

I even deleted its partition and reformatted it and have then tried to change its permissions again.

---

