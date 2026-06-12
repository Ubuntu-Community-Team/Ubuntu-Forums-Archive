---
title: "those hard disk icons on the desktop"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by sri on 2006-08-13
hi, its been  about a month since i converted to ubuntu and till now ive somehow tolerated those ugly harddisk icons on my desktop.
i would appreciate it if you could show me how to make them disappear.
also is there anything like XP's "arrange icons>hide icons" in ubuntu, that would be great

---

### Post by blackened on 2006-08-13
Use gconf-editor to do it. Note this will keep all volumes from showing on the desktop including dvd, cdrom, floppy, and usb drives.

Under Applications->System Tools->Configuration Editor

Navigate to apps->Nautilus->desktop
Deselect "volumes_visible".

---

### Post by kinematic on 2006-08-13
you could also change your fstab lines for the drives you don't want to automount.
this is what i did for 2 partitions that hold 2 other distro's.
/dev/hda#	/media/hda#	ext3	nouser,noexec,rw,noauto	0 0.
works fine for me.

---

### Post by Frank Golden on 2006-08-13
> **kinematic said:**
> you could also change your fstab lines for the drives you don't want to automount.
this is what i did for 2 partitions that hold 2 other distro's.
/dev/hda#	/media/hda#	ext3	nouser,noexec,rw,noauto	0 0.
works fine for me.Or you could change the icons. Right click, choose properties and click on the icon in the properties window. There are tons of icons in /usr/share/pixmaps. See link to screenshot of my
desktop.

[http://i30.photobucket.com/albums/c338/fjgold/Screenshot-1.png](http://i30.photobucket.com/albums/c338/fjgold/Screenshot-1.png)

The two M$ icons I created by modifying winnt.bmp a wallpaper image
on my XP install located at C:\Windows. The LINNUXSHARED icon I got
by googling "gnome icons". I placed them in /usr/share/pixmaps by
using "gksudo nautilus" command in terminal (without quotes). This
command opens your file browser (nautilus) in a kind of super user mode,
where file and folder permissions are relaxed to allow you to copy to
/usr/share/pixmaps. Just be careful using this command, it does bypass
the security features of root and will allow you to change things
you shouldn't.
The images in pixmaps are .png images .ico images should work also.
I have changed .ico to .png images in Ubuntu by just changing the file extension. I don't know if this is proper procedure but it works for me.

---

### Post by sri on 2006-08-13
well i still havent taken them out , but thanks for your suggestions. its kindof embarassing but i hadnt figured out how to change my flock icon till i read your post.
btw, thats some sleek clock you got there

---

### Post by Frank Golden on 2006-08-14
> **sri said:**
> well i still havent taken them out , but thanks for your suggestions. its kindof embarassing but i hadnt figured out how to change my flock icon till i read your post.
btw, thats some sleek clock you got there
That clock is gdesklet available with a bunch of other desktop
applets.
Go to system>administration>Synaptics Package Manager.
Do a search for gdesklets and install.

---

