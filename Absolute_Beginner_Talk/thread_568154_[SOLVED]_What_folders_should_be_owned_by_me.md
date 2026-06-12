---
title: "[SOLVED] What folders should be owned by me?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Bebbe on 2007-10-05
It seems to me that almost all folders on my system are owned by root..shouldn't I own some of them by default? I do not have ownership over the media folder for example. Is this normal or has something gone wrong during install?

It seems terribly time consuming and unnecessary if one has to manually change ownership of each and every folder so I assume that there are other options to fix this, or do I have to reinstall?

Thanks in advance!

---

### Post by cek on 2007-10-05
Actual "owership" of the folder is not really necessary.  The only folder that you need to be owner of is your home folder.

Other folders on your system can be owned by others (root especially) and you can be grated access via group or specific other permissions.

Limiting folder "ownership" to the root account provides a small degree of security.

---

### Post by nvteighen on 2007-10-05
No, leave it all as it is. You own your home folder and that's actually the only you need; also you own some folders at /var but you must not care for them as there are temporary files and folders.

/media is not yours but you also don't need it to be so. If it's a USB or CD-ROM or other removable device, you'll have it mounted automatically. If it's an internal hard drive, you'll need root privileges and then /media should be owned by root (or root should have full access to it) if you're going to mount something there.

---

### Post by Bebbe on 2007-10-05
Thanks for your answers.
I just took over ownership of the media folder, but I guess I should turn it back to root then...But if root owns the folder how can I copy files to the drive. and will I be able to do so from a windows machine on the network?

I should make clear that this is an internal IDE drive added after I had installed Ubuntu...I'm going to add several more drives as this machine is going to be a server and I need to be sure that I can access them from my other windows machines as well as locally.

EDIT: I finally realised that I need to take ownership of the mount points themselves, not the entire /media folder :D

---

### Post by nvteighen on 2007-10-07
Just a note: please mark this thread as solved using the "Thread Tools" menu, so anyone seeking an answer can find it here!

---

