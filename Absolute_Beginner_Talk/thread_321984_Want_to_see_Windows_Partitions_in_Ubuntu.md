---
title: "Want to see Windows Partitions in Ubuntu"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by rajat200 on 2006-12-19
Hi,
I am new to UBUNTU and would like to know how I can see the windows XP Home (NTFS) partitions?

Please be patient with me... thanks

Regards
Rajat Bhargava
[email]rajat.bhargava@rediffmail.com[/email]:-?

---

### Post by taurus on 2006-12-19
Here you go...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by rajat200 on 2006-12-19
Hi...
Thanks for helping me out so far...

This is what my fstab looks like :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd1
UUID=44117ece-2855-4a7b-b00d-5b319e779b2c /boot           ext3    defaults        0       2
# /dev/hdd5
UUID=22fbf698-f64d-435e-b44e-2fd9765abbad none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


I have two HDD's one is a SATA 80GB on SATA1 and the other is an IDE 80GB drive. I have installed UBUNTU on the IDE Drive.

I also upgraded the OS

Help please

---

### Post by taurus on 2006-12-19
Okay, post the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by rajat200 on 2006-12-19
rajat@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433        9728    58605120    f  W95 Ext'd (LBA)
/dev/sda5            2433        4864    19535008+   7  HPFS/NTFS
/dev/sda6            4865        7296    19535008+   7  HPFS/NTFS
/dev/sda7            7297        9728    19535008+   7  HPFS/NTFS

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1          31      248976   83  Linux
/dev/hdd2              32        9729    77899185    5  Extended
/dev/hdd5              32         193     1301233+  82  Linux swap / Solaris
/dev/hdd6             194        9729    76597888+  8e  Linux LVM
rajat@ubuntu:~$

---

### Post by taurus on 2006-12-19
So, I assume you want to mount /dev/sda1, /dev/sda5, /dev/sda6, & /dev/sda7...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
And add the following lines to the end of it...

```

/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
/dev/sda5   /media/sda5   ntfs   nls=utf8,umask=0222   0   0
/dev/sda6   /media/sda6   ntfs   nls=utf8,umask=0222   0   0
/dev/sda7   /media/sda7   ntfs   nls=utf8,umask=0222   0   0

```
Now, you need to create those four mountpoints and mount them.

```
sudo mkdir /media/sda1 /media/sda5 /media/sda6 /media/sda7
sudo mount -a
df -h
```

---

### Post by rajat200 on 2006-12-19
rajat@ubuntu:~$ sudo mkdir /media/sda1 /media/sda5 /media/sda6 /media/sda7
rajat@ubuntu:~$ sudo mount -a
rajat@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                       72G  2.2G   67G   4% /
varrun                218M   80K  218M   1% /var/run
varlock               218M     0  218M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm                218M     0  218M   0% /dev/shm
/dev/hdd1             228M   14M  202M   7% /boot
/dev/sda1              19G  4.9G   14G  27% /media/sda1
/dev/sda5              19G  6.9G   12G  37% /media/sda5
/dev/sda6              19G   11G  8.3G  56% /media/sda6
/dev/sda7              19G   16G  3.3G  83% /media/sda7
rajat@ubuntu:~$

Thanks...

this seems to be mounted.... Now the problem is... I cannot see the partitions in computer... Do we restart or is there any other way:confused:

---

### Post by taurus on 2006-12-19
There should be icons on your desktop!!!

---

### Post by rajat200 on 2006-12-19
Don't see them....

---

### Post by taurus on 2006-12-19
Maybe reboot!!!

---

### Post by rajat200 on 2006-12-19
just restarted gnome...

Ctrl+Alt+Backspace...

Do I do a reboot of the PC !!!

---

### Post by taurus on 2006-12-19
Reboot the machine.

---

### Post by rodney3 on 2006-12-19
Stupid question...

What does mounting your harddrive mean? and why do you do it?

---

### Post by rajat200 on 2006-12-19
Worked.......... Absolutely fine....  Yipeee....

Thanks a lot buddy... You made my day

I owe you one over the weekend :-D

