---
title: "Help me set permissions for samba shares"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-26
Hi I'm playing around with samba and need some clarification and guidance on some things. The scenario is that I have got a server set up and I hav two folders on there that I want to share. But can't really figure out how to set the permissions right.

share: Backup_200GB which should only be accesible by the user "rudolf" who makes the backups. This should not be accessible to others without the prompt for a password

share: Medier_100GB this folder should be accessible to everyone, this contains music, photo and video. These files should be readable and watchable by everyone on the network (does the files need to executable here?) This should however also have full read,write access for it's user "rudolf"

I have this smb.conf file which I know I need to edit and found some settings here on the site, but I dont really understand them. Could someone explain what they mean and how I would go about setting them, so it would work the way I want it?
> [Backup_200GB]
    path = /media/Backup_200GB/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = rudolf
    force group = rudolf

[Medier_100GB]
    path = /media/Medier_100GB/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = rudolf
    force group = rudolf

if you could briefly explain what each line means, that would be great

EDIT: Also what does this means in relationship to the permission I set on the directory outside samba.

Lets say if I do a
>  sudo chmod 0777 /media/Medier_100GB

---

### Post by kasperbs on 2007-09-27
I have another question regarding this. And that is if the local permissions set on a folder, for example if I have set the permissions 777 for my mounted drive in /media/Medier_Backup, would that be overwritten by the permission I set for it in Samba?

---

### Post by kasperbs on 2007-09-27
does anyone know how to do this

---

### Post by umoser on 2007-10-04
First of all there are some very good Samba documentations around on the web which explain all of the options one by one. You should look out for them to get a better understanding of the Samba configuration. But here is a first short reply to your question.

path = /media/Backup_200GB/
This is the path to a directory you want to share within the workgroup set up in the globals paragraph

browseable = yes
This tells the samba server that it is visible in a network browse

read only = no
Access is not set to read only, which means the attributes of the individual files apply, either read or write.

guest ok = no
You won't allow guest accounts (users not know in the smbpasswd file.

create mask = 0644
This tells samba which Unix permissions to set on new files. Values are like in chmod.

directory mask = 0755
same for directory creation

force user = rudolf
If a valid user accesses this share he will be treated as if the user konwn as rudolf on the server accesses the directory. 

force group = rudolf
and this is the group that is used on behalf of the user

But you need more than this in smb.conf. So lookout for the online docs.

---

### Post by kasperbs on 2007-10-04
Thanks for taking your time to respond to thsi and explain the details behind all that. I will try and find some more documentation around on the internet.

Thanks.

---

