---
title: "Drive suddenly became read only and cannot find answer anywhere please someone help"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by zms on 2008-04-07
The other day my external hard drive became a read only drive all of a sudden. I have been looking for days for a solution and nothing seems to be working I was wondering if someone could help me because i obviously have no idea whats going on. Thank you for your help I greatly appreciate it.

---

### Post by Dark Aspect on 2008-04-07
> **zms said:**
> The other day my external hard drive became a read only drive all of a sudden. I have been looking for days for a solution and nothing seems to be working I was wondering if someone could help me because i obviously have no idea whats going on. Thank you for your help I greatly appreciate it.

Try:

> sudo nautilus

Then,browse to the /media folder and find your external hard drive mount point.Then make sure your normal user has the correct permissions to access the drive.If that does not help then try to unmount the drive and mount the drive again.

Hope that helped.

---

### Post by Inxsible on 2008-04-07
you can also use the command line which is much safer than obtaining root privs on nautilus```
sudo chown -R <*your user name*>:<*your group*> <*path to mount point*>
``````
sudo chmod +rw <*path to mount point*>
```

---

### Post by zms on 2008-04-08
I tried them both and this is what i got...I think i wrote it correctly. but It did not work. The permission of the drive is given to the right user. I was wondering how I would mount it and unmount it in terminal. Again thankyou very much. 



zain@zain-desktop:~$ sudo chown - R zain:zain /media/WD Combo_
chown: `-': invalid user

zain@zain-desktop:~$ sudo chmod +rw /media/wd combo_
chmod: cannot access `/media/wd': No such file or directory
chmod: cannot access `combo_': No such file or directory

---

### Post by zms on 2008-04-08
I looked at the filing system and it is formated as vfat...I dont know if that makes a difference

---

### Post by Irihapeti on 2008-04-08
```
zain@zain-desktop:~$ sudo chown - R zain:zain /media/WD Combo_
```

The above command won't work as given. It should be:

```
zain@zain-desktop:~$ sudo chown -R zain:zain "/media/WD Combo_"
```

i.e no space between the - and the R, and quote marks in the pathname because it has a space in it.

---

### Post by zms on 2008-04-08
Thank you for the that but the files are still read only this is some of what is in terminal:

[SIZE="4"]chown: changing ownership of `/media/WD Combo_/.Trash-zain/Retrospect Backup/Backup of Drive C (C)/Documents and Settings/Zain/Local Settings/Application Data/Mozilla/Firefox/Profiles/kqwzd1i5.Default User/Cache/90013AC7d01': Read-only file system
chown: changing ownership of `/media/WD Combo_/.Trash-zain/Retrospect Backup/Backup of Drive C (C)/Documents and Settings/Zain/Local Settings/Application Data/Mozilla/Firefox/Profiles/kqwzd1i5.Default User/Cache/935BAC14d01': Read-only file system[/SIZE]

---

### Post by bilal.17 on 2008-04-08
i think you may have unmounted the disk improperly... i had a simillar problem once and the only solution i found was to save my files somewhere then format the disk then put the files back in place

---

### Post by ant2ne on 2008-04-08
What file system is the external drive. I've seen this happen with NTFS file systems and it requires some special tools installed. I forget which. NTFS-3g or something like that

---

### Post by dummyhead3 on 2008-04-08
> What file system is the external drive. I've seen this happen with NTFS file systems and it requires some special tools installed. I forget which. NTFS-3g or something like that

Dear friend, you should start reading posts, the drive has a vfat filesystem.

---

### Post by zms on 2008-04-08
I would like to aviod reformatting the drive because it has about 170 gb of media and other things on it.

---

### Post by ant2ne on 2008-04-09
> **dummyhead3 said:**
> Dear friend, you should start reading posts, the drive has a vfat filesystem.
'tis why I said "What file system is the external drive" I did scim through the post but missed that reference. So sorry.

---

