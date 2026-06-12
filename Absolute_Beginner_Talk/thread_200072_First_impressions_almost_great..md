---
title: "First impressions: almost great."
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by muxecoid on 2006-06-19
My first impression about Ubuntu was fairly good. 
Compared to SuSE:
Did not mess up xconfig monitor modelines like SuSE did.
Ubuntu detected and configure scaner automatically and correctly like SuSE did not.
Works almost fine from LiveDVD.

Compared to ordinary Debian:
Much better hardware detection.
GUI install.

General pros:
Fast decompression, works fast even from liveDVD.

Cons:
Sees my NTFS HDDs but can not mount them (doubleclick in nautiluse causes error)
Did not test it enough to see more cons.

Common cons
Does not include nvidia driver on LiveDVD. 60Hz monitor mode is really painful.
Requires console usage to configure (still much less GUIless config than other distros)

---

### Post by muep on 2006-06-19
For the NTFS partitions:

sudo gedit /etc/fstab

Add a line like the following:

/dev/hda1 /media/hda1 ntfs ro,users,auto,umask=0222,nls=utf8 0 0

or edit an existing line, if there is one for your NTFS partition.

---

### Post by nalmeth on 2006-06-19
Correction, it does included nv driver, the open-source driver. It does not include the proprietary driver for legal + licensing reasons. Ubuntu is a free OS.

If you wanted to go out of your way, you could probably install the nvidia graphically with the nvidia.run installer. Console is just easier and faster.

Let me guess, the error nautilus gave was for permissions?

That's good news about the scanner.

---

### Post by muxecoid on 2006-06-19
OK, but one can always show nvidia license on boot :)
Anyway nv is better than generic used in many other distros, at least it allows you to scroll things fast.

I do not want NTFS in RO. I heard NTFS write driver works fine under Ubuntu. :(

---

### Post by nalmeth on 2006-06-19
This may be sort of what you're looking for:
[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

I think you just 
sudo apt-get install ntfsprog

If you want to risk damaging your NTFS filesystem. I don't think it's totally reliable at this point.

---

### Post by muxecoid on 2006-06-19
[offtopic]Maybe you know any good WinXP drivers for reading and writing ext3 or reiserfs?[/offtopic]

---

### Post by Princey on 2006-06-19
[QUOTE=muxecoid]OK, but one can always show nvidia license on boot :)
Anyway nv is better than generic used in many other distros, at least it allows you to scroll things fast.

I do not want NTFS in RO. I heard NTFS write driver works fine under Ubuntu. :([/QUOTE]

NTFS write support is still experimental unless you want to use some third party programme like Paragon NTFS. If you want to dip your hands in the free open source way, check [this thread]("http://www.ubuntuforums.org/showthread.php?t=142481&highlight=ntfs+write+support") out.

---

### Post by msandersen on 2006-06-20
[QUOTE=muxecoid][offtopic]Maybe you know any good WinXP drivers for reading and writing ext3 or reiserfs?[/offtopic][/QUOTE]
Try [ExtIFS]("http://www.fs-driver.org/"). It's an ext2/3 driver for Windows. Works for me. It's not perfect, there are no Permissions control, and you see all the dot-files as they're not recognised as hidden system files/directories. You should not hibernate one system before opening up the other. Always shut down properly before switching.
You have to use the provided tool to assign a drive letter for it to appear in Windows. So only the partitions you want mounted are available. It's generally a bad idea to mount your Linux Root partition in Windows.

---

