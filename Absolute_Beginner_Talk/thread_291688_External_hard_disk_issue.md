---
title: "External hard disk issue"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by komaroveli on 2006-11-02
hi all,

i have external hard disk where i want to sync my files from computer, so i could keep it as storage utility/backup. i formated it with ext3fs, but now it owned by root.
how can i make it accessible by everyone?
i want to be able to take my external hard disk with me and for example put something on it while away from my computer?
thnx

---

### Post by Jussi Kukkonen on 2006-11-03
Just a note: If you use ext3, you won't be able to read or write to the disk from a random Windows computer. FAT, as lousy as it is, is still the universal filesystem. It doesn't support real file ownership, but if you are going to attach the drive on several computers, you can't keep the ownerships correct anyway. The wiki has howtos to help you if you want to mount the disk as FAT (after formatting it as such of course).)

If you keep using ext3, the permission problem has two solutions, use whichever suits you:

1. change the owner of the files/directories. Example:
If you only want a single user to be able to write to a certain directory, created the dir as root, and change the ownership
```
sudo mkdir /media/path/to/dir
sudo chown username:username /media/path/to/dir
```
That would set *username* as the owner of the dir (with write permissions probably). The default file permissions will leave the files readable by everyone. If this is not what you want, you will need to also...

2. change the directory/file permissions. Example:
```
chmod -R uog+rw /path/to/directory
``` 
That would give file owner (u=user), file group (g) and all other (o) permissions to read(r) and write(w) to the specified directory and everything currently inside the directory (switch -R)

This stuff is mostly possible from nautilus also.

---

### Post by flixer on 2006-11-03
I think you mean fat32.

---

### Post by komaroveli on 2006-11-03
> **flixer said:**
> I think you mean fat32.
no ext3...i have heard all this talk about how fat32 doesn't support files larger then 4Gb. and considering that i sometimes download movies exeeding that amount i have chosen for ext3.
but i didn't realize that ownership problems would be o big and depend on filing system
> **Jussi Kukkonen said:**
> If you keep using ext3, the permission problem has two solutions, use whichever suits you:
i think i go for secondone...unless i get some different advice from ubuntu wiseman

---

### Post by Jussi Kukkonen on 2006-11-03
If you're going to attach the drive to various machines that is probably as good a choice as anything (otherwise I'd recommend using proper file ownerships).

---

### Post by komaroveli on 2006-11-03
> **Jussi Kukkonen said:**
> (otherwise I'd recommend using proper file ownerships).
would you be kind to tell me more about it...or at least where can i find literature on this subject.
thnx

---

### Post by Jussi Kukkonen on 2006-11-03
Well, I meant something like option 1 in my first post: Every file/directory is owned by a real 'owner' who has read/write rights and who decides whether other people have rights to read the file, or write to it... 

This is pretty hard to do if the disk is moved from machine to machine, as there will be different users on different computers. Even if the usernames were the same, they may have different IDs (which are used to map files to owners). I this situation you will end up in problems unless you keep the whole drive world-writable (I can't think of good ways to overcome that anyway).

---

