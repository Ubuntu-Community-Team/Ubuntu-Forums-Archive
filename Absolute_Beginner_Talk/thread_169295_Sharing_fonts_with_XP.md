---
title: "Sharing fonts with XP ?"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by Kopydlow on 2006-05-02
Hey,

I did not found any answers to what I consider being a "beginner problem" using Google or Ubuntu-fr.org forums (I'm French).

Now, I have to install (and delete) fonts twice, in XP's C:\WINDOWS\Fonts and in Ubuntu. I'm sure there's a trick to have only one directory. ;)

First I wanted to have a fonts directory on my FAT32 partition, but here's my new idea :
XP (and most of my nice fonts) is installed on a NTFS partition. Ubuntu can read data on NTFS. Softwares don't modify fonts, they just "read" them. :-k So if I tell Ubuntu to go and find fonts in my NTFS partition, I think I won't have any problem to add or delete fonts anymore. Is this possible ?

Thanks,
Luc.

---

### Post by jazzmuzik on 2006-05-02
While it's probably possible to link to the fonts in the windows partition I've heard that for security reasons this is not be a good idea. Fonts need a 644 permission. But let's see what others have to say about it.

---

### Post by Kopydlow on 2006-05-02
Ok :-| Otherwise I can move both XP fonts and Ubuntu fonts to a directory located on my FAT32 partition linking the fonts to this partition in Ubuntu and, uh, modifying the registery in XP ? Do you know whether I'm going to have the same permission problems doing so ?

Thanks,
Luc.

---

### Post by jazzmuzik on 2006-05-02
fat32 can't store permissions as far as I know. 

If it were me, I would just copy the ttf fonts over to Linux. But then I only copy 20-30 fonts. Some people like tons of fonts, but to me, at least from my windows experience, tons of fonts greatly slows things down. I've helped people speed up their dog-slow Windows computers just by the simple act of removing all but about 30 fonts. They are amazed.

---

### Post by pbaehr on 2006-05-02
I'm not sure about the issue at hand, but no, fat32 can't set permissions. I'm not sure how big a problem that will be regarding fonts, though. I've never tried it.

---

### Post by Kopydlow on 2006-05-02
> **jazzmuzik]Some people like tons of fonts [...][/QUOTE]

Not tons, only dozens!  said:**
> I'm not sure how big a problem that will be regarding fonts, though. I've never tried it.

Ok... :-s Do you know how to link to the fonts in the Windows partition ? I'm going to try and see whether it works or not. *Sacrifice*

Thanks,
Luc.

---

### Post by jazzmuzik on 2006-05-02
Let's see. This is basically the procedure assuming your windows OS partition is hda1:

sudo ln -s /media/hda1/windows/Fonts /usr/share/fonts/linkedtruetypefonts

sudo fc-cache /usr/share/fonts/

Anyway, it works for me. Don't think I would recommend it though.

It occurs to me that you can install fonts in your user directory as well. I think the directory must be ~/.fonts

---

### Post by Kopydlow on 2006-05-02
1. Extend the Windows NT/2000/XP operating system to include the Ext2 file system using [Ext2 IFS for Windows]("http://www.fs-driver.org/index.html").
2. Move your fonts to /usr/share/fonts/.
3. In the Control Panel, install the fonts specifying the new directory (on your Ext2 partition). Disable the "Copy Fonts to Windows Directory" option.

Source: [http://support.microsoft.com/kb/115910/en-us](http://support.microsoft.com/kb/115910/en-us) :D

---

