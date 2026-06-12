---
title: "copy /home patition"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-01-18
is it possible for me to copy my whole partition to my usb HD (ntfs) and then after i reinstall ubuntu copy the whoe thing back so still have my settings and stuff?

thanks in advance!

---

### Post by jeffus_il on 2008-01-18
It is not only possible, but it's easy.
try ```
man cp
```you need to use cp to copy, it must be recursive, must retain owners and permissions on files and folders, and probably verbose too so that you can see if it's working ...

---

### Post by b0rka7a on 2008-01-18
Yes of course :)
Use:
```
cp -R /home <path-to-the-ntfs-drive>
```

---

### Post by freebeer on 2008-01-18
as long as your new setup isn't too different from your old one, it shouldn't break anything.  If your /home is truly on a separate partition, you can probably re-install the OS without having to restore the /home partition.  Note that I said "restore".  You should still back it up just in case. ;)

---

### Post by rockinlinux on 2008-01-18
well i am trying to put vista back on here so i can use some programs and my wife can use it a little. i onyl have the recovery disks and they dont let me say a partition to install to. plus i already have 4 priamrys. so if i copy this like this how do i get it back on to the new /home parition? may plans are:

install vista
shirnk it with vista's disk managment tool
create a /root,/home and swap with gparted
install ubuntu again.

My linux will stil be the same version (7.10) and everything. I will make my paritions the same sizes and all. i was going to use partimage but i just think it is easier like this.

thanks and anymore help would be great! :)

have a good weekend too ;)

---

### Post by rockinlinux on 2008-01-19
anybody else? :)

---

### Post by RomeReactor on 2008-01-19
Hi. I think you can do all this graphically if you want: plug in your USB HD, open Nautilus in your home folder, press CTRL+H (to show all the hidden files) and then CTRL+A (to select everything) and CTRL+C (to copy). Then, still in Nautilus, navigate to your USB HD and press CTRL+V (to paste). Once you have vista and Ubuntu installed as you want, use this process starting from the USB HD, then navigate to your home folder.

---

### Post by Nythain on 2008-01-19
same install, same apps, its easy as pie... as mentioned, a simple copy over of the /home folder and then back after everything is said and done should do it

basically, like they all said, as long as the version of ubuntu you re-install is the same, and you end up installing basically the same apps it should all work out..

in fact, its common practice to keep /home on a seperate partition for this alone... that way, any reformats or wonky problems, users home's are still there and still the same

basically, either command line with cp -R or GUI with Nautilis or whatever gnomes filemanager is will do the trick, just copy that sucker over to the external and get goin mate :)

---

### Post by capink on 2008-01-19
copying files to ntfs drive will not preserve ownership and permissions. You can resotre back the ownership form the livecd by:

```
sudo chown -R username.username /path/to/mounted/home/username
```

But thers is no way to resotre permissions, and I think some files on home need the correct premissions for the corresponding program to work (e.g. .dmrc).

So if you are backing up to a ntfs (which has no unix ownership or premissions) it is better to use tar to preserve permisssions:

```
sudo tar cvpzf /path/to/ntfs/backup.tar.gz /path/to/home
```


and to restore from the tarball

```
sudo mount -t ext3 /home/partition/device/name /path/to/mounted/root/partition/home
```

N.B /path/to/mounted/root/partition/home must be empty

```
sudo tar xvpf /path/to/ntfs/backup.tar.gz --same-owner -C /path/to/mounted/root/partition
```


Or if you have a spare unix partition just use cp -a to copy.

---

### Post by rockinlinux on 2008-01-19
this /home is on its own parition, it sounds to me like all these are for if it were just a folder.

---

### Post by capink on 2008-01-19
I assumed it was on the same partition as root. You don't need to do anything of what I posted above.

It just a simple install from livecd for you:

1. The installer will give you an option to mount your partitions on whatever mount point you want. Make sure that the home partition mount point is /home

2. Make sure to uncheck the format partition box next to your home partition. Otherwise, the contents of your home partition will be deleted.

3. Choose a username similar to the one you have on your current system. You can change the password if you want as it not stored on the home partition.

---

### Post by rockinlinux on 2008-01-19
thanks for the help, i already siad in the post that i have to wipe my whole drive to install vista and THEN need to restore my /home partition after i reinstall ubuntu. The /home, /root and swap and to be gone for my to install vista from my recovery disks.

and FYI you cant change your user name if you do what you told me to do.

thanks, anyone else? :)

---

### Post by rockinlinux on 2008-01-19
if i just make an ext3 parition on my usb drive, gksudo nautilus and copy all the folders to the drive and then use gparted to erase all my ubuntu partitions (root and home and swap) and then install vista, then reinstall ubuntu with my seperate /home partition. Then go in with the live cd and mount the /home partition, delete it and copy all the files from the usb dirve will this work?

thanks :)

---

### Post by rockinlinux on 2008-01-20
anyone?

---

