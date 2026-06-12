---
title: "how i can mount my cd roms?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-14
Hi
thank you for reading my post
Can some one please tell me how i can mount my cd roms?
I have done something and now CD-ROMs are gone from media folder.

Thanks

---

### Post by ggaaron on 2007-06-14
```

sudo su
mkdir /media/cdrom
mount /dev/cdrom /media/cdrom

```

You can also place this in /etc/fstab
```

/dev/cdrom        /media/cdrom          auto      auto,user                                                0 0

```

and then

```

mount /media/cdrom

```

But it should mount automatically as  you place cdrom in.

I'm not sure about auto option (the second one) because I don't use it.

---

### Post by legolas_w on 2007-06-15
Thank you for your reply.
Now I found that one of my drives is dvdrw
but i have a problem
```

drwxr-xr-x 11 root root  4096 2007-06-15 10:40 .
drwxr-xr-x 24 root root  4096 2007-05-29 23:34 ..
lrwxrwxrwx  1 root root     6 2007-05-25 12:51 cdrom -> cdrom0


```


how i can delete that cdrom folder?
I delete cdrom0 and now i want to delete cdrom, can you give me some hint?
rd cdrom
del cdrom 
does not works.
thanks

---

### Post by ggaaron on 2007-06-15
Use rmdir or rm.

---

### Post by ggaaron on 2007-06-15
But this isn't your /dev/ folder, because it looks like it... It is made dynamically on boot and most devices are listed many times, like I have sr0,cdrom1 - both being the same cdrom device.

---

