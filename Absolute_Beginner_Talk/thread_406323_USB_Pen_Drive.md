---
title: "USB Pen Drive"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by indie56 on 2007-04-10
Hello
Due to some reason I have managed to lock my Pen drive. I understand that I have to change permissions to unlock the USB and the files in it. I do not know the cd commands to navigate to the USB and thereafter to unlock the USB and the files.
Pl Help 
Thanks

---

### Post by devnulljp on 2007-04-11
Not sure what you mean by lock...physically? Or just mounted read only? 
Either way try this  after you insert the drive:

dmesg  | grep 'SCSI device'

That should tell you the device:

Now, you want to mount it read-write:

sudo mount -t vfat -o rw /dev/sda1 /some/mount/point 

now cd /some/mount/point and you should be able to read and write anythingin there, at least as root (sudo some_commands)

---

### Post by indie56 on 2007-04-11
Hello
I mean the USB drive is read only. I cannot write or delete from it.
I ran the command 
dmesg | grep 'SCSI device'

Message received

[12173.415871] SCSI device sda: 499712 512-byte hdwr sectors (256 MB)
[12173.434883] SCSI device sda: 499712 512-byte hdwr sectors (256 MB)

Next I ran the command
 sudo mount -t vfat -o rw /dev/sda1 /some/mount/point

Message recived

mount: mount point /some/mount/point does not exist
Pl help out

---

### Post by darkrose on 2007-04-11
replace /some/mount/point with where you want it mounted like /media/usb0 or something.

---

### Post by devnulljp on 2007-04-14
/some/mount/point is supposed to be just some mount point -- i.e. somewhere you want to mount it...it could be /media/myusbdrive or something, up to you.

---

### Post by indie56 on 2007-04-15
I used the first command
dmesg | grep 'SCSI device'

I got
[ 2402.014044] SCSI device sda: 499712 512-byte hdwr sectors (256 MB)
[ 2402.056954] SCSI device sda: 499712 512-byte hdwr sectors (256 MB)

My USB is mounted at -desktop:/media$ 
So I ran 
 sudo mount -t vfat -o rw /dev/sda /media/usbdisk   
to get
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Then I ran  sudo mount -t vfat -o rw /dev/sda 1/media/usbdisk

to get
mount: /dev/sda1 already mounted or /media/usbdisk busy
mount: according to mtab, /dev/sda1 is already mounted on /media/usbdisk


My knowledge of line commands is zero.
Thanks

---

