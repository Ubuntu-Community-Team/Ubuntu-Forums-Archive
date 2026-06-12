---
title: "Moving files between Ubuntu machines"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by K.Mandla on 2006-03-20
Okay, all I want to do is move several large (300Mb+) files from one Ubuntu machine to another across my wireless network. I can't seem to find the right words to search for. 

I'm used to the whole \\host\sharedfolder thing in Windows.

Could someone please point me in the right direction? Thanks.

---

### Post by andlinux21 on 2006-03-20
Have you tried looking up file server?  You can set one as the host and then just ftp everything you need back and forth between the machines?

---

### Post by halfvolle melk on 2006-03-20
You could use Samba if you have it running already, or set up an FTP server on either computer. You could use NFS:
[https://wiki.ubuntu.com/NFSServerHowTo](https://wiki.ubuntu.com/NFSServerHowTo)

I liked using SSHFS when pushing files around, it's easy:
[http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)

Lots of options.

---

### Post by Kurt` on 2006-03-20
NFS (network file system) is easier to setup than Samba, and should have you copying files in no time.

---

### Post by OffHand on 2006-03-20
FTP is way faster than ssh though. I like it better for big data.

---

### Post by taurus on 2006-03-20
[QUOTE=subsonic_shadow]FTP is way faster than ssh though. I like it better for big data.[/QUOTE]
Yes, ftp (vsftpd) works great and it's much easier to set up than NFS or Samba!
:)

---

### Post by K.Mandla on 2006-03-20
Wow. Is the best way really to set up one as an FTP server? Geez.

Cool! Now I get to learn how to do that! 

Thanks!

---

### Post by pbaehr on 2006-03-20
Well, it is the "File Transfer Protocol" so I guess it makes sense.

---

### Post by MetalMusicAddict on 2006-03-20
My vote is for Samba. Its really not that bad.

---

### Post by Kurt` on 2006-03-20
mount remoteip:/remote/path/ /local/path/ + drag 'n' drop is much easier and faster imo ;)

---

### Post by WoodyMahan on 2006-03-20
Hi all,

I just saw this post as I was looking for a way to move files myself.  I saw the post with vsftpd so I opened Synaptic and searched for it.  It popped up immediately.  I marked and installed it.  Then searched the forum for vsftpd and found instructions for configuring.  This is very simple.  Just open a config file and read the file and it will explain every option and just select YES NO or comment out the line.  Very simple.  I logged onto my windows machine, opened ftp connection to the Ubuntu Machine and it worked!!

I recommend this because it took me all of 20 minutes to find, install, research, configure, and start using.

---

