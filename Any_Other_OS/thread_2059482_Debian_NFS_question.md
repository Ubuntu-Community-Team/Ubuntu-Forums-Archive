---
title: "Debian NFS question"
date: 2012-09-18
forum: Any Other OS
---

### Post by Drenriza on 2012-09-18
Hey guys.

I have created a NFS share, for example called /video/Nordic

Inside /Nordic i would have a subfolder called _EN/

So the path is /video/Nordic/_EN/

Here comes the question.

When you create a NFS share, and share it ,) can you make a symbolic link to /video/Nordic/_EN/something.folder

And then on the mounted share is it possible to "see" what the link points at (in this case a folder) instead of the link itself?

My issue is that i see the symlink instead of what it points to when i mount the share on my local machine......

The link is made from /video/folder/metadata1.folder /video/Nordic/_EN/metadata1.folder (on the remote NFS server)

And instead of "seeing" the /video/Nordic/_EN/metadata1.**folder** and it's content i "see" the /video/Nordic/_EN/metadata1.folder(broken reference)

Also my /etc/exports entri looks as follows
/video/Nordic 10.1.42.0/16(rw,sync,insecure)

Hope it makes sense.

Thanks on advance.
Kind regards.

---

### Post by Elfy on 2012-09-18
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by LewisTM on 2012-09-18
A feature of NFS is that the filesystem exported is treated like a local FS on clients. This means that symlinks are not 'translated' or 'followed', they point to someplace on the client side, which is often nowhere unless they were made to be relative and point inside the share itself. That prevents users from making symlinks that would be able to 'peek' elsewhere on the server.

There is a solution however.
1) Create an empty directory called /video/Nordic/_EN/metadata1.folder 
2) For testing, make a bind mount to your target folder
```
sudo mount -o bind /video/folder/metadata1.folder /video/Nordic/_EN/metadata1.folder 
```
You should be able to see the contents of the target mounted in _EN/metadata1.folder
3) Make this permanent with an fstab entry
> /video/folder/metadata1.folder /video/Nordic/_EN/metadata1.folder none bind 0 0 
4) Share BOTH /video/Nordic/_EN and /video/Nordic/_EN/metadata1.folder in /etc/exports and add **nohide** in the exports options.
5) Mount the **parent** /video/Nordic/_EN in your clients. The child metadata1.folder should be visible and contain the right files.

Cheers!

---

### Post by Drenriza on 2012-09-19
Hey Lewis.

Thanks for the suggestion i will definitely look into it :)

Kind regards.

---

### Post by hairfarmer88 on 2013-05-27
I know this is an old thread but it solved my issues sharing out an external USB drive using NFS.  Thanks LewisTM!

---

