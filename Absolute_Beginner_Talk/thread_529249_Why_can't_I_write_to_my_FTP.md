---
title: "Why can't I write to my FTP?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-08-19
I'm using vsftpd for my ftp server.  I can log into it anonymously and download files from it, but I can't write to it, ie upload to my ftp server.  I've got anonymous uploading on, and my server is write enabled.  I can only assume it's because my ftp folder in the /home directory isn't write-enabled, but when I sudo chmod +w ftp from /home, it doesn't actually accept the permission change.  Am I overlooking something?

---

### Post by chrisphiz on 2007-08-19
The /home/ftp directory should have the following permissions: 
drwxr-xr-x 2 root nogroup 4096 2007-08-19 01:16 /home/ftp

To enable uploads, edit /etc/vsftpd.conf with your favorite text editor as root and uncomment the write_enable=YES line and the anon_upload_enable=YES line (not sure why you'd want anonymous people writing to your FTP server, but that's not my problem :-)

Make a directory off of /home/ftp for users to upload to and make that directory owned by ftp

sudo mkdir /home/ftp/incoming && sudo chown ftp /home/ftp/incoming

Restart vsftpd when you're finished:

phiz@brain:~$ sudo /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd                               [ OK ] 
 * Starting FTP server: vsftpd                               [ OK ] 
phiz@brain:~$ 

Chris

---