---

### Post by tuxcantfly on 2006-12-19
> What does mounting your harddrive mean? and why do you do it?

The purpose of mounting is to put a block device, like /dev/sda1, into a readable/writable state on your filesystem. Other operating systems do it too; Windows mounts as drive letters (C:\, D:\), and Mac OS mounts drives as well.

---

### Post by rajat200 on 2006-12-19
> **rodney3 said:**
> Stupid question...

What does mounting your harddrive mean? and why do you do it?

Hey... I am new to this... Been with Windows for about 10 years and know it quite well... I need your help with Linux... So I am sorry If I seem to ask stupid questions

---

### Post by taurus on 2006-12-19
> **rajat200 said:**
> Worked.......... Absolutely fine....  Yipeee....

Thanks a lot buddy... You made my day

I owe you one over the weekend :-D
Okay, here is the info about mount thing...

[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

And all I want for xmas is a new 19" LCD to replace my old (1999) Dell 17" CRT!  :mrgreen:

---

### Post by rodney3 on 2006-12-19
So when would I do this? Or have I already? lol


I've got everything installed, just don't ask me to connect to the internet with Edgy.

---

### Post by taurus on 2006-12-19
> **rodney3 said:**
> So when would I do this? Or have I already? lol

You mean mounting your XP!

> I've got everything installed, just don't ask me to connect to the internet with Edgy.

What's wrong with your network connection?

---

### Post by rajat200 on 2006-12-19
> **taurus said:**
> Okay, here is the info about mount thing...

[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

And all I want for xmas is a new 19" LCD to replace my old (1999) Dell 17" CRT!  :mrgreen:

ok... I have a 17" LG monitor with me...but I'm in India... can surely do something for all of you once I come to the US of A

Thanks a lot again... and now....

Lets prepare for the weekend and drown our sorrows... Anyone coming to India !!!;)

---

### Post by rodney3 on 2006-12-19
> **taurus said:**
> You mean mounting your XP!



What's wrong with your network connection?




I have a wireless network setup, with me being wireless, and the Network Manager (or whatever) sees my wireless card, but doesn't have a name in parenthesis for it. I can enable it, but the internet still doesn't work.


By the way, when it wants me to input the SSID and such info, do I put the information of my current network?

I'm so confused

---

### Post by taurus on 2006-12-19
> **rajat200 said:**
> 
Lets prepare for the weekend and drown our sorrows... Anyone coming to India !!!;)

How long would it take to walk over there?  :twisted:

---

### Post by taurus on 2006-12-19
> **rodney3 said:**
> I have a wireless network setup, with me being wireless, and the Network Manager (or whatever) sees my wireless card, but doesn't have a name in parenthesis for it. I can enable it, but the internet still doesn't work.


By the way, when it wants me to input the SSID and such info, do I put the information of my current network?

I'm so confused
Maybe you need to use ndiswrapper to install a driver (from Windows) for your wireless card!  What is it anyway?

---

### Post by rajat200 on 2006-12-19
dont walk.... 
Take a bicycle and cross over from Alaska into Russia and then China... Travel over the Himalayas into Nepal to India... That seems like a nice trip over the weekend...  ;)

---

### Post by rodney3 on 2006-12-19
A Linksys WMP54G

I have ndiswrapper on my flash drive for when I'm in Ubuntu (*question at bottom), but I'm not sure how to execute the program. I DON'T KNOW WHAT TO CLICK! lol









Can I view my NTFS files for Windows while in Ubuntu?

---

### Post by rodney3 on 2006-12-19
Ok when installing ndiswrapper using the Terminal, I type in 

sudo tar xvzf ndiswrapper-1.31

and it says there is no file found with that name.

Any help?

---

### Post by taurus on 2006-12-19
Maybe you saved it to ~/Desktop...

```
cd ~/Desktop
tar xvzf ndiswrapper-1.31.tar.gz
cd ndiswrapper-1.31
(insert Ubuntu CD into the drive because you need the build-essential package on the CD before you can run the "./configure" command...)
sudo apt-add cdrom
sudo aptitude update
sudo aptitude install build-essential
./configure
make
sudo make install

```

