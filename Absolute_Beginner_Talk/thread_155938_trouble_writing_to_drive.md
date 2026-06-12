---
title: "trouble writing to drive"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by yellow beard on 2006-04-06
ive got a fat32 share partition set upbetween windows called osshare. i can only write to it as root which is annoying. this is what it looks like in fstab:

/dev/sdb6       /osshare        vfat    rw,user        0       0

what should i have in there so i can use it when im not root. ive tried chmod but that doesnt work.

---

### Post by aysiu on 2006-04-06
You can't *chmod* a Windows partition.

Open a terminal and type ```
sudo umount /dev/sdb6
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
Replace ```
/dev/sdb6 /osshare vfat rw,user 0 0
``` with ```
/dev/sdb6 /osshare vfat iocharset=utf8,umask=000 0 0
``` Save (control-x), confirm (y), and exit (Enter). ```
sudo mount -a
``` If *sudo mount -a* doesn't work, reboot.

---

### Post by nanotube on 2006-04-06
even better (imho), is to replace that line with
```
/dev/sdb6 /osshare vfat iocharset=utf8,uid=1000,umask=0077 0 0
```
(replace 1000 with your uid - find your uid with command "id")

this may be better because unlike the previous suggestion, this will give full access only to your username, rather than to everyone who may be using the computer. if that partition stores your personal files, this is more proper.

---

### Post by yellow beard on 2006-04-06
Thanks, ill keep *user* in there cause i like to see it under places.

---

### Post by aysiu on 2006-04-06
[QUOTE=yellow beard]Thanks, ill keep *user* in there cause i like to see it under places.[/QUOTE] According to [this page](http://www.tuxfiles.org/linuxhelp/fstab.html), > **user and nouser** These are very useful options. The user option allows normal users to mount the device, whereas nouser lets only the root to mount the device. nouser is the default, which is a major cause of headache for new Linux users. If you're not able to mount your cdrom, floppy, Windows partition, or something else as a normal user, add the user option into /etc/fstab. So I don't really see what that has to do with the partition being visible under "Places."

If it's in your /etc/fstab, it's kind of a non-issue, since it'll automount at bootup. The user doesn't have to intervene at all.

---

### Post by Sutekh on 2006-04-06
[quote=yellow beard]
Thanks, ill keep user in there cause i like to see it under places.[/quote]
Do you mean in the 'Places' menu or the 'Places' sidebar in Nautilus (the browser)?

If you want it under the 'Places' menu add it as a bookmark using Nautilus.

If you want it in the 'Places' sidebar you can add it as a bookmark *or* mount the partition in a folder under /media.   Since you went to the trouble of mounting it in /osshare, just add it as a bookmark.

Open Nautilus and browse to the partition and then press Ctrl+D to add it to the bookmarks (or use the Bookmarks menu).  You can edit the bookmarks using Ctrl+B, so you can change the display name.

---

### Post by dvarsam on 2006-04-06
[QUOTE=nanotube]even better (imho), is to replace that line with
```
/dev/sdb6 /osshare vfat iocharset=utf8,uid=1000,umask=0077 0 0
```
(replace 1000 with your uid - find your uid with command "id")

this may be better because unlike the previous suggestion, this will give full access only to your username, rather than to everyone who may be using the computer. if that partition stores your personal files, this is more proper.[/QUOTE]

It would be great if instead of using:

> uid=1000

Some one could use:

> uid=username

where "username" is YOUR username (e.g. Mine is "dimitris").

Something like DNS...

Instead of typing "185.32.46.231" (e.g. a Number), to access [www.yahoo.com](www.yahoo.com)
...

you type "www.yahoo.com" to access their page...

That would be cool...

Besides: who remembers numbers?

---

