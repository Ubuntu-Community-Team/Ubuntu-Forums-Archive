---
title: "Linux image download problem!"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by moonliter on 2006-08-12
I cant install any package anymore because i am getting this error:


[CODE]dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `&#65533;G' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `&#65533;G' must be followed by colon[CODE]

Help please?

---

### Post by moonliter on 2006-08-12
CAn anyone help me with this please?

---

### Post by msak007 on 2006-08-12
Try this in the terminal:

```
sudo dpkg --clear-avail
sudo apt-get update
```

---

### Post by moonliter on 2006-08-12
Thanks a lot it works noW!!!

---

### Post by msak007 on 2006-08-12
No problem :). Just an FYI, if you want to include code or output in your posts, make sure you include the / in your closing tag. So in your post above, the second tag should have been [/code], not [code]. Alternatively, you can click on the "Go Advanced" button to go into advanced editing mode, highlight the text you want to include in the code box, and click on the # to automatically append the tags before and after the text.

---

