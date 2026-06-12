---
title: "how do i create a symbolic link"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by grimx on 2006-09-11
How do i do this:
 symbolic link to libjavaplugin_oji.so in your Mozilla Plugins directory
 compiled yourself with gcc 2.9x, use the copy located in the plugin/i386/ns7 directory of JRE 5.0

---------------------------------

---

### Post by Tomosaur on 2006-09-11
To create a symbolic link, you must type```
ln -s /path/to/real/file /path/to/non-existant/file
```

---

### Post by fatsheep on 2006-09-11
You can do what he said ^^ or you can do it the graphical way:

Go into your terminal and type:

> 
gksudo nautilus


This starts up a file browser with root permissions.  

Now go to the plugin/i386/ns7 directory of JRE 5.0 and make a copy the symbolic link and then paste it in the Mozilla Plugins directory. :)

---

### Post by grimx on 2006-09-11
hey fatsheep it worked but the site is lagging big time when i load it
i'm using jre1.5.0_06 ..
is this the right version to use with mozilla and or firefox??
i have symbolic links in both of there plugins directorys

---

### Post by caffienda on 2006-11-11
Here is what I'm trying to do.  Copy/extract an Ubuntu server 6.10 install ISO to a USB drive.  

-I mounted the iso at /mnt/isomount/
-I copied the entire directory over $sudo cp -R *
It got through the entirecopy until it hit the Ubuntu symbolic link.  It says operation not permitted.

I tried the 2 above methods and had the sam problem.

I've also tried: sudo cp-d source destination
sudo cp -rRd source destination
sudo -rRp source destination
sudo -Rrdp source destination

all say operation not permitted.  Why would this be?  what is so special about symbolic links?  I'm new to Linux so this is confusing to me. 

Thanks a lot!

---

### Post by tuxcantfly on 2006-11-11
of course, because your usb drive is formated as FAT32. FAT32 doesn't support symlinks.

---

### Post by tuxcantfly on 2006-11-11
you could always format your usb drive as ext2 to store the symlink, but then you'll have issues with exchanging it with windows and mac people, because windows people will need the ext2 ifs: [http://fs-driver.org/](http://fs-driver.org/) to use it, and I don't think mac osx doesn't supports ext2

---

### Post by caffienda on 2006-11-11
It is Fat16 (as syslinux said it should be).. I have no problem re-doing the whole thing, it's a good exercise!  It states to use FAT16!  

I want to get this working, so will it work with an ext3 partition?  

The USB drive is going to be used for booting and then installing from there.

---

### Post by tuxcantfly on 2006-11-14
yes, ext3, ext2, and reiserfs will work for storing symlinks. just don't use fat or ntfs.

---

### Post by cb474 on 2007-05-01
I really want to make links/shortcuts to files I have on a partition shared with my Windows install (which is Fat32). Is there really no way to do this? I mean, shortcuts to this partition work fine within Windows.

---

### Post by DMcA on 2007-05-08
> I really want to make links/shortcuts to files I have on a partition shared with my Windows install (which is Fat32). Is there really no way to do this? I mean, shortcuts to this partition work fine within Windows.

As far as I'm aware, this works fine, so long as the symlink itself is not on a Fat32 partition. The file/folder that is targetted by the symlink can be.

---

### Post by Kenobi on 2007-08-27
Windows-like shortcuts are no problem - rightclick your desktop, then click on "create starter" (I think they call it like this in the English version) and fill in all the details like you would do in Windows. This "starter" can be moved in whatever fat or ntfs directory you would like it to be and performs like a Windows' shortcut.

However, this kind of "shortcut" works fine if you want to use it for personal pleasure, it won't work for system programs that "need" symbolic links because they can't interprete starters.

---

### Post by Onderhil on 2008-01-15
As  my Ubuntu is on /dev/hdb and my XP on /dev/hda I have to type a lot to get at XP files.

If I want to shorten the typing of these used NTFS files and dirs (I am migrating, you know :) ) can I use **ln** too?

Like, instead of typing
```
/dev/hda1/Audio/iTunes/myCollection/ 
```
(a WinNTFS directory) I just type
```
/iTunes/ 
```
after I did something like
```
ln -s /dev/hda1/Audio/iTunes/myCollection/ /iTunes/ 
```

And where do I have to put the symlink in order to see and use it from everywhere? At /root or what?
-
And if two users share the same Amarok, but with slightly different layout (but the same music collection, covers and mood-files) what symlink do I construct and where do I put it such that there is only one set of these files around?

-thanks, mark

---

### Post by Kenobi on 2008-01-18
Hi, Mark,

at first what you do should work perfectly. the "destination" of you link ( dev/hda/...) is up to you and looks quite right.

But the link name has to be in a folder where you have write access to as Linux saves the link like a file. For your purpose (I think you want to get to itunes right by typing "/itunes/") that would mean that the link would be stored right in the file system folder ("/"). OOOOOK you can do that but at first, use "sudo" (or open a root terminal) to become root rights, and then create the symbolic link using ls -s and so on.  When you are successful, you will be able to use the link as normal user and also see it in nautilus, as if there was a folder "itunes" right beneath the other folders (bin, home, sbin...)

please tell me if it worked for you :)

---

### Post by Onderhil on 2008-01-20
Hi Kenobi,
Did it, and it works! Thanks!  I'm going to use a lot of these symlinks now, minimising the typing and tabbing.
-mark

---

