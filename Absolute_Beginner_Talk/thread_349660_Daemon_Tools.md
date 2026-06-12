---
title: "Daemon Tools"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-01-30
Hi,

Does anyone know what the Linux equivalent of Daemon Tools is.  Basically, I am after a CD/DVD ROM emulator to mount an iso file for VMware.

Thanks.

---

### Post by taurus on 2007-01-30
```
sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop **filename.iso** /mnt/iso
```

---

### Post by dannyboy79 on 2007-01-30
not sure how to mount an iso with Vmware but I know you can simply mount an iso in linux by simply using this code:
mount myiso.iso /mnt/iso/ -t iso9660 -o ro,loop=/dev/loop0
where you need to create a folder called iso within the /mnt dir and the name of your iso is myiso.iso. good luck.

---

### Post by fakie_flip on 2007-02-17
that doesnt work with any jas versions for vmware to use. using the iso emulation built in vmware server does not work either because it cant understand the osx filesystem. thats why all guides say to use daemon tools in windows instead, but i havent found a way to do it in linux.

---

### Post by Jussi01 on 2007-02-17
gISOmount

---

### Post by fakie_flip on 2007-02-17
> **Jussi01 said:**
> gISOmount

I used gISOmount to mount the iso. The mount command shows that it is mounted.

/home/chris/SHARE/osx.iso on /media/Mac OS X Install Disc x86(vcd) type iso9660 (ro,loop=/dev/loop0)

In the vmware settings, I can choose which cd/dvd device to use such as /dev/hda /dev/cdrom etc. I put in this.
/media/Mac OS X Install Disc x86(vcd)

When I power on the virtual machine, I get the error in the picture.

---

