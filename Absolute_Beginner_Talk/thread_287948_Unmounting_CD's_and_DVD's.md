---
title: "Unmounting CD's and DVD's"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Belgatom on 2006-10-29
When I first tried Ubuntu (just a few days ago), I was impressed with the little icon that popped up on my desktop whenever I entered a removable media. After being confounded why my cd/dvd drive didn't open, I saw why it is there. 

Unfortunately, it doesn't pop up anymore. I have experimented with some things but all under guidance of this forum. I can unmount via System - Administration - Disks. This worked with Data DVD's but when I was watching a commercial DVD and needed to eject, this didn't work at all. I had to log-off to get access to the CD/DVD. 

How is his fixable?

---

### Post by CatKiller on 2006-10-29
I don't know why you'd have had this problem - perhaps something wrong with your /etc/fstab? Anyway, **umount /cdrom** should unmount the drive. It might be mounted somewhere else, if you have more than one drive, so you'd use umount followed by the mount point if that is the case.

You could also try **gconf-editor** and check to see if the /apps/nautilus/desktop/volumes_visible is set to **true** - if it isn't, then you won't get icons on your desktop.

Also, there used to be an auto-mount widget that you could put on your panel - it may still be there. That would save you typing in commands. It's called Disk Mounter, I believe.

---

### Post by Jose Catre-Vandis on 2006-10-29
Is it just on the desktop or in nautilus as well?

Have you disabbled the volumes_visible option in conf editor?
(Applications>System Tools>Configuration Editor>apps>nautilus>desktop)
You want it enabled - with a tick

---

### Post by Belgatom on 2006-10-29
> **CatKiller said:**
> I don't know why you'd have had this problem - perhaps something wrong with your /etc/fstab? 

My fstab looks like this. I added the bottom lines myself when I wanted my disks to be mounted on bootup. Could that have done something. 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5	/home/belgatom/music	ext3	defaults	0	0
/dev/hdb6	/home/belgatom/store	ext3	defaults	0	0


> **CatKiller said:**
> 
Anyway, **umount /cdrom** should unmount the drive. It might be mounted somewhere else, if you have more than one drive, so you'd use umount followed by the mount point if that is the case.


This works when using the mount point "umount /media/cdrom0. So that's already a step in the write direction. 

> **CatKiller said:**
> 
You could also try **gconf-editor** and check to see if the /apps/nautilus/desktop/volumes_visible is set to **true** - if it isn't, then you won't get icons on your desktop.


This is set to visible, so it's not that. (This did however teach me something more, so lotta thx for that)

> **CatKiller said:**
> 
Also, there used to be an auto-mount widget that you could put on your panel - it may still be there. That would save you typing in commands. It's called Disk Mounter, I believe.
A widget? I am waiting for Gdekslet to get their site up again to have a look at that. 

But I would really like to get the basic functionality up and running again.

---

### Post by Belgatom on 2006-10-29
> **Jose Catre-Vandis said:**
> Is it just on the desktop or in nautilus as well?[/QUOTE

Euhmm, how do I verify this? 

[QUOTE=Jose Catre-Vandis;1683097]
Have you disabbled the volumes_visible option in conf editor?
(Applications>System Tools>Configuration Editor>apps>nautilus>desktop)
You want it enabled - with a tick

As per above, it is ticked. Maybe I will untick it and the tick it again. I know windows had some issues with that sometimes.

****edit****

Nope, that didn't do it. What I have noticed, is that it seems to be in "autorun" mode. I mean, when I enter a DVD or CD, it starts filemanager or VLC automatically.

---

### Post by CatKiller on 2006-10-29
> **Belgatom said:**
> My fstab looks like this. I added the bottom lines myself when I wanted my disks to be mounted on bootup. Could that have done something. 

Well, your line looks like my lines, and mine works, so I guess it's not that ;)

> A widget? I am waiting for Gdekslet to get their site up again to have a look at that. 

It's just a standard panel item: Right-click, Add to Panel, Disk Mounter.

> But I would really like to get the basic functionality up and running again.

I can understand that. I've run out of ideas as to what might have caused it though. Sorry.

btw, Nautilus is the file manager. So Jose Catre-Vandis was asking if you got the functions you need by opening a Nautilus window.

---

### Post by Belgatom on 2006-10-29
> It's just a standard panel item: Right-click, Add to Panel, Disk Mounter.

Don't know if this has something to do with the overal problem but I can't seem to get that widget on my menubar/panel. Tried draggin', tried "button ADD" but doesn't appear.

---

### Post by CatKiller on 2006-10-29
Have you tried adding it to the panel when you haven't got a disc in?

> ****edit****

Nope, that didn't do it. What I have noticed, is that it seems to be in "autorun" mode. I mean, when I enter a DVD or CD, it starts filemanager or VLC automatically. These sorts of settings are handled by the gnome-volume-properties application (System -> Preferences -> Removable Drives and Media). Perhaps there's something in there that's amiss?

---

### Post by zappa on 2006-10-29
I know a friend who had the same problem. Are you using LDAP by any chance? 
Check this: 
[http://www.ubuntuforums.org/archive/index.php/t-186560.html](http://www.ubuntuforums.org/archive/index.php/t-186560.html)

---

