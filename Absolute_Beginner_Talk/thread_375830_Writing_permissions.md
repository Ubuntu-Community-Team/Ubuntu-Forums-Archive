---
title: "Writing permissions"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by zydy on 2007-03-04
hi, how can it be that i cant write to my other hd's? the write permissions is only allowed for root user. i would like to change that in some way?
i've tried 

sudo chown -R zydy:zydy /media/sda5
and i don't think that works or maybe i did something wrong

and

sudo nano /etc/fstab
to change the permissions in there but i cant figure out the logic in that

# /dev/hdc5
UUID=F2FCF887FCF8477F /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

thats what it says now, can i change the (umask=007) to something else or what is the problem?
can someone tell me? remember im a newbie in ubuntu.

---

### Post by LeoRomanovsky on 2007-03-04
You might not be able to change permissions on a drive that you only have read-only access to, such as a windows ntfs partition. In fact, if this is the case, it would be best not to fiddle with it as Ubuntu only supports reading from an ntfs drive (writing still unreliable). You can look at your fstab file by:

```
gksudo gedit /etc/fstab
```

There should be a line similar to:

```
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
```

In order to gain write permission to the drive, change it to:

```
/dev/hda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0
```

and reboot.

I hope I was on target and this helps.

---

### Post by adarkmethod on 2007-03-04
Im trying to install Skins for my Xmms media player, on the Ubuntu partition, and im getting "Root User only" error.

so my question is, how do I give my main account Root user access through the GUI?

---

### Post by freeflyer57 on 2007-03-04
Just use ubuntu and redownload the skins you want, and then install them into XMMS. It would be much easier.

---

### Post by taurus on 2007-03-04
> **adarkmethod said:**
> Im trying to install Skins for my Xmms media player, on the Ubuntu partition, and im getting "Root User only" error.

so my question is, how do I give my main account Root user access through the GUI?

Press <Alt>F2 and type

```
gksudo nautilus
```

---

### Post by adarkmethod on 2007-03-04
@ FreeFlyer : Its a bigger issue than jsut this, I need to be able to edit files freely, and i dont know how to change the settings correctly, i've only been on Ubuntu for about a 5 days.

@ Taurus: Thank you, that worked great for that quick fix, but is there a way to change my user permissions permanently to allow myslef root access?

---

### Post by taurus on 2007-03-04
You should leave the permissions of your system to what they are.  Changing them to something else can damage your system beyond repair.  So if you need to edit something outside your $HOME, then use either sudo or gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by adarkmethod on 2007-03-04
alright, thank you

---

### Post by ramjet_1953 on 2007-03-04
Isn't there a way to overcome this issue by creating a group that is allowed full access to all drives and then put youself into that group?

I'm not quite sure how to do it, but maybe one of our Linux Gurus may be able to either confirm or refute this suggestion.

Regards,
Roger :cool:

---

