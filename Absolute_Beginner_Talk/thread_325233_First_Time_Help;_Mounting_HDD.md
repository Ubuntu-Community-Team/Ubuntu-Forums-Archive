---
title: "First Time Help; Mounting HDD"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by AtomBombmk2 on 2006-12-25
Hello All,

Today i finally got around to downloading ubuntu and creatinng a bootdisk.

Once loading up i noticed before the main interface came on the text came up;

"Mount: Function not implemented"

I have no access to my laptops HDD, i am currently using an Inspiron|6000 and i was wondinering anyone could help me mount the HDD.

Ive tried the commands:

Sudo mkdir /mnt/windowsntfs
Sudo mount /dev/hda1 /mnt/windowsntfs

all i get though is special device /dev/hda1 device does not exist. ... :<

---

### Post by dbbolton on 2006-12-25
did you edit your fstab ?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by AtomBombmk2 on 2006-12-25
> **dbbolton said:**
> did you edit your fstab ?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I tried doing that just now, ive worked out my windows partition is sda2 so now im working with that, ive attempted to follow the tutorial to a t, but it hasnt worked :/

the one part that doesnt cooperate is when i get to editing the fstab.

instead of having:

proc /proc proc defaults 0 0
/dev/hda6 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 0 2
/dev/hda1 /media/hda1 ntfs defaults 0 0
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0

all i have is:

unionfs / unionfs rw 0 0
tmpfs /tmp tempfs nosuid,nodev 0 0

ive tried adding the 

/dev/sda 2 /windows ntfs defaults 0 0 to the end but i have a feeling that isnt the correct thing to do, any more ideas?

---

### Post by taurus on 2006-12-25
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by AtomBombmk2 on 2006-12-25
> **taurus said:**
> What's the output of this command from a terminal?

```
sudo fdisk -l
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

    Device    Boot      Start            End        Blocks    Id    System
/dev/sda1                     1              11         88326   de   Dell Utility
/dev/sda2      *            12          4471    35824950    7    HPFS/NTFS 
/dev/sda3                4472          4863     3148740    db CP/M /  CTOS  /  ...

---

### Post by taurus on 2006-12-25
Edit your /etc/fstab and add this line to the end of it...

```

/dev/sda2   /media/sda2   ntfs   nls=utf8,umask=0222   0   0  

```
Save it.  Then, create a mount point and mount it.

```
sudo mkdir /media/sda2
sudo mount -a
df -h
```

---

### Post by Hendrixski on 2006-12-25
hey, I was using KNOPPIX to show some of my friends that their password protected windows OS didn't do **** to protect their files, but I had to unmount and remount the drive in write mode to show them that I could even change their files.  For me naturally this is done through the command line, but for them it seemed like they would never be able to remember the commands and was useless.  **Is there a GUI interface for mounting drives and partitions?**

---

### Post by LameBMX on 2006-12-25
well it sounds to me like you are currently on the live cd for install ... and in which case if you modify fstab you will need to 
mount -a 
afterwards ... and then the drives should be mounted correctly ... a previous post a person had a lot of issues gettin ubuntu installed strictly because he didnt trust ubuntu ... ubuntu is nice it plays well with windows (i think .. havent tried bootin back to vista since i installed ubuntu)

> /dev/hda1 /media/hda1 ntfs defaults 0 0

should reflect your drive
mkdir /media/windows
mount /dev/sda2 /media/windows ntfs 

if i got the cammands right (im a n00b) then voila in /media/windows should be your windows drive though that is not needed to install ubuntu

Easiest way .. boot back to windows ... run dialog .. enter compmgmt.msc ... (or browse start menu for administrative tools | computer management ) goto diskmgmt (run dialog diskmgmt.msc may also work .. i always mispell them the first try or two) 
so your at disk management and there is the partition(s) you was going to install ubuntu too .. followed by the partion for windows ... now here is where there is going to be a split depending on how you want to do this ... 
a) best on disk space .. saves a couple MB's 
look up how to swap drives (drive mapping i think its called) around using grub
delete the first partition ... so its raw blank space and then the windows partition ... 
reboot and install ubuntu
map drivesfor grub because ubuntu will create a couple partitions ... 
sda1 /
sda2 swap
sda3 (windows) (note root n swap may be switched around )
now whats gonna happen is you select windows at grub menu .. and grub passes this to ntloader .. that is on partition 3 and it thinks its on partition 2
follow the first directions to map sda3 to sda2 and prolly sda2 to sda3 to be consistent

B) the easy way .... 
reboot to windows and use diskmgmt to do this
make smallest possible partition at the front of the drive and move windows really close to the front ... and leave your ubuntu freespace after the windows partion so it will basically look like

AGAIN leave the space for ubuntu raw ... 
sda1 ntfs .. couple MB's or so
sda2 windows so its in the same spot for ntloader
raw freespace for ubuntu to make(
sda3 / ubuntu
sda4 swap (againt / and swap may be switched around) i would double check this but i got christmas stuff to do sorry 

of course the last way is gonna work the fastest and easiest

---

