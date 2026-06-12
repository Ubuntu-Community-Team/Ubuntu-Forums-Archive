---
title: "Play movie with Totem over smb network?"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by xiaogwu on 2006-04-25
Has anyone been able to play a movie (divx, avi) that is located on a windows share drive in Totem?  I have smb setup and can access the drive but can't seem to browse for it in totem.

The only way I can get it to work is copy the movie to the local Ubuntu drive.

---

### Post by mjm115 on 2006-04-25
Usually, I have to mount the smb share first and then I am able to watch it over the network.

---

### Post by GrammatonCleric on 2006-04-25
Do it all the time with totem-xine, mplayer, or vlc.  I steam tv and other video that has been recored on my HTPC.

[http://linuxjunkie.net/gallery/displayimage.php?album=2&pos=4](http://linuxjunkie.net/gallery/displayimage.php?album=2&pos=4)


What version of totem are you using?  Do you have have all the codec's installed?

GC

---

### Post by echo $USER on 2006-04-25
I use vlc to stream from my smb share.  It can stream entire directories so I dont have to keep opening new files.

---

### Post by adamkane on 2006-04-25
You have to mount the share, so that Totem will think your files are located in a local directory:
[http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read]("http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read")

Some apps can browse Samba shares, but this is not the norm.

---

### Post by xiaogwu on 2006-04-27
Thanks everyone, I'll try this.

---

