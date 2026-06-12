---
title: "How to see HD contents"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-04-20
I'm still using Xubuntu, but it seems I'm too dumb or too old to understand even the basics.

I still can't figure it out how to install programs.

More irritating, I cannot see whats in the HD, or if it has much space left. In fact, I don't even know where to look for the HD!

How I wish this linux thing had an windows explorer!


Anyone can help me find the HD, and how to check the contents and free space?


Thank you.

---

### Post by taurus on 2007-04-20
Open a terminal and run

Free disk space:
```
df -h
```

To install stuff:
```
sudo aptitude update 
sudo aptitude install **program_name**
```

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by kyphi on 2007-04-20
To see how the disk is utilised, go to System -> Administration -> Disks.

If you want to see the filesystem on your HD go to Places -> Home Folder and click on the up arrow (twice).
That will let you see your folder hierarchy.

To install programmes, go to Applications -> Add/Remove and there you are in Aladdin's cave.  Please note the two selectors 1. Show unsupported applications and 2. Show commercial applications.  These are programmes  available from the Ubuntu repositories.  Programmes from other sources may come in other formats but are usually self-extracting.

To uninstall programmes use the Add/Remove mentioned above.

Enjoy Xubuntu.

---

### Post by Ganda_Melga on 2007-04-21
> **taurus said:**
> Open a terminal and run

Free disk space:
```
df -h
```

To install stuff:
```
sudo aptitude update 
sudo aptitude install **program_name**
```

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)


Thanks a lot! I can now see the space left on the HD with the first command.

But still no luck installing Clam Antivirus. It seems to install, but gave me several errors, and at the end, I cannot find Clam anywhere. This worries me, because I'm running unprotected in the internet.

I'll check out the links you gave me.

---

### Post by Ganda_Melga on 2007-04-21
> **kyphi said:**
> To see how the disk is utilised, go to System -> Administration -> Disks.

If you want to see the filesystem on your HD go to Places -> Home Folder and click on the up arrow (twice).
That will let you see your folder hierarchy.

To install programmes, go to Applications -> Add/Remove and there you are in Aladdin's cave.  Please note the two selectors 1. Show unsupported applications and 2. Show commercial applications.  These are programmes  available from the Ubuntu repositories.  Programmes from other sources may come in other formats but are usually self-extracting.

To uninstall programmes use the Add/Remove mentioned above.

Enjoy Xubuntu.


Well... there is no such menu in Xubuntu. Xubuntu has differentt menus from Ubuntu, and I just can't see anything that ressembles that menu.

The Add/remove gives a list of programs wich I can install. However Clam anti virus is not one of them.  It only list one anti-virus and I have no ideia if it's any good.

Anyway, thanks for the help!

---

### Post by lluisanunez on 2007-04-21
Open your XFCE menu >> System >> Synaptics package manager
This is the best way to install and uninstall software

An you don't really need antivirus with linux :KS

---

### Post by Rui Pais on 2007-04-21
> **Ganda_Melga said:**
> 

How I wish this linux thing had an windows explorer!



It has better.. it has dozens. :) 
The default for Xubuntu is Thunar (an excellent one, btw) 
But you can install too nautilus, konqueror, rox-filer, pcmanfm, gentoo, xfe, just to name a few.

Don't be a melga ;) and choose the one you like most :lol:

---

