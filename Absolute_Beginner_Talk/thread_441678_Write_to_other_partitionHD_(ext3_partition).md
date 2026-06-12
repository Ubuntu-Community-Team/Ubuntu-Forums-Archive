---
title: "Write to other partition/HD (ext3 partition)"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-05-12
Can anyone tell me how to write to a partition or second HD, i.e. create folders, etc.? I have done tons of searching, reading about permissions, etc., it is all so confusing to a new user.

Basically, I can't create a folder/i.e. write to my drives, any partitions...

I have tried running "sudo chown usewrname" , nautilus, & other stuff, buit nothing seems to work!

Help a newbie out, please?!?! :confused:

---

### Post by taurus on 2007-05-12
What filesystem is that partition and where do you mount it?

---

### Post by discmaster on 2007-05-12
As per some other instruction on here, I made all file systems ext3. (except the xp one) I have a partition set aside that I may install xp on later, but for now that one is empty.

---

### Post by taurus on 2007-05-12
Okay, where do you mount that partition, mount point and what is your login name.  You just need to change the ownership of that mount point from root to your login name and you can write to it anytime you want.

```
id
df -h
```

---

### Post by discmaster on 2007-05-12
> Okay, where do you mount that partition, mount point and what is your login name. ok, be gentle here! This is where it is getting confusing for me, right from the start...I am a 9 yr. veteran of windows, & a 1 1/2 week newbie on linux!

I can barely use the terminal, so all the relative searches & code, etc. that I find on here is "all greek to me", as they say.

I don't understand exactly what you mean, in the quote...It is mounted on the desktop, & also in computer...sorry that is about as much as I know. I am willing to learn, but I seem to get bogged down in endless tutorials, threads, etc. that go many different directions, & I can't seem to find anything like a "basic starter guide"...

---

### Post by taurus on 2007-05-12
Let's assuming that partition is mounted to /media/storage with ext3 filesystem and you can't write to it because root is the owner of it.  You want to write to it but don't want to become root all the time.  Therefore, you need to change the owernship of /media/storage from root to your login name.  

That's why I need to know what is the name of that mount point and your login name so I can show you how to change the permissions without trashing your machine.

```
id
df -h
```

---

### Post by discmaster on 2007-05-12
ok, this is what I have...> tr@tr-desktop:~$ sudo chown tr /media/sda6
Password:
tr@tr-desktop:~$ sudo chgrp tr /media/sda6
tr@tr-desktop:~$ 
tr@tr-desktop:~$ id
uid=1000(tr) gid=1000(tr) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(tr)
tr@tr-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              19G  2.0G   16G  12% /
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  108K  506M   1% /proc/bus/usb
udev                  506M  108K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda3              15G  185M   14G   2% /home
/dev/sda1              28G  173M   26G   1% /media/sda1
/dev/sda6             167G  188M  159G   1% /media/sda6
tr@tr-desktop:~$ 


Note that all my partitions are not showing up there? This is what I have;

> sda1 ext media/disk (primary)
sda2 ext3 media/disk-1 (primary)
sda3 ext3 media/disk-2 (primary) (this will be home partition)
sda4 extended
sda5 linux-swap
sda6 ext3 (data partition)

(swap & data are in the extended partition)

---

### Post by taurus on 2007-05-12
```
sudo chown -R tr:tr /media/sda6
ls -la /media
```

---

### Post by discmaster on 2007-05-12
I did that - got this -
> tr@tr-desktop:~$ sudo chown -R tr:tr /media/sda6
tr@tr-desktop:~$ ls -la /media
total 28
drwxr-xr-x  7 root root 4096 2007-04-15 07:56 .
drwxr-xr-x 21 root root 4096 2007-05-11 22:04 ..
lrwxrwxrwx  1 root root    6 2007-05-11 21:51 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-05-11 21:51 cdrom0
drwxr-xr-x  2 root root 4096 2007-05-11 21:51 cdrom1
lrwxrwxrwx  1 root root    7 2007-05-11 21:51 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-05-11 21:51 floppy0
--wxr-x---  1 root root    0 2007-04-15 07:56 .hal-mtab-lock
drwxr-xr-x  3 root root 4096 2007-05-11 21:50 sda1
drwxr-xr-x  3 tr   tr   4096 2007-05-11 21:39 sda6
tr@tr-desktop:~$ 


Still do not have access...

---

### Post by taurus on 2007-05-12
What do you mean you still don't have access?  If you look at the output from the second command, you would see that you are the owner of /media/sda6 now.

```
drwxr-xr-x 3 **[COLOR="Red"]tr[/COLOR]** **[COLOR="Red"]tr[/COLOR]** 4096 2007-05-11 21:39 sda6
```

```
ls -la /media/sda6
```

---

### Post by discmaster on 2007-05-12
I cannot change any permissions, make a folder, etc.

---

### Post by discmaster on 2007-05-12
Update - Well, I finally figured it out - don't ask me how?

But, what about this?
> sda1 ext3 media/disk (primary)
sda2 ext3 media/disk-1 (primary)
sda3 ext3 media/disk-2 (primary) (this will be home partition)
sda4 extended
sda5 linux-swap
sda6 ext3 (data partition)

(swap & data are in the extended partition)

Why does only sda1 & 6 show up either on the desktop or in computer? Can I have them all show up?

---

