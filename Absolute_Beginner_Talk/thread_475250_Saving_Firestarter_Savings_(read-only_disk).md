---
title: "Saving Firestarter Savings (read-only disk)"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by smurphv2 on 2007-06-15
Hey all,
    I'm working off the tutorial here: [http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access](http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access)

    and get as far as editing the /etc/firestarter/inbound/setup file. When I try to save it, I get an error that I'm trying to save the file on a read-only disk. This is true even when I sudo gedit /etc/firestarter/inbound/setup. Does anyone know how I can get these settings to actually persist? Thanks for any help that you can provide, and let me know if you need any more info.

---

### Post by plcdfa on 2007-06-16
Strange. Try creating another file in that directory, and please report what happens. (It's quite impossible that your root file system is mounted ro, I think X doesn't even start that way.)

---

### Post by smurphv2 on 2007-06-16
Hey, I've resolved this. Foolishly, I didn't bother checking through the terminal what the permissions of the file were. After a chmod of the file, everything is good. Thanks for the help though.

---

