---
title: "Sharing files between two linux machines"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by guano on 2006-06-07
Hey all, this should be so silly...

I want to copy some files from my desktop to my laptop. Both machines run Ubuntu 6.06. I was palnning use a crossover cable. I set the IPs to 192.168.0.1 and 192.168.0.2. I can ping each other. I have set Gnome's Sharing in both relevant folders (NFS). The question is, how can I navigate through these folders, and copy files from one to another? In "network" in Nautilus, I guess I should have a icon for a unix-share, but all I get is the "windows network"...

---

### Post by Nequeo on 2006-06-07
[QUOTE=guano]Hey all, this should be so silly...

I want to copy some files from my desktop to my laptop. Both machines run Ubuntu 6.06. I was palnning use a crossover cable. I set the IPs to 192.168.0.1 and 192.168.0.2. I can ping each other. I have set Gnome's Sharing in both relevant folders (NFS). The question is, how can I navigate through these folders, and copy files from one to another? In "network" in Nautilus, I guess I should have a icon for a unix-share, but all I get is the "windows network"...[/QUOTE]

NFS directories have to be mounted. I don't know how to do it graphically.
I don't know the details of the directories you are sharing, but let assume your username is 'guano' and you shared the directory /home/guano/MyStuff on the PC 192.168.0.2

To access that share from 192.168.0.1 type these commands:

$ mkdir Shared
$ mount -F nfs 192.168.0.2:/home/guano/MyStuff Shared

And if it you don't get any error messages, it's done. Now you'll be able to open up the File Explorer and if you look in the 'Shared' directory you'll be able to acess /home/guano/MyStuff .

If you get an error message, post it up here and we'll try and figure out what's wrong.

Cheers,

---

### Post by dtfinch on 2006-06-07
One cheap shortcut that doesn't require the command line is to install ssh on one or both of them and use gftp, which I've found is more stable transferring over ssh than it is over ftp. I was finally able to get samba working just using the GUI, just to see how far one could get without the command line, but it shared it read only for some reason.

For now the easiest way to share folders between two ubuntu desktops still seems to involve the command line.

---

### Post by guano on 2006-06-08
Thanks Nequeo! That did it.

---

### Post by dvarsam on 2006-06-08
[QUOTE=guano]Thanks Nequeo! That did it.[/QUOTE]

To see how you can do it with SSH, look here:

[http://ubuntuforums.org/showthread.php?t=158176](http://ubuntuforums.org/showthread.php?t=158176)

To see how you can do it with NFS, look here:

[http://ubuntuforums.org/showthread.php?t=186063](http://ubuntuforums.org/showthread.php?t=186063)

Good Luck!

---

