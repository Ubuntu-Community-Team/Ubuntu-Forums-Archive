---
title: "[SOLVED] mounting directories with fuse"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-10-22
I'm having a bit of trouble using the sshfs.  Here is the command that I am using:

sshfs -o allow_other  usr@host:/myhomedir  /media/remote

However, if I don't run this command with sudo, I get an error saying that I do not have access to write to /media/remote. 

This doesn't make sense though. If insert a flash disk, it gets mounted to the /media directory but I have access to it, and I can unmount it as well.

How can I get sshfs to do the same sort of thing?

---

### Post by Hospadar on 2007-10-22
what exactly are you trying to do? are you trying to mount a remote ssh filesystem to your local machine?

---

### Post by noorez on 2007-10-22
Yes. I'm trying to mount a remote ssh directory into my local machine.

---

### Post by Insightfill on 2007-10-23
I think when you insert the flash disk, the system is using root to do the mount for you, but giving everyone on the system read/write privileges automatically.

If you want to make such a mount, but don't want sudo to do it, do you need to do it at /media/remote?  Make a directory for just yourself (~/media/remote) and mount THAT instead:

sshfs -o allow_other usr@host:/myhomedir ~/media/remote

Alternatively, change the ownership (CHOWN) of /media/remote and try without sudo.

---

