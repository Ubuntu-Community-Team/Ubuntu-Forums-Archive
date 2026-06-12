---
title: "[SOLVED] Sansa e260 mount in MSC mode"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by prophetkinggov on 2008-02-13
So I can mount this, and see what's on it-- but apparently, 7.04 has set the owner as root, not my log on. How do I mount this lovely in MSC mode so I can write to it?

---

### Post by Origin415 on 2008-02-13
Try changing the owner

```
sudo chown -R *user* /media/SANSA\ E200P/*
```
(atleast that is the directory Gnome mounts my e280, make sure of that)

---

### Post by prophetkinggov on 2008-02-13
```
sudo chown -R *user* /media/ninja/*
```
with user being my login, of course... Gets me this:

```
 chown: changing ownership of `/media/ninja/MUSIC': Operation not permitted
chown: changing ownership of `/media/ninja/PHOTO': Operation not permitted
chown: changing ownership of `/media/ninja/PICTURES': Operation not permitted
chown: changing ownership of `/media/ninja/PLAYLISTS/Go List.plp': Operation not permitted
chown: changing ownership of `/media/ninja/PLAYLISTS': Operation not permitted
chown: changing ownership of `/media/ninja/RECORD/VOICE': Operation not permitted
chown: changing ownership of `/media/ninja/RECORD/FM': Operation not permitted
chown: changing ownership of `/media/ninja/RECORD': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/WMDRMPD': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000.DAT': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_@DEV.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_FPTH.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_FNAM.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_FRMT.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_MTPF.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_TPE1.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_TALB.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_TCON.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_TIT2.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_RATG.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_MODF.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_PCNT.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_MGEN.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000_BUYF.IDX': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA/PP5000.HDR': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM/DATA': Operation not permitted
chown: changing ownership of `/media/ninja/SYSTEM': Operation not permitted
chown: changing ownership of `/media/ninja/tmp': Operation not permitted
chown: changing ownership of `/media/ninja/version.sdk': Operation not permitted
chown: changing ownership of `/media/ninja/VERSION.TXT': Operation not permitted
chown: changing ownership of `/media/ninja/VIDEO': Operation not permitted
```

Thoughts.

---

### Post by Origin415 on 2008-02-13
Are you mounting it manually or is Gnome mounting it?

I'm not at my home computer right now so I can't tell you exactly what I did, but you could also try 
```
chmod -R 777 /media/ninja/*
```

---

### Post by prophetkinggov on 2008-02-13
> **Origin415 said:**
> Are you mounting it manually or is Gnome mounting it?

I'm not at my home computer right now so I can't tell you exactly what I did, but you could also try 
```
chmod -R 777 /media/ninja/*
```

Manually. Using the number (I understand the concept from the docs for chmod, but they confuse me, I'll admit) gives the same error.  If I do that as root, (ie, sudo) it seems to read it as "make root the owner".

---

### Post by Origin415 on 2008-02-14
Then try using Gnome to mount it. Either have it automount, which you can set in Preferences -> Removable Drives and Media or the command (run as your normal user)
```
gnome-mount -d /dev/*device*
```

I never understood the chmod numbers for a long time too, it works using a three digit binary number. The first digit is a 1 for read privileges, 0 for not, the second the same for write and the last for execute. Then convert that number to decimal, and it will be a unique number from 0-7. The first of these numbers is for the user, then the group, then the rest.

More simply:
Start with 4 for read privileges, 0 for not.
Add 2 for write, 0 for not.
Add 1 for execute, 0 for not.

So 755 (the most common) is full for the user, and read/execute for the rest.

Hope that helps.

---

### Post by prophetkinggov on 2008-02-14
Well, interesting; it was on automount. It looks like, if I read this fstab line right, it was trying to mount my cd rw drive on the same dev/ point as the usb or mistook the player as a USB CD rom (possibly from attempting to plug it in as an MTP?}

```
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

sdc1 is were the player's appearing. I'll comment that out, report back.

---

### Post by prophetkinggov on 2008-02-14
That did it. Apparently it was trying to read it as a cd rom device...

---

