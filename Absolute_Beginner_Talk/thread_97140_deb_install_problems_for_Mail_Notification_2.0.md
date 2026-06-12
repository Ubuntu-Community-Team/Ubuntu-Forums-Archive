---
title: "deb install problems for Mail Notification 2.0"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by cjamesjust on 2005-11-30
I'm fairly new to Ubuntu and have been able to manage most installs with apt-get and synaptic, but the deb files still mess me up.  I've downloaded the Mail Notification 2.0 to my desktop, but now am stuck.  There's reference in some of the text files to an INSTALL file, but there isn't one anywhere in the folders so I'm lost on how and where to install the deb file.  I know I have to dpkg it, but don't know where.  Is there either an INSTALL file that someone has or can someone assist by posting it?

Cheers.

---

### Post by 23meg on 2005-11-30
You have to issue the dpkg command this way:

```
sudo dpkg -i /path/to/deb/file
```

---

### Post by ex` on 2005-11-30
In addition: the INSTALL file is only a textfile containing basic installation instructions.
One you can normally also find on the program's website in the manuals.

---

### Post by 23meg on 2005-11-30
That's not the file you should use; you should use the .deb package.

---

### Post by ex` on 2005-11-30
[QUOTE=23meg]That's not the file you should use; you should use the .deb package.[/QUOTE]
Huh? Did you even read my post?
I said it was a textfile containing basic installation **instructions** (which it is), as that was what the original topicstarter was mainly worried about.
Next to that I said it was in addition to what you said.

:)

---

