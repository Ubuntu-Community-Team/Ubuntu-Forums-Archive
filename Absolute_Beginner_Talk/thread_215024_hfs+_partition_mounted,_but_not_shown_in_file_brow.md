---
title: "hfs+ partition mounted, but not shown in file browser"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by silversurfer2025 on 2006-07-13
Hello world,
I just managed to auto-mount (read-only) my hfs+ partition and it all works well through the terminal. E.g. if I enter (in su mode) /mnt/macos (which is where it is mounted) I can acces all the files without a problem.

The thing which is currently not working is the file-browser. If I choose "Places" and then "Computer" I do not see the mounted partition.

How can I get the mounted partition to be visible through the file-browser as well?

Thanks a lot for your help
Timee

---

### Post by Kilz on 2006-07-13
> **silversurfer2025 said:**
> Hello world,
I just managed to auto-mount (read-only) my hfs+ partition and it all works well through the terminal. E.g. if I enter (in su mode) /mnt/macos (which is where it is mounted) I can acces all the files without a problem.

The thing which is currently not working is the file-browser. If I choose "Places" and then "Computer" I do not see the mounted partition.

How can I get the mounted partition to be visible through the file-browser as well?

Thanks a lot for your help
Timee
You should be able to browse to it by clicking on the filesystem icon, then the mount folder, then macos once its mounted. If you want easier access you could change the auto mount to mount the macos folder to your home folder.

---

### Post by silversurfer2025 on 2006-07-13
thanks, I just dragged the macos folder to the left and thus created a link to it for easier access..

Thanks for the tip where to find it...

Timee

---

