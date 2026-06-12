---
title: "Things keep resetting."
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Anthraxx on 2006-08-29
After I mount an ntfs partition, or change the DNS server so I can connect to the 'net, a few minutes pass and then it returns to the way I had it before! How can I stop this?

---

### Post by raldz on 2006-08-29
To automount your partition, you have to edit your /etc/fstab so that your partitions will mount on boot.. to edit your DNS permanently, open your /etc/resolv.conf file an enter your DNS manually there..

---

### Post by Anthraxx on 2006-08-29
I edited the resolv file, but it still reverts.

---

### Post by xyz on 2006-08-29
It may make things a bit clearer to us if you could post the output of:
```
sudo gedit /etc/fstab
```
to see what may be wrong there.

---

### Post by Iowan on 2006-08-29
[http://www.ubuntuforums.org/showthread.php?p=1421423#post1421423]("http://www.ubuntuforums.org/showthread.php?p=1421423#post1421423")
Not a cure-all, but does this one help?

...especially the part about:> remove "domain-name-servers," from that section and save the file with ctrl+x, Y, Enter.

now you need to set the correct DNS servers in the file /etc/resolv.conf (sudo open it and add them one per line).

This way they wont get changed when you grab an IP via DHCP.

---

### Post by Anthraxx on 2006-08-30
It's all good now. I commented out the first function in resolv.conf, and manualy edited my fstab.

Something weird though: whenever I type sudo 

gedit /etc/fstab

it opens a blank file, but when I pasted what xyz posted, it works fine. I'm 100% sure I'm typing the right thing.

---

### Post by Anthraxx on 2006-08-30
OK, I'm retarded, I was typing ect not etc. Whenever I try to access my Windows partitions, it says I don't have the right permission to access them. This is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1	/driveofC	ntfs	auto,user,rw		0	0
/dev/sda1	/driveofD	ntfs	auto,user,rw		0	0
```

---

### Post by Anthraxx on 2006-09-01
*bump*

---

### Post by Scorpuk on 2006-09-01
Do you have the guest account activated in windows?

I think this will help.

---

### Post by eternalis on 2006-09-01
> Whenever I try to access my Windows partitions, it says I don't have the right permission to access them.

What do you mean by access? Do you mean mounting or are you able to mount them already?

---

### Post by Anthraxx on 2006-09-01
I guess they're mounted because before I edited fstab, it said they weren't mounted, but now it says that I don't have the permissions. I can type this:

sudo mount -t ntfs /dev/sda1 /windows -o nls=utf8,umask=0222

but I want them to be working automaticaly, when I start up.

---

### Post by Scorpuk on 2006-09-01
Do you get the permission problem if you manually mount the drives or does it happen with both?


As I said previously try activating the windows guest account. Even with windows to windows sharing I had to activate the guest account otherwise it would ask me for a username and password to get access to files. 

control panel -> user accounts (should be somewhere there - I cant check as work computer is locked down for administrator privilages)


I am presuming windows xp btw :)

---

### Post by eternalis on 2006-09-01
Try typing:
mount
in the terminal.

Does it show your Windows Partition as mounted?

Also check this page for more help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Anthraxx on 2006-09-02
```
/dev/sdb1 on /driveofD type ntfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /driveofC type ntfs (rw,noexec,nosuid,nodev)
```

Yup, sure does! Also, activating the guest account does precicely bupkus.

---

