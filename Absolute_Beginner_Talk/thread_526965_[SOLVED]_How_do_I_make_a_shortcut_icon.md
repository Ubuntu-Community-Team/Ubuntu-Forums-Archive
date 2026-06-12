---
title: "[SOLVED] How do I make a shortcut icon?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-08-16
Hi everyone,

I've been asking a lot of questions since joining, I hope you all don't mind.

I want to create an icon on my desktop to run the following command - is that possible? Saves me typing the command everytime I want to access my encrypted USB device.

Thanks
```

sudo truecrypt /media/sdd5/media /media/tc1 --filesystem ntfs-3g -M "rw,gid=users,umask=0000"
```

---

### Post by AlexenderReez on 2007-08-16
> **keymoo said:**
> Hi everyone,

I've been asking a lot of questions since joining, I hope you all don't mind.

I want to create an icon on my desktop to run the following command - is that possible? Saves me typing the command everytime I want to access my encrypted USB device.

Thanks
```

sudo truecrypt /media/sdd5/media /media/tc1 --filesystem ntfs-3g -M "rw,gid=users,umask=0000"
```

i never try it..but....it is better to use gksudo instead of sudo for that kind of situation....

---

### Post by keymoo on 2007-08-16
> **AlexenderReez said:**
> i never try it..but....it is better to use gksudo instead of sudo for that kind of situation....

How do I do that?

Thanks

---

### Post by walkerk on 2007-08-16
Right click your panel > Add to Panel > Custom Launcher...

Name: YourScript
command: gksudo truecrypt /media/sdd5/media /media/tc1 --filesystem ntfs-3g -M "rw,gid=users,umask=0000"

That should do the trick. You can also assign an icon to the launcher.


if for some reason that doesn't work you can make a small script and call it with the launcher:

```
gedit ~/.truecrypt.sh
```

now insert the command into truecrypt.sh:
```
gksudo truecrypt /media/sdd5/media /media/tc1 --filesystem ntfs-3g -M "rw,gid=users,umask=0000"
```

now make it executable:
```
chmod +x ~/.truecrypt.sh
```

Now create the launcher like above..

Name: whatever
Command: ~/.truecrypt.sh

---

### Post by anaconda on 2007-08-16
Yep..
And if you want the launcher to the desktop instead of the panel.

Just right-click to the desktop and do the same.

---

### Post by keymoo on 2007-08-16
Thanks for the replies, very helpful.

---

