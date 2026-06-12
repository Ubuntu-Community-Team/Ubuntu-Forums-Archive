---
title: "FTP Problem - Users cannot upload."
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Tiberath on 2006-10-08
G'day

Forgive me if this is the wrong spot. But seeing as there are support posts here, and I have pretty much no idea what I'm doing. I figure this is correct. So if I'm mistaken please forgive me.

--

Okay. I have successfully installed SSH under the guidence of a friend of mine, who knows what he's doing. I let him then, go on and set everything up for me. FTP, DMCGI, PHP, MySQL, PHP, Apache2, PHPMyAdmin etc.

He set the vsftpd.conf file to allow local uses and not anonymous. Which is just what I needed. However, these users can not upload files. (Don't get me wrong, I'm not thick) I consulted the user documentation. And typed in *sudo nano /etc/vsftpd.conf*
Located the term: *#write_enable=YES*
And proceeded to uncomment it. I saved the file as is, and reset Apache2 and vsftpd via *sudo /etc/init.d/[apache2/vsftpd] restart*

I also created another user: *website* for which he has been set local to */var/www*.

Out of everything I've done, not a single problem has arrised. Except the fact, my FTP client tells me "Permission denied" when I attempt to upload or edit a file. The dir this user locates to works and I've double checked the vsftpd.conf file. I don't understand what could be going wrong.

I am trying to connect to my FTP server via another computer on my network which uses Windows XP Professional. This computer has no problems in viewing the apache2 website or running PhpMyAdmin on my linux computer. The only thing I can't do is upload.

I apologise if this message is hard to understand. I will try and clarify it more if people are having trouble understanding.

--

Nevermind I have resolved the issue. I followed the tag vsftpd I put up there, and it took me to a link about chmodding.
I took the following steps to solve my issue:

[i]cd /var
chmod 777 www/[/i]

I can now upload files.

---

### Post by wieman01 on 2006-10-08
I think it's the folder's permission settings that keep other from uploading files. Nothing to do with the FTP server.

There is a ftp-folder in the home-directory section, correct? Make sure the folder belongs to the right group so that everybody can upload files & remove them if necessary or enable "others" to have write-rights (assuming that your ftp-folder is "/home/ftp"):
> sudo chmod +w+w+w /home/ftp
Run this command from a terminal window and try again. This give EVERYBODY the right to "write" files.

---

