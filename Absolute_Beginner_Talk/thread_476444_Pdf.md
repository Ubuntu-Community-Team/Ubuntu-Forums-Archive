---
title: "Pdf"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by datavirtue on 2007-06-17
What is the command to launch a PDF viewer from the command line.

I used to be fine on slackware but can hardly find anything on Ubuntu.

Also, I had my application (Nevitium) setup to automatically configure a PDF viewer for the user based on the OS type returned in the Java properties.  This doesn't work on Ubuntu, anyone know why?

Sean

---

### Post by meborc on 2007-06-17
depends on the program... if you use kpdf for example and you have a test.pdf in your folder you want to open type ```
kpdf /home/USER/test.pdf
```

---

### Post by starcraft.man on 2007-06-17
> **datavirtue said:**
> What is the command to launch a PDF viewer from the command line.

I used to be fine on slackware but can hardly find anything on Ubuntu.

Also, I had my application (Nevitium) setup to automatically configure a PDF viewer for the user based on the OS type returned in the Java properties.  This doesn't work on Ubuntu, anyone know why?

Sean

I suppose it should be "acroread" unless you install a pdf reader that wasn't acrobat, in which case it would be the name of the program...

I don't know about Nevitum... can't help there.

---

### Post by datavirtue on 2007-06-17
Is there a way to set the working directory for a link?

This is an extreme peave of mine.  Why doesn't Gnome let you set a working directory!?

Sean

---

### Post by schorsch on 2007-06-17
> **datavirtue said:**
> What is the command to launch a PDF viewer from the command line.

I used to be fine on slackware but can hardly find anything on Ubuntu.

Also, I had my application (Nevitium) setup to automatically configure a PDF viewer for the user based on the OS type returned in the Java properties.  This doesn't work on Ubuntu, anyone know why?

Sean

If you are using GNOME, "evince" will do the job per default.

---

