---
title: "Desktop icon for mounted drive."
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by Porta on 2006-06-17
I've installed Dapper and when i mount a partition i don't get an icon on the desktop of the partition anymore.
In Breezy this worked fine, but after the upgrade on one of my computers it was gone.
Is there a solution to this little problem?

TIA
Porta

---

### Post by catlett on 2006-06-17
[QUOTE=Porta]I've installed Dapper and when i mount a partition i don't get an icon on the desktop of the partition anymore.
In Breezy this worked fine, but after the upgrade on one of my computers it was gone.
Is there a solution to this little problem?

TIA
Porta[/QUOTE]
What mount point are you using? Are you mounting manually every time or are you changing the /etc/fstab?

If your moint point is in the /media folder an icon willl always appear on the desktop. Did dapper make the mount points in the media folder or the mnt folder?

The long and short of it is a mount point in /media always creates a desktop icon. So make sure your mount points are in media first. This is the simple solution.

If that doesn't work you can create a deaktop launcher manually for the other partitions but first doubl;e ckeck your mount points.

P.S. Just to double check, "Have you been getting any errors during startup about mounting?)

---

### Post by adam.tropics on 2006-06-17
Applications-->System tools-->Configuration editor, then

apps-->nautilus-->desktop-->volumes visible

everything else for me was done by the installer..

---

### Post by Porta on 2006-06-17
The mount point is in the media folder and i haven't got any errors about mounting at startup.
This particular partition is always mounted manually.
I will try out what adam.tropics suggested.

---

### Post by adam.tropics on 2006-06-17
I should quickly mention (I forgot) that by default in Dapper, for some very strange reason, the configuraton editor is not shown by default in the menu. You can therefore either

Applications-->Accessories-->ALaCarte menu editor, and then choose to show the configuration editor, OR

Enter a command line

```
gconf-editor
```

---

### Post by Porta on 2006-06-17
I went to 'volumes visible' but you can't change anything there, at least what i can see.
You can't change the values for now, it will be possible in a later version, so it tells me.

---

### Post by adam.tropics on 2006-06-17
Sorry, my fault, I should have noticed you're on Breezy. It works on my Dapper box, and I made an assumption sorry.

That said, I just did a search of th old breezy threads, and they seemed to manage it. It should be a check box.

---

### Post by Porta on 2006-06-17
This is a Dapper-install i'm talking about, and there are no check-boxes present on that item.
I only see this; <schema>, under value and when clicked on i get the message 'sorry can't change this, it will be possible in a later version'

---

### Post by u.b.u.n.t.u on 2006-06-17
I make my own desktop link.

Right mouse click on the desktop.
Select "Create Launcher".
At "Type:" select "Link".
The path is similar to this:
```
/media/storage
```

*storage is the folder I mounted the HDD to.

Then I change the desktop icon to something else and cool.

---

### Post by adam.tropics on 2006-06-17
Well that's very odd. So now I'm guessing! I have only had one application lose the schema settings before, and running gconf-editor as sudo (just let it load have a look at what you're after and close it) then running as <user> sorted it for me. I can't find much else about your problem, and in your shoes woukd more than likely reinstall gconf-editor. Sorry I can't be of more help!

---

### Post by Porta on 2006-06-17
I was thinking about that too, reinstalling gconf-editor might help.
I can always, as suggested, make a desktop link.
Anyway thanks for the help.


regards
Porta

---

### Post by puterboy on 2007-11-18
I've got the same problem. No icon. Creating a new desktop icon is my next step, if someone can't tell me if i'm doing something wrong

fdisk:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24102410

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440088+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            7650       15298    61440592+  83  Linux
/dev/sda3           15299       15363      522112+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x538a9b62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       49965   401343831    7  HPFS/NTFS
/dev/sdb2           49966       60801    87040170    b  W95 FAT32


df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              58G  2.5G   53G   5% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  104K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              59G  6.8G   52G  12% /media/sda1
/dev/sdb1             383G   14G  370G   4% /media/sdb1
/dev/sdb2              83G   13G   71G  16% /media/sdb2


fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d5f990d3-e3a6-47b9-82e6-fff124964a32 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=CA30EDD230EDC593 /media/sda1     ntfs-3g    defaults,locale=en_US.utf8 0       0
# /dev/sdb1
UUID=8C98CD7D98CD65F4 /media/sdb1     ntfs-3g    defaults,locale=en_US.utf8 0       0
# /dev/sda3
UUID=95ee5306-3b56-45bb-b18c-b9e6edd11951 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/sdb2       /media/sdb2     vfat iocharset=utf8,umask=000 0 0


From what i've read, this is all right. Using gutsy x86. I wanna figure out how to do everything right, with no shortcuts. learn the stuff behind it. i will use the shortcut if there's no solution, i just wanna learn as much as possible

---

### Post by puterboy on 2007-11-18
never mind. had to restart ubuntu, not just x server.

---