---

### Post by rodney3 on 2006-12-19
Ok thanks, I'll try that


what is the 'xvzf' part for? If you don't mind..

---

### Post by taurus on 2006-12-19
Uncompress and extract in verbose mode...

```
man tar
```

---

### Post by rodney3 on 2006-12-19
> **taurus said:**
> Maybe you saved it to ~/Desktop...

```
cd ~/Desktop
tar xvzf ndiswrapper-1.31.tar.gz
cd ndiswrapper-1.31
(insert Ubuntu CD into the drive because you need the build-essential package on the CD before you can run the "./configure" command...)
**sudo apt-add cdrom**
sudo aptitude update
sudo aptitude install build-essential
./configure
make
sudo make install

```

When I put in the bolded line, it gave me back this:

"sudo: apt-add: command not found"


help!


Another question. In Windows, what would a .tar.gz file be? Like a .exe or a .zip?

---

### Post by macogw on 2006-12-19
.tar.gz is like .zip.  gz means "g-zip"
.deb would be like Setup.exe

sudo tar xvzf ndiswrapper-1.31
^ that's wrong.  It's -xvzf The - means those are the switches.  Just sitting there, they don't do anything

---

### Post by taurus on 2006-12-19
Must be getting late over here.  It should have been

```
sudo apt-cdrom add
```

---

### Post by rodney3 on 2006-12-19
Ok now it works; however, when I type in 

"./configure"


it says no such file or directory

and when I type

"make" 

it says no target specified and no makefile found

 "sudo make install"

it tells me no rule to make target 'install'



Another question. When I boot back into Edgy, should I start over with the code you gave me or should I start at a certain step (like after the build-essential part)?

---

### Post by ciscosurfer on 2006-12-19
> **macogw said:**
> [...]sudo tar xvzf ndiswrapper-1.31
^ that's wrong.  It's -xvzf The - means those are the switches.  Just sitting there, they don't do anythingActually, the dash ( - ) used for switches when using **tar** *does not *have to be there.  Create an archive and test it for yourself to check ;).  In other words```
tar xvzf ndiswrapper-1.31
```will do the exact same things as```
tar -xvzf ndiswrapper-1.31
```

---

### Post by rodney3 on 2006-12-19
> **rodney3 said:**
> Ok now it works; however, when I type in 

"./configure"


it says no such file or directory

and when I type

"make" 

it says no target specified and no makefile found

 "sudo make install"

it tells me no rule to make target 'install'



Another question. When I boot back into Edgy, should I start over with the code you gave me or should I start at a certain step (like after the build-essential part)?



*bump

---

### Post by taurus on 2006-12-19
> **rodney3 said:**
> Ok now it works; however, when I type in 

"./configure"


it says no such file or directory

and when I type

"make" 

it says no target specified and no makefile found

 "sudo make install"

it tells me no rule to make target 'install'



Another question. When I boot back into Edgy, should I start over with the code you gave me or should I start at a certain step (like after the build-essential part)?

Did you unpack it first?  What's the output of this command then?

```
ls -la ~/Desktop
```

---

### Post by rodney3 on 2006-12-19
I don't think I've unpacked it. I wouldn't even know how to! lol

How would I go about doing that?

---

### Post by rodney3 on 2006-12-20
*bumpity bump

---

### Post by SigmaX6 on 2006-12-20
sudo lshw says my 160 gig drive is logical name: /dev/hdb and gedit doesnt recognize my hdd. Below is about as far as i got. Pleease let me know what im doing wrong thnks



sigma@sigma:~$ sudo mkdir /media/hdb
sigma@sigma:~$ sudo mount /dev/hdb /media/hdb
mount: you must specify the filesystem type
sigma@sigma:~$ sudo mkdir /media/hda5
sigma@sigma:~$ sudo mount /dev/hda5 /media/hda5
/dev/hda5 looks like swapspace - not mounted
mount: you must specify the filesystem type
sigma@sigma:~$

---

### Post by macogw on 2006-12-20
> **ciscosurfer said:**
> Actually, the dash ( - ) used for switches when using **tar** *does not *have to be there.  Create an archive and test it for yourself to check ;).  In other words```
tar xvzf ndiswrapper-1.31
```will do the exact same things as```
tar -xvzf ndiswrapper-1.31
```

O_O crazy!

---

### Post by macogw on 2006-12-20
> **SigmaX6 said:**
> sudo lshw says my 160 gig drive is logical name: /dev/hdb and gedit doesnt recognize my hdd. Below is about as far as i got. Pleease let me know what im doing wrong thnks



sigma@sigma:~$ sudo mkdir /media/hdb
sigma@sigma:~$ sudo mount /dev/hdb /media/hdb
mount: you must specify the filesystem type
sigma@sigma:~$ sudo mkdir /media/hda5
sigma@sigma:~$ sudo mount /dev/hda5 /media/hda5
/dev/hda5 looks like swapspace - not mounted
mount: you must specify the filesystem type
sigma@sigma:~$

Try
sudo mount /dev/hdb1 /media/hdb
and see if you get a better result

---

### Post by SigmaX6 on 2006-12-20
> **macogw said:**
> Try
sudo mount /dev/hdb1 /media/hdb
and see if you get a better result

unfortuantly it did not allow me to see the partition. under media.

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+  42  SFS

---

### Post by batinzedesert on 2006-12-20
Hi
I had the same problem and I tried the code
It worked, but it doesn't appear on the desktop- it's in the media folder, as HDA5 (for you it'd be SDAsomething...).
Any idea how I make desktop shortcuts?

---

### Post by SigmaX6 on 2006-12-20
hey ive tried almost every line of code that was posted and so far ive got two empty folders in media called hdb hd5. I mounted it up in a usb hdd case and it clicked no probs.... Im not sure why it isnt mounting. got it set to slave. Shows up in windows

---

### Post by hkq35 on 2007-01-18
> **taurus said:**
> So, I assume you want to mount /dev/sda1, /dev/sda5, /dev/sda6, & /dev/sda7...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
And add the following lines to the end of it...

```

