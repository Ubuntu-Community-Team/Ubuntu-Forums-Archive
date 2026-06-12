---
title: "sudo nautilus error"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by GStubbs43 on 2006-07-20
Hi, I tried running sudo nautilus and the following came up:
```
(nautilus:31553): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: No such file or directory
Could not create per-user gnome configuration directory `/root/.gnome2/': No such file or directory

```
Does anyone know how to fix this? I don't really know what I did... I used the command, it worked, I closed out of it and now it doesn't work anymore. :(  Thanks!

---

### Post by Kobalt on 2006-07-20
Why did you have to do in nautilus with su permission ? 
Try launching nautilus with gksudo : 
```
gksudo nautilus
```

---

### Post by GStubbs43 on 2006-07-20
```
(nautilus:22850): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: No such file or directory
Could not create per-user gnome configuration directory `/root/.gnome2/': No such file or directory
```
And I also noticed that I can't use sudo at all. Sudo gedit comes up with the same error, and so does synaptic Package Manager

---

### Post by GStubbs43 on 2006-07-20
Okay, it's fixed! I did something in the terminal as suggested in another thread and everything works.

---

### Post by jayemef on 2006-07-20
Post your solution here so others who have the same problem can see what you did.

---

### Post by GStubbs43 on 2006-07-20
> **jayemef said:**
> Post your solution here so others who have the same problem can see what you did.
Woops, Just go into the terminal and type this:
```
sudo mkdir /root
```

And your done and it should work!

---

### Post by dimeotane on 2006-07-23
$gksudo nautilus
doesn't work for me either

$ sudo mkdir /root

doesn't work I get an error
"mkdir: cannot create directory `/root': File exists"

---

