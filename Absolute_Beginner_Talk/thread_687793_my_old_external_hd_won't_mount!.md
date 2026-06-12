---
title: "my old external hd won't mount!"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by pinsmack on 2008-02-04
[IMG]http://img508.imageshack.us/img508/4690/screenshotvf0.png[/IMG]
how do i fix this?

---

### Post by Blutack on 2008-02-04
Erm...
Do you have windows installed or access to a windows box?  If yes, plug it in, wait for it to be recognised then safely remove it using the little green thing at the bottom right of the screen.

---

### Post by pinsmack on 2008-02-04
i had windows installed. but i installed this so i don't know if it's still there.

---

### Post by Blutack on 2008-02-04
Do you want to keep the data on it?
If yes, you probably need to find a windows box.  You can always install XP in virtualbox
[http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)
and then remove it afterwards.

If no, just install gparted and reformat it either as NTFS (if you want to use it with windows boxes ever) or ext3 if it's just for linux users.
> sudo aptitude install gparted

---

### Post by Charcoal1981 on 2008-02-04
Question: have you tried executing the instructions given in the error dialog in your screenshot??

The answers you are likely to get here are only going to be variations on the information given by the dialog. If you try the instructions given by the dialog and they don't work, then repost with more information (e.g. errors given when you run the mount command...)

---

### Post by pinsmack on 2008-02-04
ok so i downloaded.installed gparted. how do i use it?

---

### Post by pinsmack on 2008-02-04
oh and i tried the things on terminal and this is what it came up with 
"mehmet@mehmet-laptop:~$ mount -t ntfs-3g /dev/sdb1 /media/disk -o force
mount: only root can do that
mehmet@mehmet-laptop:~$ /dev/sdb1 /media/disk ntfs-3g defaults, force 0 0
bash: /dev/sdb1: Permission denied
mehmet@mehmet-laptop:~$ "

---

### Post by Blutack on 2008-02-04
THIS WILL REMOVE ALL DATA FROM THE EXTERNAL DRIVE.

Click Administration --> Partition Editor.
Then in the dropdown list at the top right choose your external drive (probably sdb).
Make sure it looks correct and you aren't repartitioning your internal drive (the external one should have one big NTFS partition).
Delete the NTFS partition, click on the grey block of empty space, click new, choose your type, hit Save/Commit/Write changes to disc (I can't remember exactly but it's something like that).

---

### Post by Blutack on 2008-02-04
The force mount command is
> 
sudo mount /dev/sdb1 /media/disk ntfs-3g defaults, force 0 0
You may also need to create the /media/disc folder first using
> 
sudo mkdir /media/disc


However, you will have to force mount from the command line every time and the permissions may be wrong.  It is not a decent solution unless you need to rescue some stuff first before formatting.

---

### Post by Charcoal1981 on 2008-02-04
> oh and i tried the things on terminal and this is what it came up with
"mehmet@mehmet-laptop:~$ mount -t ntfs-3g /dev/sdb1 /media/disk -o force
mount: only root can do that
mehmet@mehmet-laptop:~$ /dev/sdb1 /media/disk ntfs-3g defaults, force 0 0
bash: /dev/sdb1: Permission denied
mehmet@mehmet-laptop:~$ "

You need to run the mount command with sudo to give it root permissions (i.e. sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force)

The second command line you have tried is not meant to be entered on the command line, it is an extra line to add to your /etc/fstab file. The idea is you do one or the other, not both! I would suggest reading some of the intro material at [http://www.tldp.org](http://www.tldp.org)

---

### Post by pinsmack on 2008-02-04
thanks guys. i formatted it and now it hopefully works

---