/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
/dev/sda5   /media/sda5   ntfs   nls=utf8,umask=0222   0   0
/dev/sda6   /media/sda6   ntfs   nls=utf8,umask=0222   0   0
/dev/sda7   /media/sda7   ntfs   nls=utf8,umask=0222   0   0

```
Now, you need to create those four mountpoints and mount them.

```
sudo mkdir /media/sda1 /media/sda5 /media/sda6 /media/sda7
sudo mount -a
df -h
```

Thank you to the Taurus for this post, it worked well for my sda1 drive
However I wish do the same thing again , this time for another hard disk

$ sudo fdisk -l
Password:

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9352    75119908+  83  Linux
/dev/hdc2            9353        9729     3028252+   5  Extended
/dev/hdc5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17383   139628916    7  HPFS/NTFS
/dev/sda2           17384       19457    16659405    5  Extended
/dev/sda5           17384       19457    16659373+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2       19457   156280288+   b  W95 FAT32


I wish to access the data on my  sdb2 sdb5 ( whichever one it is ) I wonder can someone please post commands similar to the instructions in the quote, as they were great and worked a treat.
Simply substituting sdax for sdbx didn't work,as you can see


~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

thanks!

---

### Post by bodhi.zazen on 2007-01-18
sdb2 will not mount

sdb5 ; same as above, change "ntfs" to "vfat:

/dev/sdb5   /media/sdb5   vfat   nls=utf8,umask=0222   0   0

Then mount -a

---

### Post by hkq35 on 2007-01-18
Thanks for the reply sadly something went wrong,


I added the line to:

/dev/sdb5 /media/sdb5 vfat nls=utf8,umask=0222 0 0

to   /etc/fstab

then in command tried

~$ sudo mount -a
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by hkq35 on 2007-01-18
Its working now! 

Solution:
Work around, went back to XP and changed my drive from FAT32 to NTFS.
Thanks to Bodhi.Zazen for indicating which partition (sdb5) to mount.

---

