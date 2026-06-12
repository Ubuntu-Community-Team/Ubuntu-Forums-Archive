---
title: "how to uninstall?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by webdreamer on 2007-03-10
I tried using aptitude uninstall code to uninstall a program, but he asked for authorization. Am I supposed to give it the password? How/when?

---

### Post by enopepsoo on 2007-03-10
you could always use synaptic or apt-get.  I don't think aptitude is installed by default.

```
sudo apt-get remove package
```

but if you are really having trouble, synaptic may be easiest.O:)

---

### Post by Wikzo on 2007-03-10
Try "sudo apt-get remove insert_the_file_name_here". Note: it doesn't uninstall everything, if you want to that use Synaptic and select "Completely remove".

EDIT: Uh, too late :P

---

