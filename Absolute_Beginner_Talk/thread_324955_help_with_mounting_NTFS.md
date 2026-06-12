---
title: "help with mounting NTFS"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-12-24
I am trying to help a friend recover data on his HD as windows crashed on him and he can not boot into it anymore. I took  Gparted and dapper livecds.
booted from Gparted, all the partition tables are intact and I was able to mount his ntfs drive on a tmp folder so we can check his files were there.. sucess.
Booted from a dapper livecd, to my surprise, the ntfs was not mounted automatically.Here is what I then tried..
```
cd /media
sudo mkdir windows
sudo mount /dev/hda2 /media/windows
```
It seemed as though it was successfully mounted, but when I try to cd into that dir, I get permissions problem. I can not get into it graphically either, tried sudo chmod 777 on the mount point and get an error that it was a read-only dir
What can I do to mount to NTFS properly so we can burn his files onto a cd from Dapper and continue with installing linux on his corrupted partition??

I know this might be rather simple.. and thus hoping from quick responses.. thanks~

---

### Post by taurus on 2006-12-24
```
sudo umount /dev/hda2
sudo mount -t ntfs /dev/hda2 /media/windows -o nls=utf8,umask=0222
ls -la /media/windows
```

---

### Post by mike3k on 2006-12-24
Install the ntfs-3g package and use ntfs-mount. It supports write access a lot better than standard mount for NTFS volumes.

---

### Post by habtish on 2006-12-24
> **taurus said:**
> ```
sudo umount /dev/hda2
sudo mount -t ntfs /dev/hda2 /media/windows -o nls=utf8,umask=0222
ls -la /media/windows
```

That worked, thanks taurus..any app from the ones out there you would recommend to fix MBR?

mike3k, thanks for your reply, but as I had said.. I am running this from a Livecd and didn't need RW acess..
Cheers

---

### Post by Hankers on 2006-12-24
Boot from the XP disk and select the Recovery Console. Type fixmbr [device_name] [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true")

---

