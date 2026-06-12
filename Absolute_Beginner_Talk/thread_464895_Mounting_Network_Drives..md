---
title: "Mounting Network Drives."
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by gbrook on 2007-06-05
[SIZE="2"]My First Time - so be gentle

Just installed Ubuntu today and after some issues setting up a Printer (a Brother MFC5440CN) the only outstanding item is accessing a Thecus 4100 NAS where I store all my Documents and wish to edit with Open Office and view etc etc.

It is on a Windows Workgroup called "Home Network".
Ubuntu can see it and shows as a Folder/ Drive but just won't let me access it.

The same goes for another Windows PC even though the Drives have all been shared previously using Windows.

I would appreciate any help as this would then have made it a relatively painless experience.

Cheers
Garry[/SIZE]

---

### Post by honeydew on 2007-06-05
I have the n2100 which has both ftp and samba(windowshares).  a easy fix for now would be using the ftp filesystem...  

at the top click              
Places >  
    Connect to server >
     Then on that box click the drop down(servicetype) and select ftp(with login)

This will create a folder on your desktop that you can use to access your share.  If you must use samba then I would search the howto forums for information on mounting samba shares. 

[http://ubuntuforums.org/showthread.php?t=255872&highlight=samba](http://ubuntuforums.org/showthread.php?t=255872&highlight=samba)

---

