---
title: "Help yet again!"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Zepplinne on 2006-05-21
Can someone tell me how I can give my account access rights/privaleges so I can copy items into a folder?

---

### Post by aysiu on 2006-05-21
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Piggah on 2006-05-21
```
chown [your user] /path to folder
```

Should do the trick. That makes you the owner of the folder.

---

### Post by Zepplinne on 2006-05-21
^ when I do that it says its not allowed to be modified

---

### Post by aysiu on 2006-05-21
You should not be the owner of system files.

That's a quick way to screw up your system.

Read the link I posted earlier.

---

### Post by aktiwers on 2006-05-21
This is what I usually do:

```
sudo nautilus
```

Then go to the folder(CTL + L), and drag the file into it.

---

### Post by rahelvey on 2006-05-21
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)[/QUOTE]

Thank you!

---

