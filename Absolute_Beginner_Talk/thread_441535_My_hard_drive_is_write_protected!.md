---
title: "My hard drive is write protected!"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-12
My drive is write protected..so I can't put any files in my hard drive.

so I right clicked the drive and properties, and permission, and then at the bottom, it says

"you are not the owner, so you can't change these permissions."

grrrr....help please..


oh and about my sound problem...please see my theother post..

I haven't been listening music on my cpu since I got ubuntu...:'(

---

### Post by FuturePast on 2007-05-12
Where exactly are you trying to write to? Your home directory?

---

### Post by rocketboys on 2007-05-12
> **FuturePast said:**
> Where exactly are you trying to write to? Your home directory?

Yes, 

/media/Life   
  

this is the path.

which used to be D: on the windows xp, I put all my works, pics, songs. 

but I can't do anything now...and I don't get why it says I'm not the owner.

---

### Post by taurus on 2007-05-12
Any chance it is a ntfs filesystem?

```
df -h
sudo fdisk -l
```

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by rocketboys on 2007-05-12
> **taurus said:**
> Any chance it is a ntfs filesystem?

```
df -h
sudo fdisk -l
```

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)


Yes..I think so..
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  2.4G   65G   4% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  136K 1014M   1% /proc/bus/usb
udev                 1014M  136K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   33M  981M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/sdb1             117G  100G   17G  86% /media/Life
danny@Dan:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9733     3229065    5  Extended
/dev/sda5            9332        9733     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15197   122069871    7  HPFS/NTFS
/dev/sdb2           15198       30401   122126130    f  W95 Ext'd (LBA)
/dev/sdb5           15198       30401   122126098+   7  HPFS/NTFS

I got those when I typed them on the prompt...

Thank you for the respond guys :)

---

### Post by taurus on 2007-05-12
Check out the link to install ntfs-3g and configure it so you can read and write to your ntfs filesystem, /dev/sdb1.

---

### Post by rocketboys on 2007-05-12
> **taurus said:**
> Check out the link to install ntfs-3g and configure it so you can read and write to your ntfs filesystem, /dev/sdb1.

Argh..

it says permission denied..!

why..:'(

permission isn't denied...

who denied that...:'(

---

### Post by taurus on 2007-05-12
What permission denied?  Would be nice if you include the command that you ran before you got that error message.

---

### Post by rocketboys on 2007-05-12
> **taurus said:**
> What permission denied?  Would be nice if you include the command that you ran before you got that error message.

I typed sudo apt-get install ntfs-3g. and I installed it, and then I typed,  /dev/sdb1.

now I got this..

danny@Dan:~$ /dev/sdb1
bash: /dev/sdb1: Permission denied
danny@Dan:~$ 

:'(

---

### Post by hessiess on 2007-05-12
carnt you log in as root?

---

### Post by rocketboys on 2007-05-12
> **hessiess said:**
> carnt you log in as root?

What's that..?

---

### Post by taurus on 2007-05-12
> **rocketboys said:**
> I typed sudo apt-get install ntfs-3g. and I installed it, and then I typed,  /dev/sdb1.

now I got this..

danny@Dan:~$ **[COLOR="Red"]/dev/sdb1[/COLOR]**
bash: /dev/sdb1: Permission denied
danny@Dan:~$ 

:'(

Where in that guide that it told you to run that command, /dev/sdb1?

```
sudo apt-get install ntfs-config
gksu ntfs-config
```

---

### Post by FuturePast on 2007-05-12
Don't worry about root. Not relevant.

---

### Post by rocketboys on 2007-05-12
> **taurus said:**
> Where in that guide that it told you to run that command, /dev/sdb1?

```
sudo apt-get install ntfs-config
gksu ntfs-config
```

Thank you for the response..

I installed those two, then I got this pop up says choose the drive you wish to configure or something..

so I clicked the d drive, but then I got this 

Mounting /media/And so on failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb5': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

hoo..:'(..

---

### Post by notquitemichael on 2007-05-12
um, this has happened to me before. assuming you can actually read and write to ntfs (i.e. all the support is on your system, which to my understanding is the case in feisty.) you just need to do the following,

in the command prompt:
gksudo nautilus

now when nautilus loads (i.e. a file browser window.) goto the directory /media right click on the folder choose properties, then select the tab permissions and change the owner to yourself.

n.b. if your a kde user you'll want to use;
sudo konqueror

obviously be careful and close the window once you've finished; don't wanna be mucking around with the file system as root.

:) hope that helped.

---

### Post by rocketboys on 2007-05-12
> **notquitemichael said:**
> um, this has happened to me before. assuming you can actually read and write to ntfs (i.e. all the support is on your system, which to my understanding is the case in feisty.) you just need to do the following,

in the command prompt:
gksudo nautilus

now when nautilus loads (i.e. a file browser window.) goto the directory /media right click on the folder choose properties, then select the tab permissions and change the owner to yourself.

n.b. if your a kde user you'll want to use;
sudo konqueror

obviously be careful and close the window once you've finished; don't wanna be mucking around with the file system as root.

:) hope that helped.

Thank you for the response!

omg I think I'm really close

I tried to change the owner to my self, but it says I can't change it because It is a read only disk..

:'(.!

---

### Post by notquitemichael on 2007-05-12
hmm, then you need to change the way it's mounted in fstab. i'll pass you on to [www.ubuntuguide.org](www.ubuntuguide.org) which has this step by step method: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

good luck.

---

### Post by rocketboys on 2007-05-12
> **notquitemichael said:**
> hmm, then you need to change the way it's mounted in fstab. i'll pass you on to [www.ubuntuguide.org](www.ubuntuguide.org) which has this step by step method: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

good luck.

Thank you for the Response...and the luck!

---

### Post by Tenicus on 2007-05-12
Hi, the error you are getting is one that occurs after Windows was not shut down properly.  When it isnt shut down properly, the HDs dont get unmounted or something of the sort.
Boot back into windows and then reboot

---

### Post by rocketboys on 2007-05-12
> **Tenicus said:**
> Hi, the error you are getting is one that occurs after Windows was not shut down properly.  When it isnt shut down properly, the HDs dont get unmounted or something of the sort.
Boot back into windows and then reboot

Thanks for the response!

"boot back into windows and then reboot"

On this part, do you mean I have to go on to windows?

because I don't think I have the windows anymore..

is there any other options...? :'(

---

### Post by Spartan.II.117 on 2007-05-12
Run ntfsfix version 1.13.1 on Linux unless you had Vista.
use the command sudo ntfsfix, and follow the instructions, which will probably tell you to install it using apt-get, do that

---

### Post by rocketboys on 2007-05-12
> **Spartan.II.117 said:**
> Run ntfsfix version 1.13.1 on Linux unless you had Vista.
use the command sudo ntfsfix, and follow the instructions, which will probably tell you to install it using apt-get, do that

Thank you for the response!

but I couldn't use the command you gave me, sudo ntfsfix, can you check again plz?

---

### Post by Spartan.II.117 on 2007-05-12
use this command first:
sudo apt-get install ntfsprogs

---

