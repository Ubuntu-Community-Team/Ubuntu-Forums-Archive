---
title: "Sharing files on a home network"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by deathscytheh64 on 2006-08-14
So I'm a new Linux user, and trying to migrate from Windows. I love it on my 4 year old laptop cause its too old for gaming anyway but I've noticed a problem from constant use. From being an exclusive workstation for me, I've accumulated files that I would really like on my desktop...pictures, music, writings...

I send files from my Windows XP Desktop to the Dapper Drake install and pull whole directories of files, but I realized that it wasn't so easy trying to get files from Linux to Windows.

Aside from the cool Firefox fix for speeding it up and Automatix, I'm a right out of the box install.


I've tried looking into samba but it doesn't work (as in, for some reason my updated ubuntu is too updated?), and while apparently there is a command prompt solution (smbsomething or other), I can't even move files in command let alone change network file permissions :-? .

So in the end, I'm not wanting to turn my laptop into a web server but want to do the equivalent of sharing my linux folder on the network.

Thanks in advance and feel free to smite this thread if I missed the obvious solution on a wiki somewhere (be sure to pm/email me first!)


Justin

---

### Post by h2gofast on 2006-08-15
I'm pretty sure the only ways to share files from a linux box to a windows box is either running a ftp server or using samba.  You are going to have to use synaptic to install samba.  Webmin was helpful setting up samba.  Also there is an option in nautilus for sharing files via samba,  I imagine there is a kde equivalent as well.

---

### Post by kernelpanicked on 2006-08-15
Is the Windows machine's drive shared? If so just mount it across the network. I do this to access my wife's box.

sudo mount -t cifs -o username=username,password=xxx //192.168.1.2/C$ /shares/windows

If you want it permanent, add it to /etc/fstab.

//192.168.1.2/C$ /shares/windows  cifs    username=username,password=xxx   0 0

You can then just cp the files back and forth all you want.

---

### Post by deathscytheh64 on 2006-08-15
As for the reason of Samba, the attached screenshot is what i get.

As for mounting, I do have a partition on my windows desktop that acts like a   file server but its read only right now and mounting drives would make me nervous since this is a laptop and won't necessarily always be at my home network.

I'd like to get samba working, so any help for that is appreciated. But also if mounting my windows drive cross network sounds good, then i could use advice on what i need to do windows side to help. (probably make it not read only, and what username/pass the script was asking for)

---

### Post by kernelpanicked on 2006-08-15
Just a guess, but do you have universe and multiverse enabled on your Ubuntu box? If not you might try enabling them and see if it fixes the dependency problem.

The username and password to use in the mount command is the  Windows username and password for authenticating to the share. For this to work properly the Windows share would need to be writeable. If you're worried about the Windows box not always being on the network, that isn't a problem. Change the fstab entry to the following.

//192.168.1.2/C$ /shares/windows  cifs    username=username,password=xxx,noauto   0 0

This will keep it from mounting on boot, and when you need it you would just have to mount it with something like 

sudo mount /shares/windows

As a side note the (192.168.1.2/C$) and (/shares/windows) are just examples on my setup. Yours may differ, but if you need any help working it out I'd be glad to assist, or I'm sure someone else can give a hand on these forums. Anyway, I hope this has helped some.

---

### Post by deathscytheh64 on 2006-08-15
Got Samba to work (well, installed) but still couldn't access it from the Windows machine. It wanted a username/pass to access and my desktop doesn't have a pass...

Got a workaround by making the shared folder on my windows desktop as editable by other computers and just plopped the file there. Changing it back later...

EDIT: BTW, My dependencies were off actually and thats what let samba install. It was having problems with multiple lists or something, but seems to be updated and working fine now.

---

