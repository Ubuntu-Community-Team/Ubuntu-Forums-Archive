---
title: "Force ubuntu to download from repositories instead of CD-Rom"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-26
Hi I have a question regarding repositories. I'm normally running Ubuntu with gnome installed and do everything in a graphical interface. But I have now installed a Ubuntu Server edition, and I need to enable all the repositories - How do I do that from the command-line.

Secondly I have experienced that sometimes the server asskes for the server-install-cd - How can I force Ubuntu to download the files every time?

---

### Post by wormser on 2007-09-26
This is how to edit your sources via the command line.

```
sudo nano /etc/apt/sources.list
```

Now you need to uncomment the repositories.  Remove the ## in the lines that look like these:

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main

Go through the file and remove them for the repositories you want.  To stop searching on the cdrom look for the line (usually at the top) with cdrom in it and add ## in the front.  Then save the file.

---

### Post by bodhi.zazen on 2007-09-26
> **kasperbs said:**
> Hi I have a question regarding repositories. I'm normally running Ubuntu with gnome installed and do everything in a graphical interface. But I have now installed a Ubuntu Server edition, and I need to enable all the repositories - How do I do that from the command-line.

Secondly I have experienced that sometimes the server asskes for the server-install-cd - How can I force Ubuntu to download the files every time?

As wormser suggests, edit /etc/apt/soruces.list

Put a # in the front of the line(s) that refer to your server install CD.

---

### Post by kasperbs on 2007-09-26
Thank you very much, that was easy

---

