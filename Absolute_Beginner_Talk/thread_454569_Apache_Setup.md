---
title: "Apache Setup?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by intrepid_geek on 2007-05-25
(Ubuntu Server, 7.04)

Ok I found where my web page files are/should be located.
Now is there an easy way to get them there from my workstation? Somehow, creating and editing them in **vi** doesn't appeal to me. Maybe SAMBA? SFTP?

If someone could just point me in the right direction I'll figure it out, but I don't know the most secure way to do this. In other words, how do the real WebAdmins do it?

---

### Post by Znupi on 2007-05-25
You should try Samba. Or better yet, ssh, but that's if you only need to connect to your machine from another linux machine.

---

### Post by intrepid_geek on 2007-05-25
So generally WebAdmins use Samba, and then create a symbolic link between say(?):

/var/www   AND  /home/MyUserName/WebDocs

---

### Post by Znupi on 2007-05-25
Yup. As far as I know.

---

### Post by ruy_lopez on 2007-05-25
SSH or, more often, ftp are better used for uploading your website files. Samba is a bit overkill. Remember this is a web server, you don't want all your cpu cycles being eaten up by a samba server.

The good thing with SSH is that its secured. To upload your files you would use a command like this:

```
scp [-r] web_files_and_folders username@webserver_ip:/path/to/webserver_root_dir
```

Use the -r flag just like you would with cp, to recursively copy.

---

### Post by Znupi on 2007-05-25
If you have a relatively decent machine, you should have no problems with a samba server.

---

