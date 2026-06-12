---
title: "Secondary Hard drive"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by sonrise on 2007-01-04
When I installed the ubuntu it would not allow me access to my secondary harddrive it say I have no permission to view since I am not the owner where did I go wrong?

---

### Post by taurus on 2007-01-04
What filesystem is it and how did you mount it?  Paste the output of these commands here...

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by sonrise on 2007-01-04
The secondary drive is NTFS on an older version of ubuntu all I had to do was go to disk management and activate the drive but under the new 6.06 it gives the permission ownership message

---

### Post by taurus on 2007-01-04
Do you mount that ntfs partition by hand or do you mount it through /etc/fstab?  What's the output of those three commands from a terminal?

---

### Post by sonrise on 2007-01-04
--------------------------------------------------------------------------------

"Do you mount that ntfs partition by hand or do you mount it through /etc/fstab"

I am not sure what you mean by fstab?

I do not use the console I just use the GUI and go to the disk manager to get to the drive it has always worked in the older versions of ubuntu but not the 6.06

---

### Post by sonrise on 2007-01-04
I would like to be able to log on to root like I used to do under Slax but ubuntu will not allow me access if I could use root I could get the the secondary drive.

---

### Post by taurus on 2007-01-04
Okay, I am going to try this one more time (3rd time).  What's the output of these three commands?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

p.s.  You don't need to log in as root to mount the second harddrive!

---

### Post by sonrise on 2007-01-04
Okay, I am going to try this one more time (3rd time). What's the output of these three commands?

I dont under stand what you mean I am very new at linux?

---

### Post by sonrise on 2007-01-04
I don't mean to be a problem I guess I am in the wrong place I thought this site was for beginners sorry for the inconvience

---

### Post by taurus on 2007-01-04
> **sonrise said:**
> 
I dont under stand what you mean I am very new at linux?

Open a terminal by clicking Applications (upper left), then Accessories, and then Terminal!  That will bring up a gnome-terminal for you to type something in.

Now, type the first command and paste the output here.

```
sudo fdisk -l
```
Then the next command.

```
cat /etc/fstab
```
And the last command...

```
df -h
```

---

### Post by Cogito² on 2007-01-04
Hi I'm trying to mount my ntfs hard drive and access it with my linux box so my problem is apparently similar. Here are my results of putting in those commands in the terminal:

```
thomas@thomas-linux:~$ sudo fdisk -l
Password:

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30515   245111706    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9355    75144006   83  Linux
/dev/hda2            9356        9732     3028252+   5  Extended
/dev/hda5            9356        9732     3028221   82  Linux swap / Solaris
thomas@thomas-linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
thomas@thomas-linux:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda1              71G   51G   17G  75% /
varrun                506M  116K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  148K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-27-386/volatile

```

I want access to the 250 gb drive. Thanks for any help you can give me.

---

### Post by taurus on 2007-01-04
Okay, so you want to mount /dev/sda1.  First, you need to edit your /etc/fstab so you can add an entry for that partition/drive.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll down to the end and add this line to it.

```
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create a mount point and mount it...

```
sudo mkdir /media/sda1
sudo mount -a
df -h
```

---

### Post by Cogito² on 2007-01-04
Oh thank you so much. That works now. I've been screwing around trying to network my windows and linux box for two days now just so that I could make this one (large) file transfer. Nothing seemed to work right (or more accurately I couldn't make it work right). In the end it was so easy. Oh well live and learn I guess. Thank you so much. Now it's time to start the file transfer and crack open a beer. Cheers.

edit. Never mind. I need to change the permissions on that folder. How do I change it so that I can read/write to it (without using sudo/terminal which I'm not very good at)?

edit2. The file owner is "root" of which I know little about, except that I'm not supposed to log into it and use it as my main user for security reasons (which doesn't really matter for me, since I don't know how to log into it anyway).

---

### Post by taurus on 2007-01-04
NTFS only allows you to read from it.  If you want to write to it, you need to install ntfs-3g.  Here's a guide...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by Cogito² on 2007-01-04
There's always a catch!

But it's okay, since my sister (who knows nothing of computers) just walked in and asked, "Why don't you just save the files on my IPOD?" I then slapped myself, since I forgot that an IPOD can act like a storage drive. I have a flash drive but it's only 256 mb which isn't large enough. Her's is 30 gigs which is enough to do the transfer in two bits.

So I guess I'm just an idiot that beats complicated solutions to problems into the ground before doing the easy stuff. Well thanks anyway for helping me so far. Have a good one.

---

### Post by taurus on 2007-01-04
So I guess the moral of the story is you should always listen to your sister!!!

---

### Post by Cogito² on 2007-01-04
She is very wise indeed.

---

### Post by Hishgraphics on 2007-01-06
Hi everyone,
I just installed Ubuntu on my P3 machine. I have 2 internal hard disk drives - a 20GB (where Ubuntu's ext3 and linux-swap reside) and an 80GB one.

Running the Live CD (as well as Gnoppix) earlier, I could access hdb. But after installation I couldn't and not in the media folder.

Here's the diagnostic skinny on it:

```
Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2346    18844213+  83  Linux
/dev/hda2            2347        2434      706860    5  Extended
/dev/hda5            2347        2434      706828+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    b  W95 FAT32
```

fstab says:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by taurus on 2007-01-06
And I suppose you would like to know how to add /dev/hdb1 to your /etc/fstab so it would be mounted each time you boot Ubuntu, eh!

Here we go...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll to the end and add this line to it.

```
/dev/hdb1   /media/hdb1   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Then create a mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by Hishgraphics on 2007-01-06
Taurus, whenever you're in the neighborhood of Kuala Lumpur, let me know. I owe you a drink.

---

### Post by taurus on 2007-01-06
> **Hishgraphics said:**
> Taurus, whenever you're in the neighborhood of Kuala Lumpur, let me know. I owe you a drink.

Will keep that in mind.  Thanks.  ;)

---

