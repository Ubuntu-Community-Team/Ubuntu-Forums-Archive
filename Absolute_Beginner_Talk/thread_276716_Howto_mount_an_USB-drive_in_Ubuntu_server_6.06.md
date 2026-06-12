---
title: "Howto mount an USB-drive in Ubuntu server 6.06?"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Wesslan on 2006-10-13
I have an 250Gb USB-HD mounted on my old Mandrake(ouch) Linux-box and now I want to mount it on my Ubuntu(yeah!) Server 6.06.
It's formatted with EXT2(from fstab on Mandrake-box: "/dev/sda5 /files ext2 defaults 1 2") because I don't want to move the disk around, it will "always" be connected to my Ubuntu-box because it serves as a file server.

Does anyone know how I should do to mount this drive?
I guess that automount isn't there for me when I run a server?

Tia,
Peter

---

### Post by Wesslan on 2006-10-13
As usual, after several hours of trying, you make it yuorself just after posting a question. :D 

For the afterworld, this is how I did it:
1) Connected the USB-drive.
2) Rebooted the machine.
3) Executed > dmesg |grep -i usb and saw > scsi5 : SCSI emulation for USB Mass Storage devices.
4) Created a dir(/files2) to mount my drive on.
5) Mounted scsi5 from the [Webmin]("http://www.webmin.com/") GUI.
6) Webmin put the follwing line in /etc/fstab:
> /dev/sdc5  /files2  ext2  suid,dev,exec  0  0

Wesslan

---

### Post by ff2k on 2006-11-03
Would be possible to not reboot the system? I've been stuck with this as well. ](*,)

---

