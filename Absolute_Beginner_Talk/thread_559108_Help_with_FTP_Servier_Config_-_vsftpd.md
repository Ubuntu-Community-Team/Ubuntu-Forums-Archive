---
title: "Help with FTP Servier Config - vsftpd"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by tonym2 on 2007-09-24
I did a search for this issue, but I was unable to find it in previous posts. If it's been answered before, my apologies..

I have installed VSFTPD FTP server and have it working pretty well. I am using anonymous access to host a few files that I need to allow access to for a few of my customers.

Here' s the issue: One of the files is an .exe (Windows executable) file. All I need is for a user to hit my FTP site with IE7 or Firefox and to be able to right-click and 'Save target as' to save the file to their desktop. When I test this I get an error:  

"Internet Explorer cannot download file.exe from myserver.com. The server returned extended information."

Can anyone help me make this work? Is it a setting in the VSFTPD config?

Any and all help will be appreciated.

Thanks!

Tony

---

### Post by Pumalite on 2007-09-24
It might help (I hope so):

[http://linux.about.com/od/ubusrv_doc/a/ubusg20t03.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg20t03.htm)

[http://www.debianhelp.co.uk/vsftpd.htm](http://www.debianhelp.co.uk/vsftpd.htm)

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup)

---

### Post by tonym2 on 2007-09-24
Thanks for the links, but I could find nothing that pertained to my issue. 

Thanks thouigh!

T

---

### Post by Pumalite on 2007-09-24
What a pity. I have never used a server myself. That's all I could find for you. 'Till next time.

---

### Post by tonym2 on 2007-09-24
Actually figured it out! It was simply a permissions issue! That one file I was trying to download had the permissions set to "none" for "others". I changed it to "read only" and POOF! It worked!

---

### Post by Pumalite on 2007-09-24
Glad you got it to work. I'll bookmark it.

---

