---
title: "How can i share the files on Ubuntu to another Windows computer.???"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by AKPAKP on 2008-04-11
Please help me in trasferring the files on linux to XP....

I have a ethernet wire to connect the two computers...how do i share folder???

---

### Post by AKPAKP on 2008-04-11
Anyone help.....Please...

---

### Post by tamoneya on 2008-04-11
this is done via samba: system->adminstration -> shared folders.  Tell it to install samba and nfs.  Then you need to add a new folder.  Then you should be able to see it across the windows network.

---

### Post by hyper_ch on 2008-04-11
either use samba or ssh/scp

(or setup a webserver which has the according files in it's file directory)

---

### Post by AKPAKP on 2008-04-11
The folder which i want to share is already added there.??? how to install Samba??

---

### Post by miciurin on 2008-04-11
Open synaptic, search for samba, request install. Then turn on file sharing in system settings.

---

### Post by hyper_ch on 2008-04-11
I'd use ssh

(1) install ssh server on linux
```

sudo apt-get install openssh-server

```

(2) get a scp program for windows: [http://www.winscp.com](http://www.winscp.com)

(3) upon running winscp enter the IP of your linux box and your username/password to connect to your linux box...

(4) confortably transfer the files

---

### Post by gsiliceo on 2008-04-13
You can vote to change this in ubuntu using the brainstorm page, theres already an idea voting to make samba easier. Please vote here.
[Improve file/folder sharing experience (Samba)]("http://brainstorm.ubuntu.com/idea/403/")

---

