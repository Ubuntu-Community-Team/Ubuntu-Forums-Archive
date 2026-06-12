---
title: "mount -t smbfs etc"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by SimzI on 2006-07-09
lo, I've mounted my servers mp3 collection on my laptop so I can use xmms to play the media files. however, the mount is not connected when I reboot and I have to do mount -t smbfs etc again.

Can anybody tell me how to make it a permanent mount?

Thanks.

---

### Post by christhemonkey on 2006-07-09
```
gksudo gedit /etc/fstab
```
Then add this line:
```
//ip.add.re.ss/mp3s    /home/public smbfs dmask=777,fmask=777  0    0 
```

Then type:
```
sudo mount -a 
```
To remount everything without rebooting.

---

