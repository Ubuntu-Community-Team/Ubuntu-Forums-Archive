---
title: "Unable to mount removable hard disk"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by nickgriffiths on 2007-03-18
Hello all,

I have a 300GB Seagate USB hard disk and a 2GB Samsung YP-U2 both formatted as FAT32 that I'm trying to mount using Nautilus. When I plug either of these in and open Places -> Computer I can see an icon for the device. However, when I double click on it I get an error message that says:

[B]"Unable to mount the selected volume.
error: could not open fstab-type file: permission denied"[/B]

I have opened Users and Groups and ensured the "Access external storage devices automatically" box is checked. I also looked in /etc/group to check my username is in the "plugdev" group.

I am able to mount either device manually by typing "sudo mount /dev/sda1 /media/usbhd" into a terminal, but this only gives me read access. However, this is most inconvenient and I would like them to be mounted automatically, as is the case on my Ubuntu laptop (running Dapper Drake).

I have tried searching Google, these forums and Launchpad with my error message but found nothing relevant.

Can anyone think of a likely cause to this problem?

---

### Post by meborc on 2007-03-18
you could try to add a line like this ```
/dev/sda1    /media/usbhd vfat  iocharset=utf8,umask=000  0    0
```to your /etc/fstab file... but be sure you have created a dir for it to mout to first like so ```
sudo mkdir /media/usbhd
```
and then try```
sudo mount -a
```

...now this is a setup so it will mount on every bootup... so you will need to have the drive connected before... if you connect the drive while running ubuntu you will need to do "sudo mount -a" to mount it

EDIT: to mount it manually WITHOUT changing the etc/fstab file and still have the read/write permissions, you can use the line```
sudo mount /dev/sda1 /media/usbhd/ -t vfat -o iocharset=utf8,umask=000
```but be sure to create the directory first :)

---

### Post by nickgriffiths on 2007-03-18
> **meborc said:**
> ...now this is a setup so it will mount on every bootup... so you will need to have the drive connected before... if you connect the drive while running ubuntu you will need to do "sudo mount -a" to mount it

Thanks for your reply.

I may try that as a last resort, but surely there must be a solution that doesn't require editing fstab? I would like to be able to plug and unplug my devices at will, without having to resort to mounting/unmounting them manually.

Does anyone know precisely why I am getting the error message that I am, or what it means? I would prefer not to download the source code to try and work it out, as my knowledge of C is not good.

Incidentally, I have since discovered I am unable to mount my DVD drives as well - same error message.

---

### Post by meborc on 2007-03-18
well... you can try my second advice... so you don't have to change your fstab... 

i'm only guessing, but the error you get while mounting dvd's might come from the fact that you can't write to them?... i encountered similar problems in dapper... but i can't confirm it now

a also don't know for sure, but it would probably be best for you to upgrade your system at least to edgy... newer system - better hardware support... i don't have any usbhd's to try to reproduce your problem in edgy or in feisty though :(

do "sudo mkdir /media/usbhd" if you have not yet... and then "sudo mount /dev/sda1 /media/usbhd/ -t vfat -o iocharset=utf8,umask=000"... do you still get the same error?

---

### Post by nickgriffiths on 2007-03-18
> **meborc said:**
> i'm only guessing, but the error you get while mounting dvd's might come from the fact that you can't write to them?... i encountered similar problems in dapper... but i can't confirm it now

One of the drives is a DVD writer, but I am only trying to read files from a CD in the drive. However, I can't even mount it.

> a also don't know for sure, but it would probably be best for you to upgrade your system at least to edgy... newer system - better hardware support... i don't have any usbhd's to try to reproduce your problem in edgy or in feisty though :(

Sorry, I should have mentioned I am currently experiencing these problems on my desktop, which runs Edgy. My laptop runs Dapper (haven't used it in a while), but I am not having problems on that.

> do "sudo mkdir /media/usbhd" if you have not yet... and then "sudo mount /dev/sda1 /media/usbhd/ -t vfat -o iocharset=utf8,umask=000"... do you still get the same error?

No, I don't get an error message after doing that. Thanks for the workaround.

---

### Post by david_kt on 2007-03-18
On and off I have this problem, I guess might be due to ntfs-3g. What I did was uninstall both ntsf-3g and ntfs-config, and after that install both again. Just reinstall did not work, you should completely uninstall them first.

Regards,
DK

---

### Post by nickgriffiths on 2007-03-22
I have solved this issue.

I believe the problem occurred because I changed the permissions of /etc/fstab to rw------- because the file contained my samba credentials. I put these credentials in a separate file and changed fstab permissions back to rw-r--r--. I can now mount everything as normal.

I learned my lesson - don't change permissions unless I know what I'm doing ;)

---

