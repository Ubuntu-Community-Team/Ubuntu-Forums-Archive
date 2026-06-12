---
title: "Download FTP info from Net."
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by cutiger95 on 2006-02-21
Extremely stupid question but because I don't know I have to ask. How the heck do I download FTP information from my website server.  I need to download the entire site and modify it with NVU, but either because of stupidity or lack of sleep can't remember how to do it. Can anyone outthere give me a hand.

Thanks
C

---

### Post by iguanaphobic on 2006-02-22
Download [IglooFTP]("http://www.iglooftp.com/unix/"). Enjoy.

---

### Post by audax321 on 2006-02-22
If you're using Gnome there is also gFTP in either the main or universe repositories or if you don't want to bother installing anything you can simply go to Places > Connect to Server and enter the server information. This will give you a link to the FTP on the desktop that you can use to browse it like any other folder or you can access it using the Places menu. There is a way to do this in KDE as well, but I never use KDE anymore.

---

### Post by suRoot on 2006-02-22
No need to install more software, Nvu can handle it!

From within Nvu, click the "Edit Sites" button in the left column.  A box will appear, fill in the following info:

Site Name ->  Whatever you want to call it
Address of homepage ->  [http://yourwebsiteaddress](http://yourwebsiteaddress)
Publishing address ->  [ftp://yourwebsiteaddress](ftp://yourwebsiteaddress)
Username -> duh
Password -> duh

Click Okay.   Once the site loads, you'll see all your files over in the left column of Nvu where you can edit & do whatever you wish.

You may need to check with your hosting provider as to the address of their ftp server.  Generally speaking, it's going to be the same as your website url, just using ftp instead of http.  You may need to get your username & pass from them if you don't remember.

---

### Post by patrick295767 on 2006-02-22
[QUOTE=cutiger95]Extremely stupid question but because I don't know I have to ask. How the heck do I download FTP information from my website server.  I need to download the entire site and modify it with NVU, but either because of stupidity or lack of sleep can't remember how to do it. Can anyone outthere give me a hand.

Thanks
C[/QUOTE]
  
gftp for gnome 
or the very famous one for KDE ... kbear (buggy according to my distro-xp)
> apt-get install gftp
apt-get install kbear

Greetz

---

