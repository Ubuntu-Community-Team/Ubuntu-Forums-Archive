---
title: "newbie help with jungle disk"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-09-21
hello,

i've got jungle disk installed/running, but don't really know what to do next!  i've put two folders on my desk, one is "local_host" and the other is "remote_files".  I've tried to mount remote_files using sudo; it seemed to work but I cannot see what's in the folder, nor drag items on to it.

i also don't know how to access the files once they are uploaded.  i thought the idea of remotely mounting was so that it would show up as a drive on one's desktop; i've apparently done something wrong, because this doesn't seem to be the case.

thanks for any help,
-steve

---

### Post by misteral on 2006-09-24
Steve
Once you have JungleDisk running, you access it through a webdav container. In Konquorer (Sorry, don't know any Gnome replacements), access webdav://localhost:2067 (unles you've changed your port). Then copy between the source directory to the new one.

You can mount the webdav as a directory using davfs (but I'm not entirely certain how)

Hope this helps!

---

### Post by stevieb on 2006-09-24
well, i'm trying to mount it using DAV, but so far i'm not allowed to access the folder.

thanks anyway,

-steve

---

