---
title: "Is ther anyway of setting a sftp connection from windows 7 laptop"
date: 2012-03-01
forum: Any Other OS
---

### Post by SiSydney on 2012-03-01
I am completely new to this type of hosting using msysgit to login to a dns server with a ssh key located in a .pem file this leaves me with vim as my only vim editor which i dont really have time to learn. Tried to re-assign --global -core.editor with very little joy. Is there anyway of setting up a sftp connection from a windows sftp client using bitkinex which does allow for ssl/ssh connections but no place for ssh .pem key so its just kicking me out. Any help would be much appreciated.

---

### Post by RonnieJaysmith on 2012-03-02
Try adding your router's hostname in the server box, the port number you are using to forward SSH traffic, your user name and your password and the default directory you want to use, eg /share. I'm not entirely sure, it's not our FTP server, it's a vendor we use. I have to use a different FTP client for that one site and it works fine. Too bad because I wanted to consolidate and use WinSCP for everything since it also does SFTP/SSH2 in addition to regular FTP.

Thanks,
Ronnie
______________
[IT Support Tech]("http://www.computerrepairandcare.net/index.html")

---

