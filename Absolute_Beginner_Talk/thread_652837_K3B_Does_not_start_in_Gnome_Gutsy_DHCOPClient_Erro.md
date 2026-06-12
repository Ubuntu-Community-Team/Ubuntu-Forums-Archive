---
title: "K3B Does not start in Gnome Gutsy DHCOPClient Error"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by rahimveron on 2007-12-29
I just reinstalled Gutsy but when i rum kde from Terminal i get the error ```
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kdeinit: Aborting. bind() failed: : Not a directory
Could not bind to socket '/home/rahim/.kde/socket-SEBA/kdeinit__0'
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: KUniqueApplication: Can't setup DCOP communication.
```
I have removed and re-installed K3B but to no avail. 
Plz Help

PS: ALso tell me what packages to install , as i just installed it through ```
sudo apt-get install k3b
```. Do I have to install some other packages?

---

### Post by Hallvor on 2007-12-29
> **rahimveron said:**
> I just reinstalled Gutsy but when i rum kde from Terminal i get the error ```
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kdeinit: Aborting. bind() failed: : Not a directory
Could not bind to socket '/home/rahim/.kde/socket-SEBA/kdeinit__0'
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: KUniqueApplication: Can't setup DCOP communication.
```
I have removed and re-installed K3B but to no avail. 
Plz Help

PS: ALso tell me what packages to install , as i just installed it through ```
sudo apt-get install k3b
```. Do I have to install some other packages?

Normally,* sudo apt-get install k3b* should install the application with all the needed dependencies. I used K3b before, and it is an awesome application.

If you don`t use KDE, I`d look into Brasero. It may not be as cool as K3b, but at least you`ll get the job done.

---

### Post by rahimveron on 2007-12-30
I have used K3B before in Gusty Gnome(This is my reinstall as i have a separate /home partition). Brasero is good but K3B is more of an advance burning suite.
What is this DCOPCLient error stuff. I havent been able to get a clear answer.
Should i delete .kde folder in my home folder and reboot?

---

### Post by Ibu-ubu on 2007-12-30
I had this problem and solved it by changing permissions on kde.


 sudo chown -R <username>  ./.kde/

best wishes

Peter

---

