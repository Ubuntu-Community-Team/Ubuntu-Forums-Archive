---
title: "[SOLVED] synaptic error"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by bratliff on 2007-12-04
What is the reason I keep getting this error when I do an install? See the attachment.
'
bratliff

---

### Post by wormser on 2007-12-04
Does this happen when you try to install anything?  I found a [thread]("http://ubuntuforums.org/showthread.php?t=466646") marked solved with the same error.  The solution was to create an inittab file in /etc.

```
sudo touch /etc/inittab
```

---

### Post by bratliff on 2007-12-05
Yes, when I Install or uninstall anything including the system update I get a error.
Bratliff

---

### Post by PmDematagoda on 2007-12-05
Would you please not start duplicate threads, it is confusing and is not allowed on the forums. I just replied to your last one using the same answer wormser gave.

---

### Post by bratliff on 2007-12-05
Great, that had fixed my errors. 

thank you
bratliff



> **wormser said:**
> Does this happen when you try to install anything?  I found a [thread]("http://ubuntuforums.org/showthread.php?t=466646") marked solved with the same error.  The solution was to create an inittab file in /etc.

```
sudo touch /etc/inittab
```

---

