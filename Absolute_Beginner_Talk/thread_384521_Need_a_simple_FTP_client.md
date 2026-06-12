---
title: "Need a simple FTP client"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-14
I need a simple to use ftp client. I scanned the forum and found reference to gftp -- what is that? I tried to use that at the prompt and didn't do any good.

---

### Post by elephant007 on 2007-03-14
If you're using Firefox go to this link

[FIREFTP]("https://addons.mozilla.org/search.php?q=fireftp&type=A&app=firefox")

It's FIREFTP a Firefox Add-On, sweet, simple and easy

---

### Post by CyBuzz on 2007-03-14
gftp is a gui ftp client for Gnome.

FireFTP is an addin for firefox.  It works ok.  Doesnt support proxy though...that I could find.

---

### Post by Rhubarb on 2007-03-14
gftp is a good simple GUI client.  You'll see it under Applications -> internet -> gftp
gftp is in the repositories.
[http://gftp.seul.org/](http://gftp.seul.org/)

If you're looking for a more powerful GUI ftp client, I recommend you try out the linux version of filezilla:
[http://filezilla.sourceforge.net/](http://filezilla.sourceforge.net/)

---

### Post by lwalper on 2007-03-14
Thanks all. FireFTP worked great.

---

### Post by elephant007 on 2007-03-14
> **CyBuzz said:**
> gftp is a gui ftp client for Gnome.

FireFTP is an addin for firefox.  It works ok.  Doesnt support proxy though...that I could find.

since it's a Firefox Add-On, do you think changing the proxy setting in Firefox preferences would be setting it for FireFTP too?  I have no need for a proxy server, since you mentioned no support for proxy I thought I would look into it.. what do you think?

---

### Post by Songwind on 2007-03-14
FTP proxies are generally (or at least frequently) different than HTTP proxies.  Our local proxy, for example, requires you to log in to a local box as an FTP client, and use remoteuser@remotehost for your username, and the remote hosts's password, then it goes out and tries to connect to the remote host on your behalf.

---

### Post by maniacmusician on 2007-03-14
Looks like you've already found FireFTP, but I think there are better alternatives that can exist outside of firefox.

FileZilla is a traditional FTP client that does what most people has used do. It's in the repos. To install it, you can use Synaptic package manager or use the command line (sudo apt-get install filezilla). 

gFTP is okay; It's really simpe, not very powerful.

Konqueror is a file manager for KDE and it has really powerful FTP integration built in.

For future reference, since you were confused about how to use gFTP; you can't use a program if you don't have it. gFTP is not installed by default. to get it, you have to install it using synaptic or the command line (sudo apt-get install gftp).

---

### Post by aysiu on 2007-03-14
> **maniacmusician said:**
> 
FileZilla is a traditional FTP client that does what most people has used do. It's in the repos. To install it, you can use Synaptic package manager or use the command line (sudo apt-get install filezilla). One qualification: [FileZilla is in the repositories only if you're using Edgy and have backports enabled or if you're using Feisty](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=filezilla&searchon=name&subword=1&version=all&release=all). It isn't in the repos for Dapper.

---

