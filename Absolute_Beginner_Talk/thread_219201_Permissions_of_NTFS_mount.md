---
title: "Permissions of NTFS mount"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by martymart on 2006-07-19
I just installed Ubuntu as a server (no desktop) and I mounted my NTFS drive using sudo mount /dev/hdxx /mnt/windows but when I try to change into the windows directory it says Permission denied but the directory is listed as dr-rx------ 1 0 0 so I should be able to enter the directory as I am the administrator.
Does anyone know what the problem is?

Thanks for the help Martin

---

### Post by ajgreeny on 2006-07-19
You need to use the command:-
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

I think the umask=0222 at the end is about permissions, but I'm not sure.  I do know the command works, however, so give it a try.

There are lots of useful tips like this in the following site:-
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Good luck.

---

### Post by Sonofmoog on 2006-07-19
Be very careful in NTFS filesystems.  Ubuntu has read access only.  Most linuxes have read access only, though Xandros 4 claims read-write.

---

### Post by rccharles on 2006-07-19
> **ajgreeny said:**
> You need to use the command:-
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

I think the umask=0222 at the end is about permissions, but I'm not sure.  I do know the command works, however, so give it a try.
Good luck.
The option umask sets the permissions for all files in the ntfs partition. In this case, read and execute. (An on bit, indicates what you do not want. So a 2, says I do not want write access.)

Check out Captive for writing. See:
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

Robert;)

---

### Post by givré on 2006-07-19
captive is not the best driver for write support, since it use ntfs.sys (from windows) behind wine, and on user space (with fuse). So it's quite slow (i want to say really slow :cool: ).
If you want the latest improvement, see here : [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by OU812 on 2006-07-20
In other distros, when I wanted to access a win partition I would launch thunar (a file browser) as root. However, a side effect occurs if I try to copy something from win to linux: the file has root ownership. Oh well. Would this trick work in Ubuntu? Also, in some versions of linux, you're not allowed to launch a gui system apps from the command line (editors, etc). Does ubuntu have this restriction? Thank you.

john

P.S. I hope I didn't hijack this post. It seems related.

---

### Post by martymart on 2006-07-20
Thankyou for all your help people. I managed to mount the NFTS drive and entered it into my fstab file. I have also added it to the NFS demon. I would like to know if windows can read NTFS shares from a NFS server or would I have to install samba for that?

Thanks again,

Martin

---

### Post by givré on 2006-07-20
> **OU812 said:**
> In other distros, when I wanted to access a win partition I would launch thunar (a file browser) as root. However, a side effect occurs if I try to copy something from win to linux: the file has root ownership.
You have to change the owner of the file of your NTFS partition by setting uid=1000 in /etc/fstab.
> **OU812 said:**
> Also, in some versions of linux, you're not allowed to launch a gui system apps from the command line (editors, etc). Does ubuntu have this restriction? Thank you.

No, in fact it's not recommended to launch gui apps with sudo, you can do it but that could mess some system file. The recommended way is to launch a GUI with root via gksu
ex: gksu gedit.

---

### Post by OU812 on 2006-07-20
Thanks givre. What should my fstab look like? Traditionally I use

ro,users,umask=0222

If I need to use some other scheme (that includes your suggestion) what would it look like? Also, could you explain the parameters? (I know simple ones like ro, users, noauto, but only sortof understand umask). Thanks!

john

---

### Post by givré on 2006-07-20
Something like that i guess:
ro,users,umask=0222,uid=1000,gid=1000
gid will also the goup owner to your group.
But check first the number with 'id' in a terminal.

---

### Post by OU812 on 2006-07-20
Thanks again! I think I've figured it out just by looking at it: gid and uid seems straight forward. But with these two parameters I don't think users parameter is necessary. I will try (back up fstab first!).

john

---

