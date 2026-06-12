---
title: "Creating Directories Within The FTP Folder"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Ken Iovino on 2007-10-18
Hey Guys, I'm using Ubuntu Gusty 7.10 and I manage and run multiple websites. I wanted to know if it's possible to change the permissions of these FTP folders I have. As it is now, I can't create directories or files within the FTP folder, I have to create them on my desktop and move them to the FTP folder. Anyone know how I can fix this? 

Thanks!

---

### Post by Dr Small on 2007-10-18
What ftpd do you use? I use ProFTPd, and GPROFTPD as the gtk frontend.

Dr Small

---

### Post by Ken Iovino on 2007-10-18
I'm using ubuntu's built in networking options. If you go to Places > Connect To Server and add your information, it will create a shortcut of the folder of your site. I'm not able to create files/folders within them, was wondering if that was by design.

---

### Post by Dr Small on 2007-10-18
Oh.. Well, if you are not hosting the FTP server, then it is most likely on the server's end.
Did you try another FTP client, such as gFTP ?

```
sudo apt-get install gftp
```

Dr Small

---

### Post by Ken Iovino on 2007-10-18
I have filezilla that I use also, but it's just much easier for me to use the FTP folder on my desktop, keeps me organized. I'm able to create files and folders through Filezilla just fine. 

 Would you or anyone else know what I might have to do on my server to get this done, or how I can change the permissions to give me the options to create files and folders via the folder? When I right click on the folder, I don't see the options.

I'm sorry to be a pest, I'm almost certain there is an easy fix here, I just can't figure it out.

---

### Post by Dr Small on 2007-10-18
You are no pest. We enjoy answering questions.
First, I do in fact realize that it is more convienant to connect to the FTP accounts from your desktop, but we need more facts; That is why I asked you if you had tried another ftp client.

If it does it in another ftp client, then it is the server, of which you can not change any permissions on your end, to allow yourself the privilages to create folders and such.

If it does work, while in another ftp client, all probablility points towards Nautilus.

Dr Small

---

### Post by oldos2er on 2007-10-18
Do you have write permission on the server(s)?

---

### Post by Ken Iovino on 2007-10-18
Thanks, I appreciate the support. I do have have write permissions on the server, I have 4 that I'll need to do this on. I can SSH into them through the terminal if I need to change anything.

---

### Post by oldos2er on 2007-10-18
You can use SSH through Nautilus too.

Maybe you'd need to login as root to manage your sites? Type 'gksu nautilus' in a terminal, then open the connection.

---

