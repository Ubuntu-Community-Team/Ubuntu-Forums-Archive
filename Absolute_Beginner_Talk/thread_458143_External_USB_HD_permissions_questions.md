---
title: "External USB HD permissions questions"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by r76 on 2007-05-29
Hi, I formatted a new Seagate 500GB USB hard drive with two ext3 partitions using gparted in Feisty.  But I can't write to them.  How can I make it so that users other than root are given access to it?  For example I have myself and mythTV as users on one of my PCs and I want both users to be be able to access the drive.

I looked [here]("https://help.ubuntu.com/community/InstallingANewHardDrive") but chown didn't work until I substituted USERNAME:USERNAME for USERNAME:users.  Even so I guess I can change ownership to only one user by that method.
Is this what I need instead?
sudo chgrp plugdev /media/mynewdrive
sudo chmod g+w /media/mynewdrive

I'm so confused.  Do I really need to create a mount point,set it to automount and set permissions on each computer I use the drive with?

---

### Post by Inxsible on 2007-05-29
you can add both users to the same group. that way all users within tht group can have access.

---

### Post by r76 on 2007-05-29
Oh crap, I knew this was going to be more complicated than plug it in and go :(

I don't really understand that solution, obviously I will need to find out more about what users and groups are.  But I'll need to do this for every PC, right?

---

### Post by george29 on 2007-05-29
if you're not worried about file and folder permissions and all the machines you use can write to FAT32, why not reformat to that filesystem - your external drive should then just plug and play.

---

### Post by Inxsible on 2007-05-29
If you use pmount then external drives will automount :

```

sudo pmount /dev/sdX mynewdrive

```

This will mount it under /media/mynewdrive. and remove the folder when the drive is not connected. This would only be for the mounting of course...not the permissions.

but you can do this to change owner ship after mounting
```

sudo chown you:you /media/mynewdrive

sudo chown mythTV:you /media/mtynewdrive

```

Now you and mythTV are both in the same group i.e. 'you' You can create a new group too if you like

---

### Post by Inxsible on 2007-05-29
Or click System -- > Administration --> Users and Groups

and create or edit users and groups

---

### Post by r76 on 2007-05-30
I get it, thanks.  I thought the permissions would be stored on each drive, not on the PC.  I will print out those instructions and put them on the side of the drive so I can take it with me.

As for the FAT32 - I want to keep some very large files (backup images) and this would not be possible on that filestystem, hence ext3.

Many thanks for the help :D

---

### Post by r76 on 2007-05-31
Well yesterday I used the drive on a Windows XP machine (with the ext2IFS drivers from [http://www.fs-driver.org/](http://www.fs-driver.org/)), and while I was on there I changed the volume labels to seagate1 and seagate2.  I then attached the drive to yet another ubuntu PC (to which it had never been attached before) and the mount points used automatically were seagate1 and seagate2 (instead of disk and disk-1).

Also I didn't seem to have any problem with permissions this time, although my username is identical to that on the first Ubuntu box I used with the drive - whether that affects it I don't know.  Perhaps it's more likely that the permissions used were like they would be for a USB stick because it automounted and I therefore never set the mount points.

So using XP to set the volume labels seems to solve my problem of having to define each mount point with the name I want on every PC, and may (through automounting) avoid permission issues as well?

---

### Post by michwill on 2007-06-01
I'm having a similar problem.  However, I don't wish to wipe the drive.  I've got important information on the partition and it's formatted NTFS.  I can mount/see everything, but I can't share it without it prompting for a password.  What's more, no username/password combination seems to work.

How, exactly, do I go about FORCING a permissions change?  I've tried logging in as root and everything.  Nothing seems to work.  Ideas?

---

