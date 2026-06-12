---
title: "Problems mounting windows drive"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by Josh_b on 2006-07-29
Hey

Before I installed linux I had a SATA drive in two partitions (1 for Windows, and 1 for games and stuff) and an IDE drive. I installed Ubuntu onto the IDE drive and when I try and mount the Games partition it displays the following error:

error: device /dev/sda5 is not removable

error: could not execute pmount

Any help would be appreciated

Thanks,
Josh

---

### Post by CameronCalver on 2006-07-29
what command did you do to mount it 
do sudo fdisk -l and then see what it is then do and did you make a folder to mount it

is this what you did 

```
sudo mount /dev/xxx /mnt/xxx
``` ?

---

### Post by GaryReggae on 2006-07-29
I am having a similiar problem.  I can mount my windows drive by goint into the System menu | Administration | Disks , choosing a path and then clicking Enable but it loses this every time I reboot.  If your Windows drive is the Primary HDD then it will be hda0, if it is the secondary drive then it will be hda1.  The Disk Manager tells you the capacity of each drive anyway so you can kind of figure out which is which.

I have tried typing in the command you mentioned but it says you must specify the file system.  Mine is FAT32 but I'm not sure how to specify that and suspect it would lose the mount on reboot anyway.

Is there a way of making a mount 'Permanent'?  It would be very handy as I have all my working files on the C (windows) drive at the moment.

---

### Post by Herman on 2006-07-29
There are two ways to mount other filesystems 
[LIST=1]
[*]By using a 'mount' command, this method is most popular when running from a LiveCD, but can also be used from a hard-disk installed system. It is only for one session.
[*]By making an entry in /etc/fstab, this method is commonl used with a hard-disk installed system where the mounted filesystem will be automatically remounted at each bootup. It is more permanent.[/LIST]There are three essential steps for each method
[LIST=1]
[*]Find out the detials of the partitions on the disk. This information is easiest to gather by using your favourite disk partitioning software such as GParted 'System'->'Administration'-> 'Gnome Partition Editor', and take a look.  The more traditional method is to use the  following command ```
sudo fdisk -l
``` Specifically, you need to find out what the proper Linux designation is for the partition you want to mount, for example /dev/hda1 or /dev/hdb3 or the like. You also will need to know the filesystem type, such as FAT32, NTFS, ext3, reiserfs or whatever.
[*]Make a mount point. A mount point is just a directory (folder). Popular locations to make this mount point in are /mnt, or /media. In Ubuntu if you make it in /media, it will be given an icon on your desktop. You will need to use a 'sudo' command to make a directory in one of those locations. You can also make your mount point in another location, such as in your /home/username directory. That gives easy access and keeps your desktop clear, but might not be so secure.
[*]Either (a)issue the appropriate 'mount' command for the filesystem you want to mount, or (b) make the appropriate entry in /etc/fstab, and reboot or use the sudo mount -a command.[/LIST] 
[LEFT]
[/LEFT]

---

### Post by Herman on 2006-07-29
Josh_b,
 If you want to mount your 'Games' partition, you would find out it it is /dev/sda5 for sure or not with the command sudo fdisk-l or I guess looking at it in 'Disks Manager would be good too, and what filesytem it is like FAT32 or NTFS.

Then you make a new directory (mount point)  in /media for example with a command like this one, ```
sudo mkdir /media/games
``` 
Then you would make a backup of your /etc/fstab file for safety, ```
sudo cp /etc/fstab /etc/fstab_backup
``` 
After that you open your /etc/fstab file with a text editor and add an appropriate line into it,```
sudo gedit /etc/fstab
``` 
Add a line something like this (below) in to it if it has an NTFS filesystem, 
```
/dev/sda5 /media/games  ntfs  nls=utf8,umask=0222      0          0
``` But if it has a FAT32 filesystem, add a line like this, (below)
```
/dev/sda5 /media/games  vfat iocharset=utf8,umask=000       0            0
``` Here's a link with some illustrations that might help, but it's about mounting another Linux system, not about mounting a Windows partition, but at least it shows how to paste a line into an /etc/fstab file, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu").


I hope that helps you, please ask again if you still have trouble, Regards, Herman :D

---

### Post by Herman on 2006-07-29
GaryReggae,
If you have a Windows FAT32filesystem you want to mount, you can just almost the same thing.
```
sudo mkdir /media/windows
``` ```
sudo cp /etc/fstab /etc/fstab_backup
``` ```
sudo gedit /etc/fstab
``` 
And add in a line something like: 
```
/dev/hda1 /media/windows    vfat   iocharset=utf8,umask=000  0   0 
``` But you need to check in 'Disks Manager and make sure 'device: is /dev/hda1, if not replace '/dev/hda1' where I have that on the line above with whatever it really is for you (or your computer).
```
sudo mount -a
```
Here is an excellent link on mounting Windows partitions by aysiu, [Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows.php")
It would be a good idea to have a look at that one before you do anything.
Regards, Herman :D

---

### Post by GaryReggae on 2006-07-29
Herman: Thanks very much - that worked an absolute treat! :KS

---

### Post by Josh_b on 2006-08-07
Thanks Herman. That worked. Although, how do I open .exe files?

---

### Post by nexxus on 2006-08-08
exe files are Windows executables, and they don't natively run on Linux. There is a product called Wine that provides a layer of emulation to run *some* Windows apps.

You can try a search for wine & the name of your app and you may even get a HOWTO if the app is supported.

---

### Post by CameronCalver on 2006-08-08
Wine's aim is to get every windows app to run on linux and they are doing a dam good job at it most apps work but they have a bit to go yet and there is  another thing called **Crossover office**it is another layer over the top of wine it also works pretty well but there is one main thing that is not good about crossover **its not open source**

---

