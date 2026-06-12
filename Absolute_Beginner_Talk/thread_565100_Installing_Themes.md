---
title: "Installing Themes"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Spoken on 2007-10-01
hey guys. im trying to install a new theme and login screen for my laptop. and when i go to the install part of my "login window" preference. i get a error that says File not a tar.gz or tar archive. i dont know what to do.:confused:

---

### Post by llamakc on 2007-10-01
An easy way to resolve this is to share the link to where you downloaded the theme. Often the themes are bundled together with the GDM (login window) theme stuck in the archive with the GTK2/Metacity theme also.

---

### Post by Spoken on 2007-10-01
ok..im just gona say it now. im kinda new to ubuntu and linux for that matter. so if you can, im kinda gona need to be baby stepped through this on how to fix it and get it working.

---

### Post by overlord.gaurav on 2007-10-01
You can download GDM themes at [http://art.gnome.org/](http://art.gnome.org/) or [http://gnome-look.org](http://gnome-look.org).
To open Login Screen Setup: System tab ---> Adminstration ---> Login Window or in terminal

```
gksudo gdmsetup
```

In local tab. Push the add button and browse to the downloaded GDM theme.

---

### Post by llamakc on 2007-10-01
> **Spoken said:**
> ok..im just gona say it now. im kinda new to ubuntu and linux for that matter. so if you can, im kinda gona need to be baby stepped through this on how to fix it and get it working.

No problem. You said you were trying to install a theme and a login-theme. Where did you find it. You know what a link is, right? Give us the URL of the download or site from where you are trying to install the theme from.

---

### Post by llamakc on 2007-10-01
Also, are you using KDE or GNOME?

---

### Post by coolen on 2007-10-01
When you drag-and-drop a theme to one of the theme dialogues, it generally expects to find it in a certain format: that is, a tar/tar.gz archive (a tar archive is simply a bunch of files/folders shipped together, and gzip is a compression algorithm) with a folder containing all of the theme components.
Often, people will ship several different themes in the archive, perhaps with accompanying icon themes or slight variations on the original.
If you extract the archive and drop individual folder in, it may work.

---

