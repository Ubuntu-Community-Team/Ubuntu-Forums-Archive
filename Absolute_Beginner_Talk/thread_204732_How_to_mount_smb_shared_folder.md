---
title: "How to mount smb shared folder ?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by widjaja31 on 2006-06-27
hi All !!!
I have  2 computer, 1 for server and 1 for client. steps that i already did :

1. I already install samba server at the server computer.
2. I already shared my /pictures folder as pictures ( i did it in /etc/smb.conf )
3. I already restart samba services ( sudo /etc/init.d/samba restart )
4. In the client computer, when i type smb://server/pictures and it success. my client computer can open picture's folder. 

my question is what command that i should type to mount that shared folder as my local folder. i already type like this :

sudo mount -t smbfs //server/pictures /local_directory -o username=myname,password=mypasswd

but it's always generate an error message like this one :
wrong fs type, bad option, bad superblock on server
missing codepage or other error

so maybe there's someone could help me how to mount network shared folder into my local folder using samba ?

Thanx
Ronny Widjaja

---

### Post by Kilz on 2006-06-27
[QUOTE=widjaja31]hi All !!!
I have  2 computer, 1 for server and 1 for client. steps that i already did :

1. I already install samba server at the server computer.
2. I already shared my /pictures folder as pictures ( i did it in /etc/smb.conf )
3. I already restart samba services ( sudo /etc/init.d/samba restart )
4. In the client computer, when i type smb://server/pictures and it success. my client computer can open picture's folder. 

my question is what command that i should type to mount that shared folder as my local folder. i already type like this :

sudo mount -t smbfs //server/pictures /local_directory -o username=myname,password=mypasswd

but it's always generate an error message like this one :
wrong fs type, bad option, bad superblock on server
missing codepage or other error

so maybe there's someone could help me how to mount network shared folder into my local folder using samba ?

Thanx
Ronny Widjaja[/QUOTE]

I have a folderr on my server mounted by fstab, did you install the smbfs package?
```
sudo apt-get install smbfs
```

---

### Post by bayani on 2008-01-28
> **widjaja31 said:**
> hi All !!!
I have  2 computer, 1 for server and 1 for client. steps that i already did :

1. I already install samba server at the server computer.
2. I already shared my /pictures folder as pictures ( i did it in /etc/smb.conf )
3. I already restart samba services ( sudo /etc/init.d/samba restart )
4. In the client computer, when i type smb://server/pictures and it success. my client computer can open picture's folder. 

my question is what command that i should type to mount that shared folder as my local folder. i already type like this :

sudo mount -t smbfs //server/pictures /local_directory -o username=myname,password=mypasswd

but it's always generate an error message like this one :
wrong fs type, bad option, bad superblock on server
missing codepage or other error

so maybe there's someone could help me how to mount network shared folder into my local folder using samba ?

Thanx
Ronny Widjaja


Hi All,
I try to run this but it says 
bash: smb:/servername/home/folder/share :no such file or directory
please help, i em very new in here

---

