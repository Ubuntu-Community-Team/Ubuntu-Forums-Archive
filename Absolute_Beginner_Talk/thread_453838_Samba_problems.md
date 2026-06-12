---
title: "Samba problems"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by barbz127 on 2007-05-24
Hi all

Im trying to transfer some files 4.7gb from my windows box to my ubuntu 7.04 box.

Im using samba and going from ntfs to fat32.

It just drops out when it has about 1 minute to go and it only transfers 4.1gb.

I get an error saying the network location is no longer available.

Please help me - this is very frustrating!

Thanks
Paul

---

### Post by Hobo Joe on 2007-05-24
Try doing it in smaller bits, like, don't transfer all at the same time, and see if it works.

---

### Post by barbz127 on 2007-05-24
That works.

Still cant copy across a dvd image as one file which is how they are all stored.

Paul

---

### Post by NT4usB on 2007-05-24
Are you entering a username/password when you make the connection?
My Samba shares ask for a login then puke after a few minutes and ask again.
I'm sure there's a way to get Samba to retain the info longer but I don't know it.

---

### Post by barbz127 on 2007-05-24
tried mapping a drive and telling it to save the password but didnt make a difference.

installed an ftp server and have similar issues - could it be fat32?

Paul

---

### Post by qpieus on 2007-05-24
This is not a samba problem at all. The problem is that you are copying to a fat32 partition and in fat32 the largest filesize that is supported is 4 GB. There is no way to make that fat32 partition accept the 4.7 GB file. The linux ext3 filesystem can handle a 4.7 GB file just fine though, so if you can, make room for it on a ext3 partition on your linux pc, then the transfer will work just fine.

---

