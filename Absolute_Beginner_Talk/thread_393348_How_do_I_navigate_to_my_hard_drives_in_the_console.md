---
title: "How do I navigate to my hard drives in the console?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by toecutter on 2007-03-25
I have to change the permissions on one of my partitions so I can copy music files from some backup DVDs. There doesn't seem to be a way to change permissions in the GUI, so I have to do this through the console, but I can't figure out how to CHMOD my partitions. 

Anyone have a clue?

---

### Post by d3r1v3d on 2007-03-25
First thing you need to do is figure out what the name of the partition is (if you don't know already). *gparted* is a great graphical tool you can use to figure this out. Generally, it should be **hd*X***, where ***X*** is some variable letter. Although, it might be **sd*X*** if you're using SATA drives instead of IDE.

Once you have the name of the partition, you can mount it using the (aptly-named) *mount* program in the terminal. Try running a *man mount* to learn more about it. What you'll want to do is create a directory in */mnt* for the partition you're going to mount. After figuring out the name of your partition, run *mount /dev/hd**X** /mnt/**name_partition_dir***. (where ***name_partition_dir*** is the name of the directory you created in */mnt*)

Keep in mind, you'll need root permissions to create a directory in */mnt* and mount the partition there, so you might need to prepend *sudo* to all these commands if it gives you flack about not having adequate permissions. Once you've mounted the partition, you can change the permissions on the mounted directory using the *chmod* command and giving users 'write' permission.

---

### Post by annda on 2007-03-25
you can also run nautilus with root privileges from the terminal with the following command:

gksudo nautilus

---

### Post by toecutter on 2007-03-27
OK :)

'hda8' is the name of the big partition where I want to copy my MP3 dvd data discs to. There's an icon for it on my desktop (put there after I nuked & partitioned the drive, and installed Ubuntu), but when I open it I can't drag and drop anything to it, it just says I don't have permission for '/media/hda8' 

I tried doing the mount command in terminal, using the code 'sudo mount /dev/hdX /mnt/hda8', found out I had to create the directory, couldn't get that to work (forget what the error was now) so I tried Nautilus.

...and I got this error:

> (nautilus:6221): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:6221): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

No idea what that means but Nautilus started and I was able to navigate around the file system and use the GUI to alter permissions. (FINALLY!! :)) 

I also realized that the '/media/hda8' meant that the drives I wanted to access and backup, etc., were already mounted in the /media folder (duh) so I changed the permissions on the one that I need to copy the MP3 backups to, and I'm transferring files as I type this :D so...big 'yay', thanks you guys! Terrific stuff. I also changed the emblem and renamed the drive so it's a bit more memorable.


**My only question now is how can I make a link on the desktop to the 'hda8' partition?** Even in Nautilus I can't just drag it on there or make a link and drag *that* to the desktop.

---

### Post by x1a4 on 2007-03-27
> **toecutter said:**
> 
*<snip>*

**My only question now is how can I make a link on the desktop to the 'hda8' partition?** Even in Nautilus I can't just drag it on there or make a link and drag *that* to the desktop.

*ln -s /path/to/target /path/to/linkname*

---

### Post by toecutter on 2007-03-27
Excellent, thanks! :) I also found out how to do it in Nautilus (right-click on the drive, make a link, change permissions on the folder containing the link, then I could move the link to the desktop)

---

