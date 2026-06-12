---
title: "FTP Transfer"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by micrologix on 2006-04-01
I use WSFTP in Windows to transfer files for some web development that I do, is there a similar program that I can use with Ubuntu and if so, how can I install it. Thanks in advance for your help.

---

### Post by niviche on 2006-04-01
You can use gFTP in Gnome, or KFTPgrabber in KDE. Both are available in the repositories. Go to Synaptic in Gnome, or to Adept in KDE, select the program you want to install, and it's done.

---

### Post by Jong on 2006-04-01
There's a program called [gFTP]("http://www.gftp.org"). It's available within Synaptic.

---

### Post by micrologix on 2006-04-01
I looked for KFTP Grabber in Adept and it is not there but I found FTP (The FTP Client) which says that it is installed, do you have any idea what this means and if so how can I run it, thanks.

---

### Post by Jong on 2006-04-01
Try installing gFTP from Synaptic. It's very similar to Windows FTP programs.
When you have installed gFTP, log out and login to refresh the GUI.
gFTP should then be located in Programs -> Internet -> gFTP.

---

### Post by micrologix on 2006-04-01
Thanks Jong, even though I am using KDE it still worked fine :-)

---

### Post by taurus on 2006-04-01
Yes, you can run Gnome's apps even if you are in KDE and vice versa...

---

### Post by Jong on 2006-04-01
Cool, now I know that too :)

---

### Post by veruus on 2006-04-01
Konqueror is a pretty good FTP client as well.  You can also use it for SCP (SFTP) transfers.

[ftp://user@location.foo/directory](ftp://user@location.foo/directory)
sftp://user@location.foo/directory

Putting "user@" keeps you from having to input a username every time you go to that location if you bookmark it.  You could also do "user:password@" but you probably don't want that sitting in your book marks...

---

