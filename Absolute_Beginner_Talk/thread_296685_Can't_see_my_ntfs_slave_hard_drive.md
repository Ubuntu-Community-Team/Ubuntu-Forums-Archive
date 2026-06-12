---
title: "Can't see my ntfs slave hard drive"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by havedampton on 2006-11-09
I boot ubuntu with a 4gb drive I stole from my old machine.

I have an 80gb NTFS hard drive with all my music files etc. that I was using as the slave when I was running windows.  I've connected it and can see it in the device manager, but I can't find any way to access it.  I've looked around the forums and can't find anything that I understand (being a complete beginner.)  I'm a little scared of doing too much that I don't understand because I really don't want to accidentally erase all my music.

Any help would be greatly appreciated.

---

### Post by John.Michael.Kane on 2006-11-10
Have a read [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by bodhi.zazen on 2006-11-10
> **havedampton said:**
> I boot ubuntu with a 4gb drive I stole from my old machine.

I have an 80gb NTFS hard drive with all my music files etc. that I was using as the slave when I was running windows.  I've connected it and can see it in the device manager, but I can't find any way to access it.  I've looked around the forums and can't find anything that I understand (being a complete beginner.)  I'm a little scared of doing too much that I don't understand because I really don't want to accidentally erase all my music.

Any help would be greatly appreciated.

To mount the drive ro (read only):[list=number][*]Make a mount point.[*]mount[/list]

First open a terminal.

Then type these commands (assuming the partition is /dev/hdb1):
```
sudo mkdir /mnt/music
sudo mount /dev/hdb1 /mnt/music -t ntfs 
```

_Note_: if the partition is not /dev/hdb1 you will need to adjuxt accordingly.

To make the mount automatic at boot you need to edit fstab:```
sudo gedit /etc/fstab
```Add this line:> /dev/hdb1 /mnt/music ntfs auto,users,ro 0 0Again, adjust your partition accordingly if needed.

To mount your ntfs partition rw (read-write) see this link: [ntfs-3g](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)

_Note_: [color=red]There may be a risk of data loss with ntfs-3g[/color].

HTH 8)

---

