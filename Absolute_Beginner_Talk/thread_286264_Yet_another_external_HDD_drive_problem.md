---
title: "Yet another external HDD drive problem"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Alveric on 2006-10-27
OK, so I have this Lacie external HDD (80 GB, USB2) which I had formatted in NTFS from Windows days...

I wanted to copy my documents and music onto it as a low-key backup, so got gparted using synaptic, and formatted it to ext3.

Except, I couldn't write to it! I unmounted it and checked the permissions from Computer in nautilus and I didn't have write permissions. I couldn't change the permissions - got error message about not being able to do so.

Did some googling and used gksudo nautilus to go in and change permissions.

Still couldn't write to it.](*,) 

Went back into gparted and re-reformatted it, may have accidentally moved the path...:-?  Now, can't see it even in Computer.

Any helpful suggestions or should I just use it as a paperweight?

Thanks in advance.

---

### Post by John.Michael.Kane on 2006-10-27
Have look over this [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by ReaderRat on 2006-10-27
One of these may help....or not...depending on what you decide to do...
     [**Mounting Windoze Partition**](http://www.psychocats.net/ubuntu/mountwindows)
    OR   [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by bodhi.zazen on 2006-10-27
> **Alveric said:**
> Any helpful suggestions or should I just use it as a paperweight?

Thanks in advance.

No, send it to me :)

To use the drive the way you like I think you need an entry in fstab.

Unplug the USB cable and the re-connect.

Fire up GParted and re-format as ext3. Note the partition (/dev/sda1 ? )

Now:
```
sudo mkdir /mnt/usb
mount /dev/sda1 /mnt/usb ext3 -o uid=1000,gid=100,umask=000
```

If that work, unmount the device and add this to fstab:> /dev/sda1 /mnt/usb ext3 users,uid=1000,gid=100,umask=000 0 0

_Note_: To edit fstab:```
sudo gedit /etc/fstab
```

re-mount the device:```
mount /mnt/usb
```

should be good to go....

See also: [How to fstab](http://ubuntuforums.org/showthread.php?t=283131)

8)

---

### Post by bodycoach2 on 2006-10-27
I've got my NTFS external harddrive to read/write. Not exactly sure what/how I it worked, but here's what I did:

When into Synaptic, did a search on NTFS, and loaded up anything that had to do with NTFS. After restarting the system (not sure if I really need to), I could read/write my drive.

Anyone have any idea how I made it work?

---

### Post by bodhi.zazen on 2006-10-27
[ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Alveric on 2006-10-30
> **bodhi.zazen said:**
> No, send it to me :)

To use the drive the way you like I think you need an entry in fstab.

U

should be good to go....

8)

Just wanted to say thanks; with your help, and a guy on my LUG mailing list I need to go out and buy a new paperweight.

Its embarrassing - I'm a pretty experienced user of Gates's OS, and recently moved over to Ubuntu thinking, "This isn't so hard" and then manage to utterly mess up a simple task like formatting an external HDD.

If anyone would like to add "RTFM" then please feel free...:-D 

Cheers.

---

