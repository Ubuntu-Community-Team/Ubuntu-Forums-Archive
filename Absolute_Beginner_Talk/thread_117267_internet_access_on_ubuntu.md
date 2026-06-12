---
title: "internet access on ubuntu"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by alek on 2006-01-14
Hi! I am an absolute beginner in Linux... so any help would be greatly appreciated...

I am trying to configure my internet access, so I went to the website of my ISP, Bell Sympatico, and got instructions to download a set of system files and to install them in /usr/local/bin. The only problem with that is, even though I am labelled as administrator of the system, I still cannot copy anything to that file folder. I checked my privileges as well as the security designations of the folder. When trying to change the designations of the folder (by using chmod function) it said that only the "owner" (not administrator, apparently) can change the designation. I went the visual way as well, through 'my computer' right clicked on the folder, checked the properties, and it said exactly the same thing. I can see, but I cannot change anything.

My question is the following: how can I change the folder properties and enable myself to write in it?

(I have to install these files because, while attempting to configure internet access by clicking on "networking" it asked for my IP address.... however, my IP address is not static, so I don't actually have one to begin with).

Any help is greatly appreciated,
Alek

---

### Post by sesstreets on 2006-01-14
I think that you have to enable root to login using the splash screen:

System>administration>users and groups
tick "show all users and groups"
select root
press properties
give root a password

then,

System>administration>Login screen setup
Security tab
tick "allow root to login with GDM

now log off and log back in as root with your password

you should now be able to make changes to any folder.

---

### Post by L Campbell on 2006-01-14
[QUOTE=alek]Hi! I am an absolute beginner in Linux... so any help would be greatly appreciated...

I am trying to configure my internet access, so I went to the website of my ISP, Bell Sympatico, and got instructions to download a set of system files and to install them in /usr/local/bin. The only problem with that is, even though I am labelled as administrator of the system, I still cannot copy anything to that file folder. I checked my privileges as well as the security designations of the folder. When trying to change the designations of the folder (by using chmod function) it said that only the "owner" (not administrator, apparently) can change the designation. I went the visual way as well, through 'my computer' right clicked on the folder, checked the properties, and it said exactly the same thing. I can see, but I cannot change anything.

My question is the following: how can I change the folder properties and enable myself to write in it?

(I have to install these files because, while attempting to configure internet access by clicking on "networking" it asked for my IP address.... however, my IP address is not static, so I don't actually have one to begin with).

Any help is greatly appreciated,
Alek[/QUOTE]
>>>>>>>>>>>>>>>>>>>>

 (by using chmod function)

<<<<<<<<<<<<<<<<<<<<

Have you tried   sudo chmod   

sudo (super user do) gives you more authority to do things.

Hope this helps you.

---

### Post by alek on 2006-01-14
I tried logging in as the root (after going through all the steps you have shown me) and it worked perfectly :smile: 

thanks,
Alek

---

### Post by hen3rz on 2006-01-14
You could also try:

```
sudo nautilus
```

---

### Post by ed_d on 2006-01-14
sudo chown username:username name of file.

to do the directory, sudo chown -R username:username nameof direcory

owner ship is 421 421 421. 4=read  2 =write and 1=execute. and iirc, its owner, group and then world. so, to make it completely read, write execute, chmod 777.

---

