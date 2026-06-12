---
title: "NTFS-partions will not stay mounted."
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Magrioteli on 2006-03-23
My NTFS-partions will not stay mounted. :evil: 

Sigh, I know that this issue about mounting has been up umptten times.
And I read about it, but it won't stick! 
I have two NTFS-partitions that I want to have access to. 
One is named /dev/hde1 ~ 7,5 GB
and the other /dev/hde2 ~ 105 GB

Here is the things I do: 

I've opened my root terminal and made a directory named *privat*, in the root – I want to mount my **large** NTFS partition there, which contents music, film, photos and stuff I've written. 

After creating the dir I wrote:
sudo mount /dev/hde2 /privat/ -t ntfs -o umask=0222 (by the book)

I could see the NTFS partiton in the manager, but I couldn't open the folders. I was locked out. 
After re-doing it, I could open and get access but when shut down the computer, and got back again. It was all vanished. 

Has it something to do with these codes, as in 1000 for me as the admin in Ubuntu? Or do I have to use the exact terms* /media/windows. *

Yeah I know – I'm a rookie and I do apologize if this issue allready is answered somewhere. 

It's late and I am tired but I won't give in. ](*,) 

Anyone – please?

---

### Post by NeghVar on 2006-03-23
I think you are looking for auto-mount.

[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

Scroll down a bit and it will tell you about editing fstab.

[http://www.tuxfiles.org/linuxhelp/fstab.html#what](http://www.tuxfiles.org/linuxhelp/fstab.html#what)

That second link will explain fstab and what all those fun little options mean.

Hope that helps

---

### Post by Magrioteli on 2006-03-23
[QUOTE=NeghVar]I think you are looking for auto-mount. 

- - - Hope that helps[/QUOTE]

Yeah!  That looked different from the very start. I didn't realize how important that *media-directory* was.
Now I can find these two partitions when opening the menu. 

I hope that'll stick from now on.

This forum is as fast as lightning.

Thanks a lot!

---

### Post by Magrioteli on 2006-03-24
*Guess, who's back – back again....*

Nope! 

After turning off the pc overnight, the two NTFS-partitions aren't anywhere to be seen.
In System/Administation/Disks these two NTFS-partitions are marked as Inaccessible, and the path is "none". 

I wrote:
sudo mount /dev/hde1 /media/bf2 -t ntfs -o nls=utf8,umask=0222 
(where bf2 is the folder for Battlefield2)
I wrote the same command for the other partion - except antoher folder name and "hde2" for its address. (I better to explain than leave some detalis out) ;) 

**Or did I missunderstand **it all? Are these commands just to give access to NTFS's when the computer is on? (and to kill when shut off?)
The command:
*/dev/hda1       /media/partitionname  ntfs    nls=utf8,umask=0222 0       0*
which says:
"To automatically mount partitions at boot-up, edit the file /etc/fstab and add the following line for each NTFS partitionis" if editing /etc/fstab/ will it make my NTFS's accessible 24/7?

Be patience with me - I am dull - and you all are my lifline.

Sincerely
Don Magrioteli 8)

---

### Post by trent dillman on 2006-03-24
/etc/fstab is the file that lists what is mounted at startup (although you can add 'noauto' so they don't), so adding 
```

/dev/hda1 /media/partitionname ntfs nls=utf8,umask=0222 0 0

```
should do it!

---

### Post by Sutekh on 2006-03-24
Yes you are correct, mount is a temporary mounting, editing the /etc/fstab is an automatic mounting.

If you use the ```
sudo mount /dev/hde1 /media/bf2 -t ntfs -o nls=utf8,umask=0222
```
Then that partition is only mounted for that particular session.  If you reboot/turn off the PC it won't be mounted anymore.

To make it an automatic mount, backup and edit the /etc/fstab with this command
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
Then add this line
```
/dev/hde1   /media/bf2   ntfs   nls=utf8,umask=0222   0   0
```Save (Ctrl+O) and exit (Ctrl+X)

Then use this command to remount the partitions, without needing to reboot
```
sudo mount -a
```

---

### Post by Magrioteli on 2006-03-24
[QUOTE=Sutekh]Yes you are correct, mount is a temporary mounting, editing the /etc/fstab is an automatic mounting.
- - -

To make it an automatic mount, backup and edit the /etc/fstab with this command
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
Then add this line
- - -

Then use this command to remount the partitions, without needing to reboot
```
sudo mount -a
```[/QUOTE]

Weeii! :D 

It worked! Just to be sure I restarted the computer, after writing all that pedagogical information you gave. And my two NTFS partitions were there. On the desktop. What a joy!

Thanks a lot!

---

