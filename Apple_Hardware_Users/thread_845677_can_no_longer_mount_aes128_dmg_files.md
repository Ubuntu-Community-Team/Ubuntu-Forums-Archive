---
title: "can no longer mount aes128 dmg files"
date: 2008-06-30
forum: Apple Hardware Users
---

### Post by fangorious on 2008-06-30
I have an DMG file encrypted with 128 bit AES that I used to be able to mount like this

```

modprobe cryptoloop
mount -t hfsplus -o loop,encryption=aes,keybits=128 file.dmg /mnt

```

But now when I run those commands this error is returned by mount

```

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I've noticed that both leaving off keybits and intentionally providing the wrong password fails the same way. I've also noticed this in /var/log/messages

I can mount the dmg file on my Mac, so I know the image is good. Seems like this just broke in the last week or so.

---

### Post by cyberdork33 on 2008-06-30
what is in dmesg?

---

### Post by fangorious on 2008-07-01
Nothing, but this is in /var/log/syslog and /var/log/messages

> 
Jul  1 10:00:38 basilisk kernel: [  169.247558] hfs: unable to find HFS+ superblock


---

