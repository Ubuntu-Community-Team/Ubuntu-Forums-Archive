---
title: "Setting permission for Unison sync"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Tamlyn78 on 2008-03-18
Hi, I just moved to Ubuntu from windows and use an iPod (FAT32) to synchronise files between my home and work computers using the Allwaysync software. I am trying to set this up in Ubuntu using Unison. When Unison tries to write to the iPod i get:

Failed to set permissions of file /media/MY IPOD/*filename*

I have tried changing the permission of my ipod using nautilus and logged in as root but no joy. 

I have also tries typing:

sudo chown -R username:username /media/mountpointofthedrive

as suggested in this thread [http://ubuntuforums.org/showthread.php?t=728053]("http://ubuntuforums.org/showthread.php?t=728053")

but my terminal just hangs with this symbol >

I noticed that it also hangs when I type

cd /media/MY IPOD

Could this be because of the space between MY and IPOD? Any suggestions?

---

### Post by glennric on 2008-03-18
Spaces in file and directory names often cause issues in linux.  It is probably a particularly bad idea to have  a mount point have a space in the name.  Although, I don't know that that is what is causing your permissions problem.  It may also be a limitation of the device.

---

### Post by Tamlyn78 on 2008-03-20
Thanks for the tip glennric. I have many files and folders created in windows with spaces so I may have to look into changing them. I didn't end up managing to change the permissions but I figured out a solution anyway. Unison doesn't seem to be able to propagate the permissions (maybe due to the different file systems between my laptop and iPod) so by adding the line

perms = 0

to the profile file (found in the hidden directory /home/.unison/[I]profile name[I])

Unison did not attempt to mirror the permissions and the synchronization succeeded. Brilliant!

---

### Post by Chonnawonga on 2008-04-05
Tamlyn,

That's very helpful. Thank you!

I should point out, though, that the directory is /home/username/.unison and not /home/.unison/username/

---

