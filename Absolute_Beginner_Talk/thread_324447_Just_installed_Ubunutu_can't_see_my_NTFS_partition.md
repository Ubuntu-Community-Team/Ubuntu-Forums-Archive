---
title: "Just installed Ubunutu can't see my NTFS partition"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Tutu 1234 on 2006-12-23
Looked in help it said click system->administration->disks and mount it on my install it has no disks it goes device manager and then keyboard indicator plugins.

I'm an unfortunate noobie who's spent all day cleaning up hard disk space to install it and now desperately wants to watch a film before bed (On my NTFS partition).

I loved the install though I tried gentoo and gave up when I could not for love nor money get it to see my Internet connection.

Also how do I screen grab in Ubuntu so I can paste into GIMP

Thanks for your time

:EDIT am using 6.10

---

### Post by Bachstelze on 2006-12-23
GIMP has a screenshot feature builtin. It's in FIle > Acquire.

---

### Post by angkor on 2006-12-23
Can you post the output of the command:

```
sudo fdisk -l
```

It will prompt you for your user password.

---

### Post by rsambuca on 2006-12-23
You'll first want to make a directory to mount the NTFS partition to.  In a terminal:
```
mkdir /media/insert-the-name-you-want-to-call-it-here
```

then mount the partition to the new directory with```
sudo mount /dev/hd?? /media/insert-the-name-you-want-to-call-it-here
```
where hd?? is the partition in question, ie hda1

---

### Post by Tutu 1234 on 2006-12-23
Thanks, worked a treat.

---

### Post by juff on 2006-12-26
Hi all,

I'm a newbie and followed rsambuca's instructions for mounting the hda1 partition which holds my XP installation.  However, when I double click on the icon (C_drive) in the media folder, it gives me the following message:

[COLOR="Red"]You do not have the permissions necessary to view the contents of "C_drive".[/COLOR]

How do I get the magic permissions?  :confused:

---

### Post by Melancholy on 2006-12-26
Try sudo Nautilus from terminal and browse to the /media/C folder

---

### Post by Duck2006 on 2006-12-26
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by navneeth on 2006-12-26
I have a related question. 

I followed instructions available here:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html)

I can see my Windows C: drive installed in the other hard disk (hda1). Can I use the same procedure to access another Windows partition (hdb1) that is sitting in the same disk as Ubuntu?

---

### Post by Duck2006 on 2006-12-26
Yes

---

### Post by navneeth on 2006-12-26
Thanks. So do I just change hda1 to hdb1, which is also NTFS

```
/dev/hda1 /media/windows ntfs umask=0222 0 0
```

and add it to fstab? Or do I need to create another directory, etc. ?

---

### Post by juff on 2006-12-26
> **Melancholy said:**
> Try sudo Nautilus from terminal and browse to the /media/C folder

Thanks for the tip Melancholy, but it only half worked.  I stopped getting the message about lack of permissions, but nothing appeared in the C_folder.  Also, I got this error message when I entered sudo nautilus in the console:

[COLOR="Blue"](nautilus:6371): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
[/COLOR]

Anyway, I tried the advice at  	[COLOR="Red"]http://www.psychocats.net/ubuntu/mountwindows[/COLOR] and that worked OK.  For any other newbies reading this, here are the extra entries I put into my fstab file to see the  Windows ntfs partitions on my master drive (hda1 and hda2).  Note that I had to make new directories at /windows and /data, and don't forget to use the [COLOR="Blue"]sudo mount -a[/COLOR] command.

# /dev/hda1
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
# /dev/hda2
/dev/hda2 /data ntfs nls=utf8,umask=0222 0 0

---

### Post by Duck2006 on 2006-12-26
Good to see you got it happing

---

