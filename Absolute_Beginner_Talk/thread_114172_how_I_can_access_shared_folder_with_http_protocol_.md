---
title: "how I can access shared folder with http protocol not smb"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by widjajayd on 2006-01-08
I have 2 pc

server
I shared one folder with samba and I give shared folder name as data

client
I can access from other linux client using this command
smb://10.168.0.10/data
what I want is I can access with
[http://10.168.0.10/data](http://10.168.0.10/data)

thank you

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=widjajayd]I have 2 pc

server
I shared one folder with samba and I give shared folder name as data

client
I can access from other linux client using this command
smb://10.168.0.10/data
what I want is I can access with
[http://10.168.0.10/data](http://10.168.0.10/data)

thank you[/QUOTE]
Well, you would need to at least have some sort of web server software running on the server.  Do you have anything like that set up?

---

### Post by widjajayd on 2006-01-08
Not yet, I just install ubuntu.
so it means I have to setup apache then

thanks for reply

---

