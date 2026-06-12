---
title: "Can you mount hard drives using live cd?"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-03-02
I was wondering how to mount a hard drive while running off the live cd. Is it automatically done when you boot up, or do you have to use the terminal? If so, what are the commands to do so?

---

### Post by taurus on 2007-03-02
Yes, you have to use a terminal to mount your harddrive, depending what partitions you want to mount.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Shack_ on 2007-03-02
Okay, I did that, and I can see the hard drive, but how do I actually mount and access the files on the drive? I need really specific instructions, sorry.

---

### Post by scxtt on 2007-03-02
sudo mkdir /media/<disk name>
sudo mount /dev/<disk name> /media/<disk name>

<disk name> = hd* or sd*, depends on your hardware (setup)

---

### Post by taurus on 2007-03-02
Well, I am going show you as soon as I know which partition you want to mount but since you wouldn't post that output, here it is then.

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
```

---

### Post by doc_eman on 2007-03-03
open terminal:
1- #sudo mkdir /mnt/YourFileNameHere (this one time only, folder always stays here)
2- #sudo thunar (or your filebrowser name)
3- right clik the yourfoldernamehere and select properties, then permissions and switch all tabs to read-write and close (or apply/close)
4- #sudo mount -v /dev/hda1 /mnt/yourfilenamehere (you said you could see it).
 5- since you set the proper permissions, as regular user you should now be able to read/write to it. Even symlink it to your desktop or where ever.
6- NOTE; only step 4 needs to be done after each reboot.
simplest i could put it... (-v usually takes care of file system types for new users).

---

