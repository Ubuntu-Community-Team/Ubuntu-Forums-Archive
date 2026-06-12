---
title: "Accessing MP3 files from a Windoews share"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by brooklynlou on 2006-03-09
Laptop OS = Ubuntu

PC OS = Windows XP
 - Drive F = Music

I have managed to mount the drive in Ubuntu and there is now a Music folder on my desktop. When I open the folder I can see, rename, move, copy etc, the mp3 files in that drive.

Unfortunately the music applications do not see that mounted drive.

If I double click on the file, it appears in the playlist window of the associated music player, but it does not play. If I copy the file over to the Ubuntu laptop, it plays fine.

How do I get the Ubuntu laptop to play mp3's stored on the desktop windows PC?

---

### Post by brooklynlou on 2006-03-09
Ok. This is wierd. The drive appears and works fine in the Totem movie player. It just doesnt appear in Beep, Rhythm Box, Mplayer, VLC or XMMS.

---

### Post by rboss on 2006-03-10
Well, it's not so wierd at all.

You don't actually have "mounted" the directory, you have promoted it to GnomeVFS. This works fine as long as the application you are using is GnomeVFS aware. However; neigher BMP, nor vls or any of the other applications you named are GnomeVFS aware. Only Totem is.

You may, however, really mount the windows share though smbmount.

Try this:
mount -t smbfs -o username=[username],password=[secret] //windowshost/sharename /mnt/directory-where-to-mount

This should give you a directory where you can access your mp3 files.
(remember to create the directory first before mounting with mkdir /mnt/directory-where-to-mount).

If you want this automaticly done, you have to add the mount to the /etc/fstab file.

Add a line as following:
//windowshost/sharename /mnt/directory-where-to-mount smbfs username=[username],password=[secret],uid=500,gid=500 0 0

This way the mount should be available at every mount.

You may want to replace [username] and [secret] with the username and password of the windows box. ^^

---

### Post by meborc on 2006-03-10
also some good read about mounting:

[https://wiki.ubuntu.com/AutomaticallyMountPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions)

---

### Post by brooklynlou on 2006-03-10
Thank you both. I will give it a shot tonite and let you know the results :) ....

---

### Post by brooklynlou on 2006-03-10
> **rboss]Well, it's not so wierd at all.

You don't actually have "mounted" the directory, you have promoted it to GnomeVFS. This works fine as long as the application you are using is GnomeVFS aware. However said:**
> ,password=[secret] //windowshost/sharename /mnt/directory-where-to-mount

This should give you a directory where you can access your mp3 files.
(remember to create the directory first before mounting with mkdir /mnt/directory-where-to-mount).

If you want this automaticly done, you have to add the mount to the /etc/fstab file.

Add a line as following:
//windowshost/sharename /mnt/directory-where-to-mount smbfs username=[username],password=[secret],uid=500,gid=500 0 0

This way the mount should be available at every mount.

You may want to replace [username] and [secret] with the username and password of the windows box. ^^

Ok, just so that I have the steps straight (remember this is like day 2 of me using Linux and this command line thing is still borderline hieroglyphics)

WinXP comp name = LOUIS
Network = WORKGROUP
Shared Drive Name = MUSIC


1. Ctr+Alt+F1 (bring up terminal 1)

2. sudo mkdir /media/windows

3. sudo gedit /etc/fstab

4. (Add the following line to fstab:: //louis/music /mnt/windows username=louis,password=[secret],uid=500,gid=500 0 0) 

Question: 
- I take it that the above line is for a NTFS drive?? If not, what would the line be?
- does it matter that the username of my ubunto box is 'Louis", same as the windows box?

5. mount -t smbfs -o username=louis,password=[secret] //louis/music /mnt/windows

Thanks in advance.

---

### Post by GMachine_24 on 2006-03-10
Hi:

My suggestion might be a bit more complicated but it also might be easier in the long run: I have a music server, essentially, that hosts most of my music files. I run the SlimServer software ([www.slimdevices.com](www.slimdevices.com)) on a Linux server (which runs Fedora FC4) and I can play music on any of my home network computers - SlimServer provides streaming mp3 support.

SlimServer is available for MAC, Windows and Linux. It is free - open source software with an active forum section. It will also catalogue all your music as to band or artist name, album title, year, most recent music added to your collection - etc. It's a very useful piece of software and not that hard to configure.

Oh - and you can play the SlimServer music on just about any MP3 player (e.g. WinAmp, XMMS and SlimServer also has a free player called "SoftSqueeze." Music can be played on Linux, Windows or MAC computers.

This solution will not only help you now but in case you expand your network you can play the music on other computers no problem.

Of course in the long run I would advise migrating your music files to a Linux machine for its greater reliability and flexibility.

Hope this helps.

---

### Post by brooklynlou on 2006-03-10
Bump - Is the below correct?

WinXP comp name = LOUIS
Network = WORKGROUP
Shared Drive Name = MUSIC


1. Ctr+Alt+F1 (bring up terminal 1)

2. sudo mkdir /media/windows

3. sudo gedit /etc/fstab

4. (Add the following line to fstab:: //louis/music /mnt/windows username=louis,password=[secret],uid=500,gid=500 0 0)

Question:
- I take it that the above line is for a NTFS drive?? If not, what would the line be?
- does it matter that the username of my ubunto box is 'Louis", same as the windows box?

5. mount -t smbfs -o username=louis,password=[secret] //louis/music /mnt/windows

Thanks in advance.

---

