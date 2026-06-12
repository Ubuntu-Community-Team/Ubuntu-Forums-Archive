---
title: "Hard Drive mounting &quot;Permissions&quot;"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by Vega on 2005-10-31
well my problem is my two hard drive mounts. I can read and execute but I can't write and it tells me that I do not have permission to alter permissions! lol

Any suggestions would be helpful!^^

---

### Post by aysiu on 2005-10-31
Are they Windows partitions/hard drives? If so, this may help:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by Vega on 2005-10-31
[QUOTE=aysiu]Are they Windows partitions/hard drives? If so, this may help:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)[/QUOTE]

well they are both NTFS. One of them hda1 is my dual boot with Windows. and my other hdb1 is my storage for "stash" which is formatted NTFS.

---

### Post by aysiu on 2005-10-31
```
sudo fdisk -l
```

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by Vega on 2005-10-31
[QUOTE=aysiu]```
sudo fdisk -l
```

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)[/QUOTE]


I've done the automount commands. Nothing has changed...

When I rebooted. the following verbose message in startup said 

"mounting local file systems"                      failed

---

### Post by Mustard on 2005-11-01
Paste your fstab contents in here....

```
gedit /etc/fstab
```

---

### Post by aysiu on 2005-11-01
And the result of ```
sudo fdisk -l
```

---

### Post by xmastree on 2005-11-01
[QUOTE=Vega]I can read and execute but I can't write[/QUOTE]
> well they are both NTFS. One of them hda1 is my dual boot with Windows. and my other hdb1 is my storage for "stash" which is formatted NTFS.Linux can't write to ntfs, so read and execute is the best you'll get. If you want to share data fully, I suggest you reformat hdb1 as FAT32.

I'm surprised you missed that one, aysiu... :rolleyes:

---

### Post by Vega on 2005-11-01
I see well thanks for your help!

---

### Post by aysiu on 2005-11-01
[QUOTE=xmastree]Linux can't write to ntfs, so read and execute is the best you'll get. If you want to share data fully, I suggest you reformat hdb1 as FAT32.

I'm surprised you missed that one, aysiu... :rolleyes:[/QUOTE] I'm tired. Thanks for catching that one.

---

