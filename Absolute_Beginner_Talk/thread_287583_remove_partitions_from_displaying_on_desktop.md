---
title: "remove partitions from displaying on desktop"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Forge42 on 2006-10-28
Hey all:

Newbie question here.  I have several other partitions on my drive that linux has mounted.  They all show up as icons on my desktop.  I would like to remove them from my desktop (I'm a desktop clutter freak), but I don't want to unmount them cause I still want to be able to access those partitions via "Places".  The 'move to trash' option isn't available.  Can anyone tell me how to get these 'shortcuts' off my desktop w/o completely unmounting those partitions?

---

### Post by NeoLithium on 2006-10-28
I think if you just highlight and delete them; it won't unmount; but simply remove the icon to access them from the desktop.

---

### Post by Forge42 on 2006-10-28
> **NeoLithium said:**
> I think if you just highlight and delete them; it won't unmount; but simply remove the icon to access them from the desktop.

That sounded simple enough that I was certain it would work.  However, I get an error message that I "can't move the volume to trash.  If I want to unmount it, use the unmount option in the pop up".

Any other ideas?

---

### Post by taurus on 2006-10-28
You can mount those partitions somewhere else like /mnt instead of /media in /etc/fstab!!!

---

### Post by Forge42 on 2006-10-29
> **taurus said:**
> You can mount those partitions somewhere else like /mnt instead of /media in /etc/fstab!!!

Okay...  I think this was done by the install routine for edge.  Those icons have been there from the beginning.

Is changing the fstab file as simple as just replacing instances of /media with /mnt or is there something else I should know?  Just reboot to put the changes into effect?

---

### Post by taurus on 2006-10-29
The best way is to unmount those partitions by hand first.  Then edit /etc/fstab and replace the /media with /mnt.  Then, create those mount points in /mnt or you will get error message when you try to mount those partitions.  Then mount them again.  No need to reboot!!!  

```

sudo umount /media/whatever_the_name <-- to unmount a partition in /media...
gksudo gedit /etc/fstab <-- to edit /etc/fstab...
sudo mkdir /mnt/whatever_the_name <-- to create a mount point in /mnt...
sudo mount -a <-- to mount those partitions again...

```

---

### Post by Forge42 on 2006-10-29
> **taurus said:**
> The best way is to unmount those partitions by hand first.  Then edit /etc/fstab and replace the /media with /mnt.  Then, create those mount points in /mnt or you will get error message when you try to mount those partitions.  Then mount them again.  No need to reboot!!!  

```

sudo umount /media/whatever_the_name <-- to unmount a partition in /media...
gksudo gedit /etc/fstab <-- to edit /etc/fstab...
sudo mkdir /mnt/whatever_the_name <-- to create a mount point in /mnt...
sudo mount -a <-- to mount those partitions again...

```

That worked well.. thanks!


Now, for extra credit, can you tell me how to get those partitions to show up as places under my "Places" and/or how to get them to show up under my 'Computer' ?

*edit*
Scratch that...  I got what I wanted using bookmarks in Nautilus.  But thanks for your help!
*/edit*

---

### Post by dukejib on 2007-11-01
> **Forge42 said:**
> That worked well.. thanks!


Now, for extra credit, can you tell me how to get those partitions to show up as places under my "Places" and/or how to get them to show up under my 'Computer' ?

*edit*
Scratch that...  I got what I wanted using bookmarks in Nautilus.  But thanks for your help!
*/edit*

@forge42
It automatically show up in Places.

---

