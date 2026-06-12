---
title: "Making Network"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-11-28
Hello,

There is an internet connection in the house where I live. The connection is by a Router and a Switch becouse there are some internet users.
All the users have connection with the Switch. 
Could you say me how I can make a network between other computers in the house? It's important to say that I only use ubuntu and the rest of the computers have Windows.
Thanks,

---

### Post by alamba on 2006-11-28
What do you mean by "make a network"? Are you trying to do file sharing between the 2 computers? If yes, do a forum search on samba and you should be up and about.

A

---

### Post by linux-beginner on 2006-11-28
Yes, I want to share some files with other computers. There are 7 computers using the hub.

---

### Post by alamba on 2006-11-28
To map a windows share in your ubuntu box: places>> connect to server and then choose Samba share and enter the connection details.

To share a file/directory in ubuntu for other windows boxes you will need to setup samba. [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

A

---

