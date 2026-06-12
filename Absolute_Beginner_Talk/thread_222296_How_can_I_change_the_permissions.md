---
title: "How can I change the permissions?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2006-07-24
Ok...so I just installed Ubuntu on my system, (dual boot with win xp pro) and it automatically mounted my 3 extra hard drives. But when I try to open those drives up to browse them, and access the files..etc..it tells me I do not have permission to access the files. When I look at the properties of the mounted drives, it claims the owner of these drives is Root, and only root can change the permissions. How do I do this? I want to be able to access these files...all Im asking for is how I go about changing the permissions on these drives allowing me to access them. Some one help!

---

### Post by JoWilly on 2006-07-24
In a shell (terminal) do "chown -R USERNAME directoryname"

"man chown" for the manual.

---

### Post by mssever on 2006-07-24
Edit your /etc/fstab:
```
gksudo gedit /etc/fstab
```

Find the lines that refer to your Windows partitions. They will contain a value in the third column that is either vfat or ntfs. Add ",umask=007" to the fourth column and save the file.

**Caution:** If you try to write to a NTFS partition, be warned that NTFS support is experimental and you could lose data. Reading s safe, though, as is writing to a vfat partition.

---

### Post by bladefallcon on 2006-07-24
ok..let me just make sure on this (im quite new to this) what i should do is:

chown -R blade hda1

is that right?

---

### Post by mssever on 2006-07-24
That will work if the disk is formatted using a Linux format. If it uses a Windows format, you can't use chown. See my post above.

---

### Post by bladefallcon on 2006-07-24
> **mssever said:**
> Edit your /etc/fstab:
```
gksudo gedit /etc/fstab
```

Find the lines that refer to your Windows partitions. They will contain a value in the third column that is either vfat or ntfs. Add ",umask=007" to the fourth column and save the file.

**Caution:** If you try to write to a NTFS partition, be warned that NTFS support is experimental and you could lose data. Reading s safe, though, as is writing to a vfat partition.

ok...tried this, and there was nothing there...so i tried to just navigate to the file, /etc/fstab, which i found, opened, and saw what you were talking about...tried to edit it, but when i tried to save it it tells me i dont have permission to edit it....so now what?

---

### Post by Jagot on 2006-07-24
Open it from Terminal like this:

```
sudo gedit /etc/fstab
```

Then you will be able to edit and save the file.

---

### Post by mssever on 2006-07-24
You have to do this with root privileges. Go to the Applications menu > Accessories > Terminal. There you'll be able to type in the command I gave you. I don't know of a way to open a file as root without using the terminal--but then, I don't use Nautilus (the file browser) enough to know.

---

### Post by Jagot on 2006-07-24
> **mssever said:**
> I don't know of a way to open a file as root without using the terminal

Hit alt+f2 and type 'gksudo nautilus'.  You will then be able to navigate through the directory tree editing any files you so desire.

---

### Post by bladefallcon on 2006-07-24
> **mssever said:**
> You have to do this with root privileges. Go to the Applications menu > Accessories > Terminal. There you'll be able to type in the command I gave you. I don't know of a way to open a file as root without using the terminal--but then, I don't use Nautilus (the file browser) enough to know.

ok...i got it to open...and save...but still cant access those drives...maybe im not understandiung what im supposed to do..(god i feel like such a noob with all this...) let me copy the line i edited...and you tell me if i did it right...


/dev/hda1       /media/hda1     ntfs    defaults,umask=007        0       0

thats what i did...added ",umask=007" to the fourth column...but still no access..HELP!

---

### Post by Jagot on 2006-07-24
[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html)

---

### Post by JoWilly on 2006-07-24
> **bladefallcon said:**
> ok...i got it to open...and save...but still cant access those drives...maybe im not understandiung what im supposed to do..(god i feel like such a noob with all this...) let me copy the line i edited...and you tell me if i did it right...


/dev/hda1       /media/hda1     ntfs    defaults,umask=007        0       0

thats what i did...added ",umask=007" to the fourth column...but still no access..HELP!

After the changes in /etc/fstab you need to remount the partition: "sudo mount /dev/hda1 -o remount"

---

### Post by bladefallcon on 2006-07-24
> **JoWilly said:**
> After the changes in /etc/fstab you need to remount the partition: "sudo mount /dev/hda1 -o remount"

AAAAAHHHH...still not working...i am sooo confused...

---

### Post by JoWilly on 2006-07-25
> **bladefallcon said:**
> AAAAAHHHH...still not working...i am sooo confused...

Did you try umask=000 ? Also try to unmount (sudo umount /dev/hda1) and then to mount it (sudo mount/dev/hda1).

(not sure if remount will take the new values in fstab)

---

### Post by bladefallcon on 2006-07-25
thanks...i finally got it to work...I just had to unmount the drives, and then remount them...which is what i had been trying to avoid...but it worked...so...oh well...

---

