---
title: "Install Samba"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by sim085 on 2007-07-26
Hi,

A friend of mine told me that I can install Samba directly from Ubuntu (without using Terminal) however I can not find the option! Does anyone know were is the option to install Samba from the GUI? I am using Ubuntu 7.04

Regards,
Sim085

---

### Post by Depressed Man on 2007-07-26
He may be talking the shared folders option.

Go to the ubuntu menu bar > system > administration > shared folders

It just installs samba for you when you try to setup a shared folder.

---

### Post by sim085 on 2007-07-26
... and would Samba service also allow me to share resources such printers and so on?

sorry for the newb question .. just too new on the linux system.

---

### Post by Depressed Man on 2007-07-26
Not sure. I'm a newbie too. Though I think Samba acts with CUPS to share printers. So you may want to look into CUPS.

---

### Post by sim085 on 2007-07-26
Thanks, seems it has worked, although I am still unsure one some things. After I install Samba i should be able to view the folders and files shared on another computer with Windows installed? or this can be done even without Samba service?

---

### Post by Depressed Man on 2007-07-26
You need the samba service (it should start up as your Linux boots up now in the background) for Windows computers to access the share files/folders you specified.

---

### Post by reckless2k2 on 2007-07-26
i think you might mean SWAT. take a look into it but edit config files will be stronger.

---

