---
title: "cannot change  permissions"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Ecthelion on 2006-04-17
Hi
I have a second hard disk mounted and i can't change the permissions of it.
I have tried to change owner/permissions/... with (sudo) nautilus, and as it didn't worked i have tried with 
sudo chown ecthelion /media/hdb1/
and even with
sudo chmod -R ecthelion /media/hdb1/
but   there's every time an error saying it's not allowed

is there another way to change permission so i can write on that harddisk....
Otherwise it's rather useless... :-|

---

### Post by christhemonkey on 2006-04-17
Open your fstab
```
sudo gedit /etc/fstab
```
look for a line about hdb1, if it says ro change it to rw.
Also what filesystem is it?
If its ntfs, then you cannot safely write to it from ubuntu.

---

### Post by Ecthelion on 2006-04-17
No it's a FAT32, so i can use it in both linux and windows
Thank you!

---

### Post by Ecthelion on 2006-04-17
uh-oh, 
the line about the harddisk says

/dev/hdb1       /media/hdb1     vfat    defaults        0       0

no ro or anything...
What do i do now?

---

### Post by christhemonkey on 2006-04-17
If its a FAT32 partition the line in your fstab should be:
```
/dev/hdb1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
```
Then type
```
sudo mount -a
```
If it complains about /media/windows not existing, make it:
```
sudo mkdir /media/windows
```

---

### Post by Ecthelion on 2006-04-17
hmmm i don't seem very bright...
i did what u said,
and then i tried again to change permissions with
```

sudo chmod -R 766 /media/hdb1/

```

but that wasn't a good idea because now everything on the harddisk is kinda weird...
unknown type 
and
application/octet-stream
as MIME-type, whatever that is
anyway it doesn't recognise directories or anything anymore....

is there any way to undo my (rather big) mistake?

---

### Post by christhemonkey on 2006-04-17
did it display that stuff before you typed that command in as well?
Have a feeling that in your fstab you need a new lil bit as well
```
/dev/hdb1   /media/windows   vfat   user,fmask=0111,dmask=0000   0   0
```

---

### Post by Iowan on 2006-04-17
'Xcuse my being a li'l dense, but FAT32 and permissions?

---

### Post by aysiu on 2006-04-17
christhemonkey's suggestion in post #4 was all you needed.

There is no *chmod*ing or *chown*ing of FAT partitions.

---

### Post by christhemonkey on 2006-04-17
I didnt make a suggestion in post no4?
:S

---

### Post by aysiu on 2006-04-17
[QUOTE=christhemonkey]I didnt make a suggestion in post no4?
:S[/QUOTE] Sorry--post #5.

---

### Post by Iowan on 2006-04-17
[QUOTE=aysiu]There is no *chmod*ing or *chown*ing of FAT partitions.[/QUOTE]Thanks - I'm not as confused (or dense) as I thought...

---

### Post by Ecthelion on 2006-04-18
> [QUOTE]Originally Posted by aysiu
There is no chmoding or chowning of FAT partitions.
[/QUOTE]

Of course you can chmod FAT32 partitions...
My problem seemed to be resolved by just rebooting my computer,and the permission are now set on modus 766 (or everyone has all permissions)

before i couldn't write on the disk without a nautilus with root permissions
```
sudo nautilus
```

Everyone tx for your help!

---

