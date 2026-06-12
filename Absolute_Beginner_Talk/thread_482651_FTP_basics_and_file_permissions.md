---
title: "FTP basics and file permissions"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by DavePechter on 2007-06-23
I have ftp running on my Dell ubuntu server, and can ping from my Windows laptop and visa versa. I was also able to to upload 5Gb to the Ubuntu machine. At one point I could see the top three folders in the ftp directory, but each one barred me from entering via remote ftp.  At the same time I couldn't see the folder contents even from the ubuntu machine. 

I ventured in with gksudo Nautilus and widened permissions ( Is their any inheritance of permissions, or do all sub-folders need to be given wide persmissions individually? By wide I mean that I have varying owners, adnd groups so I opened access to group adn Others. ) After many trips in and out of Nautilus, I can see just about  everyhting on the Ubuntu side from the std user. However, my ftp access is dead. At one point I was able to use local access of ftp, and that is gone. 

Quite a confusion factor here after having tried vsftpd tips and directions from quite a number of sites.
Current vsftpd.conf file:

# Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=davidpechter
ftpd_banner=Welcome to Pechter Family Linux FTP
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root= /home/ftp/opendir
local_root = /home/ftp/opendir

Bottom line...two issues ftp and managing permissions in a clean way. Thanks  Dave

---

### Post by Megaqwerty on 2007-06-23
I don't have much experience with vsftpd, however I can help you with easing permission applications.
In the terminal, when you want to change the owner of a folder, and everything contained in it (including subfolders) you can do this:
```
 sudo chown username:group -R directoryname
```
(replace username, group, and directoryname with the relevant data)
When changing permissions recursively (everything in a folder) you would do this:
```
sudo chmod 755 -R directoryname
```
If you want me to teach you about the chmod numbering system, don't hesitate to ask.

I hope that helps,

Megaqwerty

---

