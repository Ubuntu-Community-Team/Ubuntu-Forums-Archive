---
title: "/etc/samba/smb.conf"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by th1bill on 2007-11-20
I found the command line on the web for Red Hat but in Terminal and Root Terminal I recieve permission denied.  My 2Wire Netork is fine and from my Ubuntu unit I get right into the Windows units without a hitch.  I have set the permission to share on the Folder in Ubuntu but when I attempt to log on from any Windows unit I am confronted with no ability to do so.

I have set up an account to log onto but it fails.  This is the only Linux unit so I a
can not test that aspect.  I am left believing thaT i NEED TO CONFIGURE sAMBA.

help, PLEASE.

---

### Post by maybeway36 on 2007-11-20
```
gksu gedit /etc/samba/smb.conf
```
Try that out. Or you could install system-config-samba if you want a GUI.

---

### Post by MystaMax on 2007-11-20
Hi th1bill-

Take a look at this Samba guide on the Communtiy Docs site

[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

---

### Post by th1bill on 2007-11-20
> **maybeway36 said:**
> ```
gksu gedit /etc/samba/smb.conf
```
Try that out. Or you could install system-config-samba if you want a GUI.

Thanks, I am the only user on this unit and I saved the commqand line and installed the GUI.  I brought it up with no problem and when things quiet down tonight I'll work with it a bit.  Once more, thank-you for your patients and help.

---

### Post by th1bill on 2007-11-20
> **maybeway36 said:**
> ```
gksu gedit /etc/samba/smb.conf
```
Try that out. Or you could install system-config-samba if you want a GUI.

I found your answers very useful and having the GUI now I will play tonight.  Thank-you gentlemen very much.  You folks are making me a Linux addict.  If Microsoft ever figures out the meaning of the word service they might, I doubt it, but they might just slow the movement away from them.  I am not grounded yet and already I am pushing Ubuntu/Kubuntu for the standard OS.

---

### Post by AlanRogers on 2007-11-20
After you've done```
sudo gedit /etc/samba/smb.conf
```you need to do```
sudo smbpasswd -a <user>
sudo smbpasswd -e <user>
sudo /etc/init.d/samba restart
``` or you've not finished. You can have the same user list in Samba as in Linux but they are entirely separate lists; just because you are a valid user in Linux does not automatically grant you rights in Samba.

---

### Post by th1bill on 2007-11-20
Thank-you. I've put a post-it on the unit for tonight.  You gents are very good.

---

