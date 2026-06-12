---
title: "install w32codecs"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by harys on 2006-04-04
hi, i downloaded w32codecs file on my  usb key. how could i install it to my laptop. the fact is that i'm not allow to use ftp protocol on my university's server connection. all my updates fail because of restrictions on ftp protocol. can i put update on my key and install it on my laptop. thanks for your answer. harys

---

### Post by Pragmatist on 2006-04-04
> hi, i downloaded w32codecs file on my **usb key**. how could i install it to my laptop. the fact is that i'm not allow to use ftp protocol on my university's server connection. **all my updates fail** because of restrictions on ftp protocol. **can i put update on my key** and install it on my laptop. thanks for your answer.

1.) What is a **usb key**
2.) What do you mean by, "**put update on my key"**?

---

### Post by carlosqueso on 2006-04-04
All you need to do to install any .deb file (which I'm assuming is what you downloaded to your usb key) is copy it to your home directory (or somewhere else you will be able to find it) from your usb key, open a terminal and type ```
sudo dpkg -i <name of file>
``` where <name of file> is the name of the file you want to use.  If you are looking for any other packages, [http://packages.ubuntu.com/](http://packages.ubuntu.com/) will be your invaluable resource, although without a direct connection, it'll be a bit of a pain.

---

### Post by ELD on 2006-04-04
[QUOTE=harys]hi, i downloaded w32codecs file on my  usb key. how could i install it to my laptop. the fact is that i'm not allow to use ftp protocol on my university's server connection. all my updates fail because of restrictions on ftp protocol. can i put update on my key and install it on my laptop. thanks for your answer. harys[/QUOTE]

A USB Key is a small portable USB flash memory which you can take around with you, put files on, music etc.

And he means can he put updates on this and then take them off that.

---

### Post by dvarsam on 2006-04-04
If I understand well, you are Surfing on the Net from your Universitie's PCs...

Download your "w32codecs" appropriate ".deb" file & save it on your USB key.

Then go home & install it on your Laptop with:

```
sudo dpkg -i w32codecs.deb
```

Good Luck.

---

