---
title: "Access to 2nd drive??? Where ja go?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by pgirard on 2007-03-12
Dell 4600
Edubuntu/Edgy 6.1 on c drive
Million family photos on storage drive Maxtor 6Y160PO???

The drive has been in this machine for @ 2 years. In there during install of Edgy 6.1 also.

I'm not sure how to get Linux to see it.
I attached a ss of admin>devises

Any suggestions for a major newb?

---

### Post by taurus on 2007-03-12
Did you mount it?  What are the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by pgirard on 2007-03-12
Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1797    14434371   83  Linux
/dev/hda2            3424        3649     1815345    5  Extended
/dev/hda3   *        1798        3423    13060845   83  Linux
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris
/dev/hda6            3424        3497      594342   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19929   160079661    7  HPFS/NTFS
girard@girard-desktop:~$

---

### Post by taurus on 2007-03-12
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Now, create a new mount point for it and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by pgirard on 2007-03-12
I'm not clear on what to do.
I can:
copy and paste the code
press enter
then look for something familiar
copy paste...

But which to copy and paste?

TIA!!!

---

### Post by taurus on 2007-03-12
Open a terminal and paste this code in.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Then, continue with the instructions from above.

---

### Post by pgirard on 2007-03-12
Hold on...I think I have it...I going to restart.

---

### Post by pgirard on 2007-03-12
Here is what I have now:

girard@girard-desktop:~$ gksudo gedit /etc/fstab /dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
(gedit:4752): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
girard@girard-desktop:~$ sudo mkdir /media/hdb1
mkdir: cannot create directory `/media/hdb1': File exists
girard@girard-desktop:~$ sudo mount -a
girard@girard-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              13G  2.4G  9.3G  21% /
varrun                252M   84K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   7% /lib/modules/2.6.17-11-generic/volatile
girard@girard-desktop:~$

---

### Post by taurus on 2007-03-12
Oh dear...

You suppose to edit /etc/fstab like this from a terminal.

```
gksudo gedit /etc/fstab
```
Then, use the down arrow key to scroll to the end of that file and _add_ this line to it.

```
/dev/hdb1 /media/hdb1 ntfs nls=utf8,umask=0222 0 0
```
Now, save it.  That would put you back to the prompt again.  Then, run

```
sudo mount -a
df -h
```

---

### Post by pgirard on 2007-03-12
Here is what I get if I do not put a space between the first 2 lines of code:

---

### Post by taurus on 2007-03-12
The command to type from a terminal to edit /etc/fstab is

```
**[COLOR="Red"]gksudo gedit /etc/fstab[/COLOR]**
```

---

### Post by pgirard on 2007-03-12
Here is what I get before I save.

---

### Post by pgirard on 2007-03-12
Here is what I get after the save.

---

### Post by pgirard on 2007-03-12
Any more hints?

---

