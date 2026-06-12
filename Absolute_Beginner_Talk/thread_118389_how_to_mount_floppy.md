---
title: "how to mount floppy"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by raul99 on 2006-01-16
I have a recent install of ubuntu 5.10. I want to mount the floppy drive. My 
/mnt directory is empty. Where do I find a file in the file system  or an icon on the GUI to mount the floppy?
Thanks

---

### Post by fourchannel on 2006-01-16
firsts things firsts... you'll need a directory. ubuntu actualy mounts it's stuff under /media. but it *really* doesn't mater where you put it, just: ```
sudo mkdir /place/to/mount/floppy
``` 
and it depends on how your floppy was formatted to be able to mount it. such options are, i *think*, vfat, ext2, ext3, msdos? ??

but what you would do is launch a console *Applications>Accessories>Terminal* and type ```
sudo mount -t *FilesystemType* /dev/fd0 /place/to/mount
```

'auto' is also an option for the filetype. hope that helps.

---

### Post by GreyFox503 on 2006-01-16
If your floppy drive is listed in /etc/fstab, then you can probably just do this:

```
mount /dev/fd0
``` 
Look in the /media folder for the floppy's contents.  If that doesn't work, then you need to add a line to your /etc/fstab like this:

```
/dev/fd0        /media/floppy    auto        noauto,user,sync    0 0
``` 
That's the line from my fstab.

Once you get this whole thing working, try this: right click on your gnome panel on an empty spot and choose "Add to Panel", then choose "Disk Mounter"  it's a quick way to mount devices listed in your fstab.

---

### Post by fourchannel on 2006-01-16
I'ma have to do that. Way easier than my method lol. well, in the long run.

--Edit--

I can't spell.

---

### Post by Sef on 2006-01-16
If this works for you, it will automount your floppies:

> There is a bug in Breezy, so often the floppies won't automount. To get them to automount, go to this site:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

1) Download pmount_0.9.6-1~breezy1_i386.deb

2) Install --> sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb

3) enter password

4) After it finishes installing, your floppy should mount and umount automatically.

I found that bug and fix from this thread: [http://ubuntuforums.org/showthread.php?t=93139&page=2](http://ubuntuforums.org/showthread.php?t=93139&page=2)

---

### Post by Abracon on 2006-01-16
[QUOTE=fourchannel]but what you would do is launch a console *Applications>Accessories>Terminal* and type ```
sudo mount -t *FilesystemType* /dev/fd0 /place/to/mount
```[/QUOTE]

How do I get to the applications menu from the root directory?

---

### Post by raul99 on 2006-01-16
I was able to get it mounted and unmounted with work on the text editor, the floppy is found in /media as was mentioned.It is present in the /etc/fstab.I tried the "Add to Panel" > " Disk Mounter" process but I get a error message "Given UDI is not a mountable volume" Is there any way to get an icon on the desktop when the floppy is mounted and a way to avoid signing in as root for mount and unmount? 
Thanks

---

### Post by GreyFox503 on 2006-01-17
[quote=raul99]Is there any way to get an icon on the desktop when the floppy is mounted and a way to avoid signing in as root for mount and unmount? 
Thanks[/quote] 
See this line from my fstab:

```
/dev/fd0          /media/floppy     auto         noauto,user,sync       0 0
``` 
Notice my options in the fourth column.  Having the "user" option allows regular users to mount the drive without sudo or root access.  Make sure your user option is set, then try to mount as a regular user.

```
mount /dev/fd0
``` or
```
mount /media/floppy
``` should do the trick.

I don't know about that desktop icon, though.  When I mount my from the shell or from the gnome applet, I get an icon.

BTW:  fourchannel's method will work fine, but you will need to type the entire mount line every time you want to use the floppy.

EDIT:

I just came across something in the configuration editor.  Go to Applications > System Tools > Configuration Editor.  Then browse to /apps/nautilus/desktop/volumes_visible and see if it is checked.  This appears to toggle whether desktop icons are shown for mounted volumes.

---

