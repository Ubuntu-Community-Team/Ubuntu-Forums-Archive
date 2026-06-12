---
title: "my ubuntu was working fine and today it is saying Error: Kernel Map_Protect"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by blacksheep.baba on 2008-03-21
So it starts loading and after some time shows that file system has error  and  tries to recover it and fails.
Then it says provide the root password for maintenance or press Control-D

if the root password is provided it gives a prompt that has a Backup and a Desktop folder.

From there I have nowhere to go.

If pressed Control-D it gives a weired page that says contact your System Admin and more...
It also says failed to start X

How can I restore my system?

I use Gutsy Gibbon.
My hardware is an acer TravelMate 4010

---

### Post by philinux on 2008-03-21
You could run fsck from the recovey mode. fsck is the file system check like chkdsk in winblows.

Press esc when grub appears then select recovery mode. At the prompt use fsck -v

See if it can fix any errors. It might say something like repair bad block etc y/n etc.

---

### Post by blacksheep.baba on 2008-03-21
after running fsck -v manually, meaning the system was trying to run it and getting terminated, fixed a lot of orphans. rebooted, the system said "You home directory does not appear to exist.

logged in as failsafe mode, same problem and hint was your system might be out of space.

logged in failsafe prompt, removed some directories and rebooted.

It worked.

Thanks for the support, pleasant experience as always.

Ahmed

---

### Post by philinux on 2008-03-21
Ok good job.

Have a look in System>Admin>System Monitor and click the File system tab. Should give you a cleare picture of whats going on.

---

