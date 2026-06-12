---
title: "can't recognize cd drive"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by mokmoki on 2006-10-29
(1) i just installed an asus dvd writer, replacing my old asus cd writer. i placed it in the same cable of the old writer.

now my ubuntu can't detect my new drive, although ubuntu could detect my old cd writer before i changed it with a new one.

(2) also, another minor problem... aside from my dvd writer, i have a dvd drive (reader). now, ubuntu mounts the cd's i place in my dvd reader in /media/usbdisk...

why does it mount in usbdisk when its a cdrom? hmmm... and the /media/cdrom0 and /media/cdrom1 doesn't seem to contain anything...

(3) also in the GUI (Nautilus), the places side bar says "user, Desktop, File System, Floppy Drive, CD-ROM 1, External Drive, SHARED, and WinXP".. but when i choose CD-ROM1, it says "Unable to mount selected volume, mount: special device /dev/hdc does not exist"

-------------------

anybody can teach me how to change my mount settings? because when i first installed ubuntu, i remember changing the mount settings so that my windows xp drives can also be read...

any help would greatly be appreciated... :)

---

### Post by mokmoki on 2006-10-29
each time i post here at ubuntuforums, i never get any replies... tsk...

---

### Post by mokmoki on 2006-10-29
nice talking to you guys. really.

---

### Post by CatKiller on 2006-10-29
Crikey.

Anyway, mount points are defined in /etc/fstab. You may have the jumper set incorrectly on your new drive.

---

