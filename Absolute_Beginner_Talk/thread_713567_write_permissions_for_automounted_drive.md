---
title: "write permissions for automounted drive"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by lbarnes on 2008-03-02
hey guys, i finally got my second hard drive to automount and now i have no write permissions
i've tried the ntfs configuration tool, but it just lists dev/sda2 which is my windows c drive
the drive i need write permissions for is dev/sdb1 and is in directory /mnt/media
any help would be greatly appreciated

---

### Post by iris-n on 2008-03-02
The best thing to do is to edit the mounting options so it gives you the right permissions automatically, so ```
cat /etc/fstab
``` so we can tell what's wrong.

---

### Post by bschleusner on 2008-03-02
I just cheat and set the read/write permissions for the /media folders to be me instead of root.

---

### Post by LuisGMarine on 2008-03-02
I think the command is:
```

sudo chown -R  username:username /mnt/media
```

obviously substitute username, for your actual user name.

---

### Post by lbarnes on 2008-03-02
> **LuisGMarine said:**
> I think the command is:
```

sudo chown -R  username:username /mnt/media
```

obviously substitute username, for your actual user name.

i feel like an idiot, it's either lennon or lennon barnes
is there a command to show list of users, should be easy i'm the only one
god, i'm an idiot
thanks

---

### Post by lbarnes on 2008-03-02
this is what i get in deluge

torrent paused: disk write error, open failed: '/media/DISK2_VOL1/Ugly Casanova - Live San Francisco 11-23-01 (FLAC)/01 - Barnacles.flac'. Permission denied

this torrent is legal btw

i tried the chown command, but it didn't remove this error
do i need to restart first?

---

### Post by lbarnes on 2008-03-02
ok, now i really feel like an idiot
i forgot to change the save location in deluge
sorry to waste your time
god, someone delete this thread

---

### Post by iris-n on 2008-03-02
type id in your terminal, it gives your username (and a lot more info)
maybe restart deluge, never the system.
the chown command works, but it's not the most elegant solution.

---

