---
title: "Where are you MBR?"
date: 2011-11-18
forum: Any Other OS
---

### Post by Foobarz on 2011-11-18
How do I find the location of the MBR on my system? I'm trying to install burg, following instructions here: [http://www.omgubuntu.co.uk/2011/05/beautiful-burg-boot-loader-gets-ubuntu-11-04-ppa/](http://www.omgubuntu.co.uk/2011/05/beautiful-burg-boot-loader-gets-ubuntu-11-04-ppa/)   
It says install burg to master boot record, but i don't know where mine is. . .

---

### Post by Miljet on 2011-11-18
The MBR (Master Boot Record) is located in the first sector of the first track of your hard drive. It is not a part of any operating system you may have installed.

It might behoove you to heed this warning: > Upgrading your boot-manager to BURG is not recommended unless you’re aware of what you’re doing and how to reverse any changes.

If you are interested in learning more, I suggest starting with this link: [http://members.iinet.net.au/%7Eherman546/p6.html](http://members.iinet.net.au/%7Eherman546/p6.html)

---

### Post by Rubi1200 on 2011-11-19
Just to add to what Miljet said, if this is a Wubi install you will completely break it!

---

### Post by pierreyy on 2011-11-19
the MBR is not located in a partition

check the link 

```
 http://en.wikipedia.org/wiki/Master_boot_record 
```be careful with BURG ive heard a lot of complaints....


btw if you do install it and want to get rid of it 
```
 http://askubuntu.com/questions/9592/how-to-reinstall-grub-after-burg 
```

---

### Post by Foobarz on 2011-11-19
Never mind I know where it is its just on the whole hard drive, /dev/sda for me since i only have one hard drive with many partitions. I got BURG working, now just need a good plymouth for my linux mint 12 (which doesnt have a plymouth splash)

---

### Post by Perfect Storm on 2011-11-19
Moved to Other OS/Distro Talk.

---

