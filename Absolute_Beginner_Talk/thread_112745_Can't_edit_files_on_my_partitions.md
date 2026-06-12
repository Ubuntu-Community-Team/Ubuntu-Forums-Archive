---
title: "Can't edit files on my partitions?"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by diggs on 2006-01-05
So I have a bunch of files on my partitions, which are mounted. all are fat32. I want to be able to edit, delete, muck about with and so on with these files, as one would expect you could. However whenever I attempt to do this, I get all kinds of error messages. Why is this and how can I eliminate this? Thanks!

---

### Post by Omnios on 2006-01-05
Exactly what errors are you getting, are they permition errors and how do you have the drives mounted?

---

### Post by diggs on 2006-01-05
"/media/hda...44nas.pdf" cannot be deleted because you do not have permissions to modify its parent folder.

I have an XP dual boot setup, I set up all the partitions in XP, all fat 32. mounted? There's shortcuts on the desktop. that's all I can tell you!

---

### Post by Omnios on 2006-01-05
Im geussing that it may be the way you mounted them.

This is the Unofficial Ubuntu users guide from 5.04 but the mounting is still aplicable. This is the standard way to mount a vfat drive. The fstab part automounts your drive on start up.

 [http://ubuntuguide.org/#windows]("http://ubuntuguide.org/#windows")

 personaly I use 

 ```
/dev/hda2       /media/vfat     vfat    rw,users,gid=users,umask=000,       0       0
``` 
 in fstab as it shows my drive in the menu as well as in the file manager to save files etc.

 the "media/vfat" part  is the directory you mount your drive to which may be differnet.

 ALso this there is a page that explains fstab and how it works.

[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by diggs on 2006-01-05
All the partitions were there when I set up ubuntu. hda1,5,6,7,8,9 are all partitions of my 250gb drive. In regards to your post, I must say I have no idea what you are talking about :(

---

### Post by Omnios on 2006-01-05
K fstab is the file containing the information that mounts the drives on start up. You have a permition problem which is probably caused by the way the drive is moutned. There are many posts recently on the forum about mounting window drives and similar problems. You can do a forum search and read them if you wish.

---

### Post by diggs on 2006-01-05
ahhhh it all makes sense now. now I can edit my multitude of partitions! hooray!
...except for one folder that has a lock on it :S why is this??

---

### Post by Omnios on 2006-01-05
it might have a read only permition in windows that I think locks it or makes it root or something. Try right clicking it in wondows and see if it is read only

---

### Post by diggs on 2006-01-05
Nope, it isn't. I'll just do some fancy copy, paste and deleting in windows to sort the issue out. thanks again!

---

### Post by Omnios on 2006-01-05
Another thing you can try is to change the permitions for the folder with chmod  which changes the permitions of a file in terminal.

---

