---
title: "problem wit mounting an image!"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by TR13 on 2007-09-16
i have a n .iso file. i tried mounting it using (sudo mount -o loop Ubuntu_7.04_i386.iso /media/iso/) but is does not work it gives an error  " No such file or directory"..i saved the image in /media/iso.... help!!

---

### Post by HermanAB on 2007-09-16
I think it refers to the mount point not existing.

I usually mount ISOs to /mnt/iso, so try something like this:
$ sudo -i
# mkdir /mnt/iso
# mount -t iso9660 /where/ever/it/is.iso /mnt/iso
# ls /mnt/iso

Unmount it with:
# umount /mnt/iso

Cheers,

H.

---

### Post by TR13 on 2007-09-16
hi got this error

mount -t iso9660 /media/iso/Ubuntu_7.04_i386.iso /mnt/iso
mount: /media/iso/Ubuntu_7.04_i386.iso is not a block device (maybe try `-o loop'?)

---

### Post by TR13 on 2007-09-16
hi got it working.... thanks... i used the *-o loop* part...

---

### Post by akba0012 on 2007-09-17
> **HermanAB said:**
> I think it refers to the mount point not existing.

I usually mount ISOs to /mnt/iso, so try something like this:
$ sudo -i
# mkdir /mnt/iso
# mount -t iso9660 /where/ever/it/is.iso /mnt/iso
# ls /mnt/iso

Unmount it with:
# umount /mnt/iso

Cheers,

H.

How do i do this with .daa?

---

### Post by digen on 2007-09-18
I know that you can convert the .daa image file to an ISO file and then mount it using the same instructions mentioned earlier in this thread. 

To extract the .daa image you can use Poweriso which is a command line utility. 

poweriso convert filename.daa -o filename.iso -ot iso

---

