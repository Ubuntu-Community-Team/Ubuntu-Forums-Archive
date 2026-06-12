---
title: "How to mount Windows partitions (NTFS) on boot-up, and allow users read and write ac"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2006-09-04
I have a few questions before i proseed. You see i have 2 disks from my old days with lots of stuff that iv collected over the years, and the problem is that is ntfs. And after some searching iv found out that this isnt suported in linux generaly. But then i got over this in the Dapper guide. Can anyone tell me how risky this is? since i dont want to loos everything.

How to mount Windows partitions (NTFS) on boot-up, and allow users read and write access

Warning: Ntfs writing support is still experimental. You should not enable it on production machines and/or volumes you don't have backups of. Proceed at your own risk!

    * Read #General Notes 

sudo apt-get install libfuse2 fuse-utils

    * Download the latest ntfsprogs package (these are from the Dapper repositories, so they are safe to install.) 

libntfs8 ntfsprogs libfuse2 fuse-utils

    * Install the downloaded packages 

sudo dpkg -i libfuse2_*.deb fuse-utils_*.deb ntfsprogs_*.deb libntfs8_*.deb

    * Add fuse to the list of modules to load 

echo fuse | sudo tee -a /etc/modules

    * Create a user group to access the ntfs disks 

sudo addgroup ntfs

    * The output should look something like this, remember the GID (the number printed after the group name) as it may differ and we will need it later: 

    Adding group `ntfs' (1002)... 
    Done. 

    * Read #How to list partition tables 

    * Create the local mount folder and edit the fstab file to mount the disks to this folder. 

    e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS) 
    Local mount folder: /media/windows 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

    * Append the following line at the end of file, using the GID number previously. The umask following this GID allows write access just to owner (root) and group (ntfs), and read access to everyone. 

/dev/hda1    /media/windows    ntfs-fuse    auto,gid=1002,umask=0002    0    0

    * Save the edited file. 

    * Add users to the ntfs group, where "username" is the name of the user you would like to have write access 

sudo adduser username ntfs

    * Fix Dapper bug #29865 of the linux-ntfs package: 

sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse

    * If you reboot now, the disk will be writable to the selected users when they logon. If you want the changes to take effect immediately without rebooting, execute the following command, ignoring the errors about "/" and others not being unmounted. You'll have to logout from all your user sessions for the new group to be acknowledged (usually a logout from your graphical session and login back again will do it). 

sudo modprobe fuse && sudo umount -a && sudo mount -a

---

### Post by Seryozha on 2006-09-04
Ive found this [site]("http://www.psychocats.net/ubuntu/mountwindows") helpfull.  I have been able to mount my old partition and read from it.  I haven tried writing.

---

### Post by mattice06082 on 2006-09-16
This worked perfectly!  I had an NTFS formatted drive that I wasn't able to view in my Ubuntu box and now I'm not only able to see it, but write to it.  Thanks so much.

---

### Post by ovidescu on 2006-12-27
I know this is kinda old thread, but, there are two reasons I post here:
1) I kindly ask the Ubuntu forum staff, the admins, to share their opinions about using write access on NTFS partitions. How safe is it and if they've done it.
and 2) Maybe other people using NTFS write access will see this thread and reply also, share their experiences with using write access on NTFS partitions. Has anyone ever lost a windows partition due to write access ? Have they had data loss ? Messed up Windows file system ? you get it

I have a dual boot box, with a 200 GB hdd from which only 20 GB are for my Ubuntu, so having write access on my windows partitions would help a lot.

Hoping to seeing lots of replies.

Ovidiu

---

### Post by brianh57 on 2006-12-27
I don't have a lot of experience with this but I've been told that the big problem with using linux to write to NTFS is that it may appear corrupted to Windows the next time you boot into that.

I have an NTFS hard drive and I'm planning to backup my data after mounting the drive read-only, reformat it for linux, and put my data back just to be sure I don't lose anything to a glitch.

---

### Post by Jussi01 on 2006-12-27
Hei,

Im using [ntfs3g]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs3g") and it works perfectly!! Ive not had a problem with it at all! no data loss, no corrupted files. so it is definately been good for me!!

---

### Post by dannyboy79 on 2006-12-27
> **Jussi01 said:**
> Hei,

Im using [ntfs3g]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs3g") and it works perfectly!! Ive not had a problem with it at all! no data loss, no corrupted files. so it is definately been good for me!!

this how-to doesn't use ntfs3g, just so everyone who reads this comment from jussi01 knows that this how-to uses another method to write to ntfs! I can't speak about it, I only use vfat and ext3 for my linux box. I have a winbloz that has all those drives as ntfs and the most I do is use ftp or samba to copy files over to my winbloz box and they write fine.

---

### Post by bulldog on 2006-12-27
Some time ago,when I was running Fedora,I tried the NTFS writing and lost a data partition.
Not a big deal because I had a backup of the important things.

I will never use it again,mainly because I have nothing to write to a NTFS partition :D

---

### Post by Jussi01 on 2006-12-27
> **dannyboy79 said:**
> this how-to doesn't use ntfs3g, just so everyone who reads this comment from jussi01 knows that this how-to uses another method to write to ntfs! I can't speak about it, I only use vfat and ext3 for my linux box. I have a winbloz that has all those drives as ntfs and the most I do is use ftp or samba to copy files over to my winbloz box and they write fine.

It doesnt?

why the titile "HOWTO: NTFS with read/write support **using the ntfs-3g **(easy & safe method)" then?

---

### Post by dannyboy79 on 2006-12-27
well you're obviously not getting that from the title of this thread! this thread's title reads "How to mount Windows partitions (NTFS) on boot-up, and allow users read and write ac" and nothing about ntfs-3g. Although I do know the thread your referring to. I simply was pointing out that if people come here and read people comments they should make note that you aren't using THIS THREADS how to, you're using the other thread that uses ntfs-3g and NOT NTFS-FUSE like this thread uses.

---

### Post by Jussi01 on 2006-12-27
> **dannyboy79 said:**
> well you're obviously not getting that from the title of this thread! this thread's title reads "How to mount Windows partitions (NTFS) on boot-up, and allow users read and write ac" and nothing about ntfs-3g. Although I do know the thread your referring to. I simply was pointing out that if people come here and read people comments they should make note that you aren't using THIS THREADS how to, you're using the other thread that uses ntfs-3g and NOT NTFS-FUSE like this thread uses.

Ahhh - ok - I did have the link to the other thread there so I thought that was clear. My apologies.

---

### Post by dannyboy79 on 2006-12-27
no problem. i knew what you meant but other newbies might not have.

---

