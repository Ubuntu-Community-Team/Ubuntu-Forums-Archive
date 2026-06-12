---
title: "Problems with new harddrive/partition"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2006-09-23
Since there wasnt any good way to get write permission to an NTFS disk, i bought a new disk instead. And now iv formated it to ex3 and copied over all the files and folder from the old disk to the new one. But now i have the problem that i dont have write permission to those files/folders. How can i fix this? Iv tried using "sudo nautilus" and changed it but when i go into another folder/directory everything in it has the same problem with write permission.

So is the only way to do this, to change the permission to everything with "nautilus"? Wich will take ages.... Anyone that has a handy command to use?

Iv tried searching the net for any good answers but with no result. Probably just typing the wrong search word.

---

### Post by U5tabil on 2006-09-23
No one knows what to do?

---

### Post by U5tabil on 2006-09-23
Ok i got it now.

To make you the owner
sudo chown username:usergroup /where/i/want/to/be/writable

To make you the write access
sudo chmod 777 -R /where/i/want/to/be/writable

777 for the permission
-R for making all subfolders/files writable

Hopfully someone will make advantage of it.

---

