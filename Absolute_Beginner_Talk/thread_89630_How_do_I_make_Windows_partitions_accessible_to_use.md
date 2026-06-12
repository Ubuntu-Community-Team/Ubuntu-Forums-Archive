---
title: "How do I make Windows partitions accessible to users?"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by zvodd on 2005-11-13
Thats pretty much it:
How do i set root password?

When i was installing Ubuntu 5.10 from the CD it never asked me for a root password. Is this the way its ment to be? If so how do i set my root password, so that i can login as root?

---

### Post by dwalker on 2005-11-13
If you're using Command Prompt, I believe it's...

> sudo passwd root

---

### Post by heimo on 2005-11-13
You should not log in using root privileges. Instead you should use sudo or gksudo to run programs that require super user rights. This should answer your questions (it also instructs howto set root password, if neccessary - not recommended):
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by kilps on 2005-11-13
[QUOTE=heimo]You should not log in using root privileges. Instead you should use sudo or gksudo to run programs that require super user rights. This should answer your questions (it also instructs howto set root password, if neccessary - not recommended):
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]
When I logon I can see my windows partition of the hard drive on my desktop but when I try and open it it says I do not have permissions and only root has/can give permissions. But I cannot logon as root from the logon screen so  how do I change the permissions? If through terminal how? Thanks

---

### Post by tseliot on 2005-11-13
[QUOTE=kilps]When I logon I can see my windows partition of the hard drive on my desktop but when I try and open it it says I do not have permissions and only root has/can give permissions. But I cannot logon as root from the logon screen so  how do I change the permissions? If through terminal how? Thanks[/QUOTE]
Please post your /etc/fstab 

```
sudo gedit /etc/fstab
```

OR
 
```
sudo nano /etc/fstab
```

---

### Post by kilps on 2005-11-13
[quote=tseliot]Please post your /etc/fstab 

```
sudo gedit /etc/fstab
``` 
[/quote]

I havn't an internet connection on ubunut yet and cannot get the file over to windows - i'll ask the question once I have internet - thanks ;)

---

### Post by tseliot on 2005-11-13
[QUOTE=kilps]I havn't an internet connection on ubunut yet and cannot get the file over to windows - i'll ask the question once I have internet - thanks ;)[/QUOTE]
BTW try this:

```
sudo gedit /etc/fstab
```

You will see a text like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
[COLOR="Red"]/dev/sda2[/COLOR]	[COLOR="Lime"]/media/windows2[/COLOR] [COLOR="Blue"]ntfs noauto,users,exec,ro,umask=000 0 0[/COLOR]
```



Now, the last line in my previous (I don't use Windows any more) fstab is the one which interests you.

The part in red is the one which represents the harddisk or the partition in which you installed Windows (yours might be /dev/hda , etc.).

The part in green represents the folder on which that partition is mounted (i.e. the folder in which you can access the partition). It is usually "/media/name_of_the_partition" (but it may vary)

The part in blue is the part you should be particularly interested in because it defines the filesystem of the partition (NTFS, ext3, etc) and the authorisation.

Try this:

```
Use the blue part in the example to replace that part in your fstab ([COLOR="Red"]only for your Windows partition/s[/COLOR])
```

---

### Post by aysiu on 2005-11-13
This link explains everything about mounting Windows partitions to be readable:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

