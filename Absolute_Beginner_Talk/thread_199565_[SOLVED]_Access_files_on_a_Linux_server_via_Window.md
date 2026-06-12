---
title: "[SOLVED] Access files on a Linux server via Windows"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by altonbr on 2006-06-19
I've been asked by a gentlemen to help him set up some way to keep all his files in one place and be able to edit them while he's out of the office. (He wants the files to be in one place because he has 3 other employees including him, that usually all have the same file).

So I know of adding an SSH shell and using WinSCP or PuTTY to use as a ftp client or act as a linux command line, but is it possible, using Windows, to use a file for Photoshop for example, that is in another town?

---

### Post by spyke01 on 2006-06-19
youd probally have to download it onto the windows machine, edit the psd file and then stick it back on the foreign box

---

### Post by NESFreak on 2006-06-19
you could try [hamachi]("http://www.hamachi.cc") to set up a lan over the internet

---

### Post by altonbr on 2006-06-22
Thanks for your help.. I'll give Hamachi a try :)

---

### Post by airtonix on 2006-07-16
hamachi is easy, but not as secure as openVPN or using the vpn feature of your router. Neither of the two last options need a third party to mediate the connection like hamachi requires...and its allwasy the hamachi company servers ....im not sure you can run your own mediation servers.

which makes me suspiscious....

---

### Post by dyssident on 2006-07-19
try NetDrive. you dont really need a virtual network to just shuffle a few files around, and NetDrive is much easier to setup and maintain. it mounts an FTP server as a drive so you can use it from any program.

there is a tutorial on using NetDrive here: [http://www.engadget.com/2005/10/25/how-to-map-a-drive-to-your-ftp-server/](http://www.engadget.com/2005/10/25/how-to-map-a-drive-to-your-ftp-server/)

---

### Post by altonbr on 2007-07-05
Hah, Hamachi. Why did I say I'd give it a try? That wasn't what I was looking for.

Is it possible to edit a file on a remote machine OR have 3 users edit a file on separate machines and then use rsync to co-ordinate all three files?

That's what I meant to ask.

---

### Post by altonbr on 2007-09-16
I guess I could have set him with SVN (Subversion). It has copy-modify-unlock and copy-modify-merge solutions for binary and text files respectively.

More here: [http://svnbook.red-bean.com/en/1.4/svn.basic.vsn-models.html](http://svnbook.red-bean.com/en/1.4/svn.basic.vsn-models.html)

---

