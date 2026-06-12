---
title: "Asking for help with my boot-repair"
date: 2021-12-12
forum: Apple Hardware Users
---

### Post by redfrog2000 on 2021-12-12
I have a mac mini where I am running Ubuntu for probably a year or so. I upgraded my ram and after I started the machine I got the grub minimal Bash-like terminal thingy. So according to the interweb I launch a live ubuntu install boot-repair and got my URL. 

Here's my paste bin url: [https://paste.ubuntu.com/p/B5VQXcZjbB/](https://paste.ubuntu.com/p/B5VQXcZjbB/)

Thx

---

### Post by howefield on 2021-12-12
Moved to the "*Apple Hardware Users*" forum.

---

### Post by redfrog2000 on 2021-12-12
I just want to add that I'm not dual booting, I just want to boot directly into ubuntu. Thx.

---

### Post by oldfred on 2021-12-12
Do not know Mac.
Looks like install was to sdb drive, but ext4 partition not correctly shown.
Boot is via ESP on sda and ESP on sdb not used, which is common with Ubuntu's Ubiquity installer.

Gdisk also says sdb is a hybrid configuration. You may want to remove that, but I do not think that is related to ext4 partition not correctly shown.
[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
convert hybrid to protective MBR gdisk experts commands  p, x, n, p, w
[http://askubuntu.com/questions/650194/repair-windows-boot-loader-after-installing-ubuntu-on-macbook-pro](http://askubuntu.com/questions/650194/repair-windows-boot-loader-after-installing-ubuntu-on-macbook-pro)

You can see if testdisk sees partition or just reformat & reinstall.
If drive issue, you may want to also check SmartStatus. 

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks is Smart Data:
[https://askubuntu.com/questions/983619/s-m-a-r-t-data-no-longer-available-in-ubuntu-16-04-disks-application](https://askubuntu.com/questions/983619/s-m-a-r-t-data-no-longer-available-in-ubuntu-16-04-disks-application)

---

### Post by redfrog2000 on 2021-12-12
Looks like one my SSD drive is toasted. Self test is failing. We'll need to replace it and reinstall Ubuntu :( and all the software, but the data is not on that drive at least.

---

