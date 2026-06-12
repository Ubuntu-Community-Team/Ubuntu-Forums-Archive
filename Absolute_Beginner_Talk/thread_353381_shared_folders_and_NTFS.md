---
title: "shared folders and NTFS"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-02-04
I want to use ubuntu as my home file server (the desktop version, since I only have 2 users). I want to be able to share certain files and USB hard drives from the file server to my WinXp computers. All the hard drives are formated as NTFS, will I have any problems with being able to share these drives over the network and being able to read/write from my windows computers.

---

### Post by amohanty on 2007-02-04
Sharing will be fine as long as its read only. I am not quite sure of the state of the art, but I believe that writes to an NTFS mount is not yet in a stable state. So I would suggest that you format them as XFS (for large disks) or any other format and then use samba to share them to windows machines.

HTH
AM

---

### Post by Falcorian on 2007-02-04
I'm no expert at Samba (which is what you'll probably want to use), but my understanding is that the OS has to be able to read the drive, but the computers connecting don't have to be able to.

So while your Windows boxes can read NTFS, you server can and so Samba will not work (well... you should be able to read the files, but not write). However, you could format Ext3 or XFS or some other filesystem, and your server would read it fine, and Samba would "translate" for the Windows boxes.


Hope I got that right. ;)

---

### Post by Acglaphotis on 2007-02-04
You wont be able to write on the NTFS hard drive (You can read, and copy files TO ubuntu, but not FROM ubuntu), however, there is a beta program that lets you, but i heard its a bit unstable, if you wanna try it, here is the link to the post:

 [NTFS-3G](http://ubuntuforums.org/showthread.php?t=217009)

-Acglaphotis

---

### Post by Falcorian on 2007-02-04
> **Acglaphotis said:**
> You wont be able to write on the NTFS hard drive (You can read, and copy files TO ubuntu, but not FROM ubuntu), however, there is a beta program that lets you, but i heard its a bit unstable, if you wanna try it, here is the link to the post:

 [NTFS-3G](http://ubuntuforums.org/showthread.php?t=217009)

-Acglaphotis

I had to set up a Samba share about a week ago, and from the postings I found it  can give some errors with Samba.

Give it a shot, but the best solution is probably reformat.

---

