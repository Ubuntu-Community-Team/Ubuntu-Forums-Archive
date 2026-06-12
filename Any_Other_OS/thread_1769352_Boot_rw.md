---
title: "Boot rw"
date: 2011-05-27
forum: Any Other OS
---

### Post by cecilpierce on 2011-05-27
Running Natty,

System won't boot unless I change read only  (ro) to read write (rw)

linux /vmlinuz root=/dev/sda1 ro quiet splash
to
linux /vmlinuz root=/dev/sda1 rw quiet splash

I did fsck and it fixed a few inodes but it still crashes on boot with ro.

---

### Post by Rubi1200 on 2011-05-28
Hi,
why did you post here where your request for help is less likely to be seen?

A more appropriate forum would have been General Help or Installation & Upgrades.

That said, please do the following so we can get a better overview of the current state of your system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

