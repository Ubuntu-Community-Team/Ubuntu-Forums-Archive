---
title: "Windows Machines and NFS"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2008-02-28
I was wondering if there was any free software out there that will allow Windows machines to see and use the NFS server that I have set up.

---

### Post by rajj on 2008-02-28
One way is setup NFS server as CIFS server as well, you can use packages like Samba to achieve this.

---

### Post by poordamnedfool on 2008-02-28
could you go into a little more detail on this?

---

### Post by Oldsoldier2003 on 2008-02-28
> **poordamnedfool said:**
> could you go into a little more detail on this?
[Samba]("http://us3.samba.org/samba/") allows you to share files easily between linux and Windows machines. There are several how tos available that go into depth on how to configure Samba.

to install samba open a terminal and enter```
 sudo apt-get install samba
```

A good tutorial can be found here:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by poordamnedfool on 2008-02-28
Thanks but wont the nfs share that i have on the files interfere with the smb?

---

### Post by dutchman72 on 2008-02-28
NFS and Samba can share the same file/folders due to different protocols. But you will need to have samba installed for Windows to see anything. 

Linux/Unix can see either protocol, but Windows only sees Samba.

---

### Post by poordamnedfool on 2008-02-28
ok thanks a lot for the help going to try it later tonight

---

### Post by bodhi.zazen on 2008-02-28
You can mount nfs shares on Windows :

[http://doc.gwos.org/doku.php/doc:network:nfs](http://doc.gwos.org/doku.php/doc:network:nfs)

(Scroll down to the window section)

[http://www.openfree.org/pet/index.php/Mount_an_NFS_share_from_Windows](http://www.openfree.org/pet/index.php/Mount_an_NFS_share_from_Windows)

---

### Post by poordamnedfool on 2008-02-28
ok got smb setup but i keep getting this error when trying to access the network from a windows machine... unexpected network error, this occurs after i am trying to map the drive, it pops up with a window i enter the user name and password and it attempts to connect then it dumps that error

---

