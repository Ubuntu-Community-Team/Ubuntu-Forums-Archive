---
title: "Help with installation of file server"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by helino on 2006-07-12
Hi, I've just started using ubuntu, and I have to say that it's really good. 

Because of this, I want to use xubuntu on my fileserver/bittorrent/printer/PVR machine. The PC has a 500 MHz Celeron, 256 MB SD RAM, and two 120 GB HD, and is currently running XP Home. I have a few question before i install it;

1. This is my biggest concern: 1 HD i full of files, and the other one is empty. I will use the empty one as master, and connect the second one as a slave. Both are formatted by NTFS, will I lose the files on the slave because Linux can't read NTFS?

2. Is it easy (not a nightmare) to a setup a shared printer (Lexmark Z33) in Xubuntu for a total beginner?

3. Is there a built in remote desktop app in Xubuntu (that you're able to connect to by Terminal Server Client?

4. Has anyone tried the IVTV drivers and a Hauppauge PVR-150, in theory it should work, but theory isn't always the same a reality...

5. I want to be able to share my folders on the xubuntu machine without username and password, is that possible?

I know I ask a lot, but I only want to know what I'm getting myself into :)

I'm grateful for any answer, thanks for a great community and OS!

---

### Post by crxyem on 2006-07-12
1. Linux can read NTFS so as long as you don't format or repartition the drive with data on it already it should be preserved

2. Sharing Printers with CUPS works very well. I just set up a
new kubuntu system with a USB HP printer and shared it to another linux box with no problems. 

3. There is a built in remote desktop connect similiar to VNC, you can also use ssh 

4. ? haven't tried

5. for linux-to-linux shares I like NFS, rather easy to setup. for linux-to-windows I like samba and you can configure samba so it doesn't need a login/passwd

---

### Post by helino on 2006-07-12
> **crxyem said:**
> 1. Linux can read NTFS so as long as you don't format or repartition the drive with data on it already it should be preserved


Can Linux write to NTFS as well, I red somewhere on the forum that Linux couldn't write to NTFS? (it could, but people recommended to use FAT32)

BTW, thanks for the fast answer

---

### Post by crxyem on 2006-07-12
you can write to NTFS as well

---

### Post by teet on 2006-07-12
Just thought I would throw my 2 cents in.

First off, I wouldn't bother trying to write to an NTFS partition from linux since it's still experimental at this time and you could end up losing all your stuff.  Linux can read NTFS partitions just fine and can read/write FAT32 (aka VFAT) just fine.

Secondly, if you're wanting to run MythTV, you may not have quite a powerful enough machine.  500 mhz is really borderline in my opinion...but there's only one way to find out.

There is a detailed howto posted on the forum for setting up a PVR150 card.
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)  

-teet

---

### Post by Kilz on 2006-07-12
> **helino said:**
> Hi, I've just started using ubuntu, and I have to say that it's really good. 

Because of this, I want to use xubuntu on my fileserver/bittorrent/printer/PVR machine. The PC has a 500 MHz Celeron, 256 MB SD RAM, and two 120 GB HD, and is currently running XP Home. I have a few question before i install it;

1. This is my biggest concern: 1 HD i full of files, and the other one is empty. I will use the empty one as master, and connect the second one as a slave. Both are formatted by NTFS, will I lose the files on the slave because Linux can't read NTFS?

2. Is it easy (not a nightmare) to a setup a shared printer (Lexmark Z33) in Xubuntu for a total beginner?

3. Is there a built in remote desktop app in Xubuntu (that you're able to connect to by Terminal Server Client?

4. Has anyone tried the IVTV drivers and a Hauppauge PVR-150, in theory it should work, but theory isn't always the same a reality...

5. I want to be able to share my folders on the xubuntu machine without username and password, is that possible?

I know I ask a lot, but I only want to know what I'm getting myself into :)

I'm grateful for any answer, thanks for a great community and OS!
As others havs said, forget about the pvr, especialy if you want it to do the rest.

1. copy the files to the master, format the slave to fat32, put the files back. Linux can read and write to fat32.

2. Lexmark is notorius for the worst printer support for linux of any printer manufacturer. Be prepaired for a problem in case there is one.

5. setup a ftp server. anon ftp or apache and a simple web page.

---

### Post by helino on 2006-07-13
teet: I'm not going to use MythTV, I'm going to use MediaPortal. And I'm only going to use the computer for recording, not live TV, and then 500 MHz would work, specially since PVR-150 use a hardware decoder. 

Kilz:> 1. copy the files to the master, format the slave to fat32, put the files back. Linux can read and write to fat32.
This is what I was thinking, and this is how I'm going to do it. 

Concering the printer, I guess I just have to try...If it's not working, I have to go back to XP

Thanks for all the answers, you really helped med to decide to start this little project.

---

