---
title: "how to mount ntfs"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Ahmad_latif on 2006-07-15
hi all ,

        i would like to know that how can we mount ntfs in linux by modifing kernal ,but not by installing packages or any patches. What are the changes or adding required in linux kernal so that we mount ntfs. plz any one can answer......:-k

---

### Post by Ctrl+Alt+Del on 2006-07-15
mounting ntfs read-only is no big deal
sudo -s
modprobe ntfs (not sure if that is needed)
mkdir /media/windows
mount /dev/hda1 /media/windows (replace hda1 with the partition you need)

if you want it mounted upon boot edit your /etc/fstab and add a line like:
/dev/hda1       /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

---

