---
title: "Getting rid of mounted disk icons from desktop ???"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by menawollas on 2007-05-20
Hi, I'm confused.:(

I thought that, when you mount a disk, the icon would appear on the desktop if it was mounted on /media. If it wasn't, it wouldn't.

Also, on searching, its suggested to use gconf-editor to set the nauti;us desktop settings to not show mounted volumes.

However, whenver and wherever I mount a disk, its appearing om the desktop. !!!!

What i want to do is something like 

sudo mount -t ext3 /dev/hdb6 /home/me/music -o defaults 

But when I do I get a /home/me/music icon on the desktop - and thats not mounted on media, and I have used gconf-editor to not display mounted volumes.

How do I mount disks, without getting them on my desktop ??????

Thanks

---

### Post by overdrank on 2007-05-20
> **menawollas said:**
> Hi, I'm confused.:(

I thought that, when you mount a disk, the icon would appear on the desktop if it was mounted on /media. If it wasn't, it wouldn't.

Also, on searching, its suggested to use gconf-editor to set the nauti;us desktop settings to not show mounted volumes.

However, whenver and wherever I mount a disk, its appearing om the desktop. !!!!

What i want to do is something like 

sudo mount -t ext3 /dev/hdb6 /home/me/music -o defaults 

But when I do I get a /home/me/music icon on the desktop - and thats not mounted on media, and I have used gconf-editor to not display mounted volumes.

How do I mount disks, without getting them on my desktop ??????

Thanks

Hi I am not a expert but here is a link that may help
[http://www.psychocats.net/ubuntu/mountwindows#mountpoint](http://www.psychocats.net/ubuntu/mountwindows#mountpoint)
**Be sure to backup your fstab** then you can try and change the mount point from like
*sudo mount -t ext3 /dev/hdb6 /home/me/music -o defaults*
sudo mount -t ext3 /dev/hdb6 /"*folder of your choice*"/me/music -o defaults
May not work but just trying to help. Good luck!:p

---

### Post by mahiyar on 2007-05-20
What are you doing in gconf-editor for the icons not to show. Is it the same as this >>System Tools >Configuration Editor>Apps>Nautilus>Desktop and then click Volumes visible.

---

### Post by menawollas on 2007-05-20
The psychcats link is about mounting windows partitions, I'm happy with how to do it, and in this case its an ext3 partition I want to mount. It mounts fine I just dont want the bloody icon on the desktop ](*,)

I presume that the menu approach (config editor etc.) is the same as gconf-editor. It doesn't matter what I do, the icons still appear. I have even checekd the other ones (show computer show wastebasket etc) and in that case, the icons DONT appear. so I'm totally confused about whats going on there.

---

### Post by scotty32 on 2007-05-20
yeah i had this problem too, untill recently

it turns out if you mount a drive to /media it adds it to the desktop and "Places"

choose either /mnt (what i use, now) or anything other than /media

---

### Post by menawollas on 2007-05-20
But I mounted it on /home/<user>/<mydir> and it still appears !

---

### Post by scotty32 on 2007-05-20
am still a newbie, so not really sure

could try mounting to /mnt then using a sym link with this:
ln -s /mnt/<drive> /home/<user>/<dir>

---

### Post by Hero of Time on 2007-05-20
I have a few drives mounted at boot using fstab. I see three drive icons on my desktop, WindowsXP, Programs (both NTFS) and File System (/ folder). When I plugin my usb drive, that icon shows up aswell. I have another partition, ext3 formatted, mounted to /data and that icon isn't on my desktop, nor on the quickpick locations. You can try to do what scotty32 said and mount them to another location and creating a symlink. See if the icon is on your desktop before you create the symlink, then see if it appears after the symlink. If it appears after the symlink, I guess you have to either live with the icon or leave the symlink/mounts in your home folder.

---

### Post by menawollas on 2007-05-20
Even when I mount it an /mnt it still appears on my desktop !!!!!

---

### Post by scotty32 on 2007-05-21
how are you mounting it?

is it mounted twice? say once by fstab, and once by you doing the mount command?

if you click on the icon at the desktop, Nautilus will tell you where you are (eg /mnt or /media)

---

### Post by adohall on 2007-05-25
> **mahiyar said:**
> What are you doing in gconf-editor for the icons not to show. Is it the same as this >>System Tools >Configuration Editor>Apps>Nautilus>Desktop and then click Volumes visible.
I'd love to follow your advice about unchecking 'Volumes visible', but I don't have a 'Configuration Editor' under 'System tools'. Is there another way of acessing the config editor?

---

### Post by adohall on 2007-05-25
> **adohall said:**
> I'd love to follow your advice about unchecking 'Volumes visible', but I don't have a 'Configuration Editor' under 'System tools'. Is there another way of acessing the config editor?
it's OK - I found it. First I had to make the 'Configuration Editor' visible in system/preferences/main menu.

Worked beautifully by the way. I also managed to make a 'garbage bin' visible on the desktop

---

### Post by mahiyar on 2007-05-26
adohall - glad to be of help

---

