---
title: "Group Folder Permission"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by jee_kes on 2007-09-19
Hi, I'm a newbie to Linux system. This is my first time installed Ubuntu in my testing PC. 

I'd downloaded Ubuntu v7.04 and installed in my PC. My question is how to I make "share group folder permission with authentication"?

I follow exactly the tutorial:

sudo mkdir /home/group
sudo chmod 777 /home/group/
gksudo gedit /etc/samba/smb.conf

security = user
username map = /etc/samba/smbusers

[Group]
comment = group folder
path = /home/group
valid users = system_myusername
guest ok = yes
read only = no
create mask = 0700
directory mask = 0700
force user = nobody
force group = nogroup

When I log in using using windows XP machine to this "Group folder", it promts for username and password. I provided username and password but unable to access to this folder. It keeps asking me for the username and password.  

Could anyone pls enlighten me? Much appreciate.. :(

---

### Post by hyper_ch on 2007-09-19
you have not added any user yet to samba ;)

```

sudo smbpasswd -a USER

```

Remember: You have to add existing system users to it.

---

### Post by jee_kes on 2007-09-19
Thanks Hyper_ch for you prompt reply.

I've added a user using the command below but still cannot. I put

sudo smbpasswd -a jessica

It still prompt me the username and password... where goes wrong... pls help :(

---

### Post by jee_kes on 2007-09-19
Thanks Hyper_ch for you prompt reply.

I've added a user using the command below but still cannot. I put

sudo smbpasswd -a jessica

I have a user name called "jessica" in my user list. What is the meaning of "existing system user"?
Inside the smbusers, i created the below:

jessica = "jessica". 

Under smb.conf, i put "valid users = system_jessica"

It still prompt me the username and password... where goes wrong... pls help :(

---

