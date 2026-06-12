---
title: "Command Line: copy file to thumb drive"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by meyergary on 2007-07-31
Hi,

I need to use cp to copy a file from the filesystem to a lexar thumbdrive.  

Like:

cp /etc/network/interfaces  ???what goes in destination???

I know I could use the gui to copy the file, but I need to copy this
file eventually to another machine where gui isn't working.

Thanks

---

### Post by aysiu on 2007-07-31
Where is the Lexar thumbdrive mounted? Can you post the output of this command? ```
df -h
```

---

### Post by LaRoza on 2007-07-31
```
copy <location> <destination>
```

Flash drives are typically mounted on ```
/media/<name>
``` where <name> is the name of the drive. They also have names like a hard drive /dev/sdb1, if you have one hard drive and one flash drive.

---

### Post by meyergary on 2007-07-31
df -h shows it's mounted on media/lexar media.

I guess it's the space in lexar media that's giving me the trouble,

cp /etc/network/interfaces "/media/lexar media" doesn't work.

---

### Post by LaRoza on 2007-07-31
Rename it to get rid of the space.

---

### Post by asmoore82 on 2007-07-31
:KS the TAB key is your best friend :KS

```
~ $ cd /etc/network/interfaces /media/Lexar*<whatever it's called like magic>*
```

Keystrokes:<C><D><Space><Slash><E>**<Tab>**<N><E><T><W>**<Tab>**<I><N>**<Tab>**<Slash><M><E>**<Tab>**<L>**<Tab>**

---

### Post by HermanAB on 2007-07-31
You have to 'escape' spaces using the backslash character, turning them into "backslash space".

In general, as you have now found, do not use delimeters in names.  This kind of head-ache is best avoided.  Portable POSIX names consists of "[a-z], [A-Z], [0-9], ".", "_" and "-" (and may only start with an alpha-character), but beware of the period and underscore as well, since periods are frowned upon by some GNU utilities and underscores are not allowed in domain names.

Cheers,

Herman

---

### Post by aysiu on 2007-07-31
Or you can do ```
cp /etc/network/interfaces /media/lexar\ media
```

---

### Post by meyergary on 2007-07-31
Thanks.  I'd forgotten how to escape the space.

---

