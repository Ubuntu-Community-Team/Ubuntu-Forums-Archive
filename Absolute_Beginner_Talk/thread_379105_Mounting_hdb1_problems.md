---
title: "Mounting hdb1 problems"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Hishgraphics on 2007-03-08
OK after (maybe) installing Edgy into my hda, I can't seem to mount hdb1 using the [psychocats help page](http://www.psychocats.net/ubuntu/mountlinux).

Here's what I've done so far:

[COLOR="DarkRed"]**sudo fdisk -l**[/COLOR] : This lists hdb1 at /dev/hdb1

[COLOR="DarkRed"]**mkdir /media/storage**[/COLOR] : This worked.

[COLOR="DarkRed"]**sudo gedit /etc/fstab**[/COLOR] and added [COLOR="DarkRed"]**/dev/hdb1   /media/storage    ext3    defaults     0     0**[/COLOR] to it.

[COLOR="DarkRed"]**sudo mount -a**[/COLOR] gives me this:
> [COLOR="DarkRed"][B]mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
            missing codepage or other error
            In some cases useful info is found in syslog - try
            dmesg | tail or so[/B][/COLOR]

I also tried to access the /media/storage directory via nautilus but all I have is an empty folder.

Help, anyone?

---

### Post by Malac on 2007-03-08
Try manually mounting /dev/hdb1 with sudo from a terminal and see if that works.
```
sudo mount /dev/hdb1 /media/storage
```Don't specify any file system and see if that mounts.
If it does then you didn't format it with ext3 (or at all) which is what you are telling fstab to use.

---

### Post by Hishgraphics on 2007-03-08
> **Malac said:**
> Try manually mounting /dev/hdb1 with sudo from a terminal and see if that works.
```
sudo mount /dev/hdb1 /media/storage
```Don't specify any file system and see if that mounts.
If it does then you didn't format it with ext3 (or at all) which is what you are telling fstab to use.
Well, mounting with sudo from terminal worked.

sudo fdisk -l says the system is W95 FAT32, so I changed ext3 to vfat.

After that running sudo mount -a worked.

But no automatic icon on desktop. I had to copy paste a "link to storage" icon from /media to /home/<username>/Desktop.

---

### Post by Malac on 2007-03-08
> **Hishgraphics said:**
> Well, mounting with sudo from terminal worked.

sudo fdisk -l says the system is W95 FAT32, so I changed ext3 to vfat.

After that running sudo mount -a worked.

But no automatic icon on desktop. I had to copy paste a "link to storage" icon from /media to /home/<username>/Desktop.
Glad it worked.
It might not show up on the desktop as you mounted it manually.
Try a reboot.
Or 
```
 sudo /etc/init.d/dbus restart
```

---

### Post by Hishgraphics on 2007-03-08
Okay, upon my second reboot, the hdb1 icon, labeled "storage", appeared on Desktop.

But the lother link which I created in my previous post doesn't seem to want to go away. I can't seem to Trash it.

I tried [COLOR="DarkRed"]**sudo chown -R *<user>* :/media/storage**[/COLOR] which only gave me a long series of "*chown: changing ownership of <filename>: Operation not permitted*" messages.

---

### Post by Malac on 2007-03-08
> **Hishgraphics said:**
> Okay, upon my second reboot, the hdb1 icon, labeled "storage", appeared on Desktop.

But the lother link which I created in my previous post doesn't seem to want to go away. I can't seem to Trash it.

I tried [COLOR=DarkRed]**sudo chown -R *<user>* :/media/storage**[/COLOR] which only gave me a long series of "*chown: changing ownership of <filename>: Operation not permitted*" messages.
Careful, if that link is still connected to /media/storage it will be trying to delete/chown all the files that it points to on /dev/hdb1
first run ```
sudo umount /dev/hdb1
```Then try deleting the link you created.
If you can't do it from the terminal run ```
gksudo nautilus
``` which will give you admin nautilus. BE CAREFUL :) and make sure /dev/hdb1 is unmounted

---

### Post by Hishgraphics on 2007-03-08
Thanks man, that worked beautifully to get rid of that infernal link icon.

However I'm still stumped as to how to change permission for hdb1.

Each time I want to drag and drop something to it (from external hard disk drive, for example) I have to [COLOR="DarkRed"]**gksudo nautilus**[/COLOR].

And when I do I get this message on terminal before nautilus runs as root:

> (nautilus:5146): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:5146): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

---

### Post by Malac on 2007-03-08
> **Hishgraphics said:**
> Thanks man, that worked beautifully to get rid of that infernal link icon.

However I'm still stumped as to how to change permission for hdb1.

Each time I want to drag and drop something to it (from external hard disk drive, for example) I have to [COLOR=DarkRed]**gksudo nautilus**[/COLOR].

And when I do I get this message on terminal before nautilus runs as root:
This is my fstab entry for a fat32 drive which lets any user (users) access the files with read-write(rw) and execute(exec) permissions.

```
/dev/hdb2 /media/MISC vfat rw,users,exec,umask=000 0 1
```

---

