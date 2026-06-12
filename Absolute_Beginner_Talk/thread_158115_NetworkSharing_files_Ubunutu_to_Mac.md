---
title: "Network/Sharing files: Ubunutu to Mac"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by mattothegeek on 2006-04-10
Here's the setup: PC Upstairs with Ubuntu > Airport wireless Network > Imac G5 Downstairs

User: Relative Newby

Desire: to be able to see the drive on the Ubunutu machine from the Imac and to be able to transfer/read/write files on same...

I would assume this is somewhat aking to sharing a drive on a PC but am not totally sure...

Could someone help get me started??  Thanks in advance...

---

### Post by ubernoob on 2006-04-10
i guess mac has support for seeing windows shares, so the easiest way is either ftp or samba.

Here is a guide for samba: [https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

Install and set up samba. Then do:
```
sudo gedit /etc/samba/smb.conf
```

add:
```
# My MP3's
[mp3]
   comment = My MP3's
   writable = no
   path = /data/share/mp3
   public = yes
   security = share
   guest ok = yes

```

if you don't want any password on it. If you want password then you need to see the howto.

Then do:
```
sudo /etc/init.d/samba reload
```

---

