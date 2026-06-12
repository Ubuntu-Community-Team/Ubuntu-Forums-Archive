---
title: "Samba Question."
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Roasted on 2008-03-22
Now, understand something. I have Samba set up and running. However, the only thing I use Samba for is for retrieving information on my desktop while I'm on my laptop. It's really easy.

However, is there no gui interface for such a thing? Like is Samba simply ran in the background, and the only gui interface you experience is when you type in the IP on a windows machine and the window appears from your linux machine with the shares in it?

---

### Post by Oldsoldier2003 on 2008-03-22
> **Roasted said:**
> Now, understand something. I have Samba set up and running. However, the only thing I use Samba for is for retrieving information on my desktop while I'm on my laptop. It's really easy.

However, is there no gui interface for such a thing? Like is Samba simply ran in the background, and the only gui interface you experience is when you type in the IP on a windows machine and the window appears from your linux machine with the shares in it?

there is no reason for a gui interface. if you need to put files in the samba shares for windows users to access all you do is move them to the directory that samba is sharing for you. nothing to it really...

---

### Post by rocketangel on 2008-03-22
Have you tried System > Administration > Shared Folders? I go there and a dialog box asks me if I want to install SMB and/or NFS. There's a GUI with buttons to add shared folders and stuff...

---

### Post by Oldsoldier2003 on 2008-03-22
> **rocketangel said:**
> Have you tried System > Administration > Shared Folders? I go there and a dialog box asks me if I want to install SMB and/or NFS. There's a GUI with buttons to add shared folders and stuff...

he already has samba up and running... but i guess adding shared folders on a desktop machine is a little easier- i've never bothered because I have a samba server set up and would never consider running samba on my workstation...

---

### Post by fmartinez on 2008-03-22
From what I understand is that you want additional directories to share with you Windows Machine..... 
Edit you /etc/samba/smb.conf file
add the path to the files you want to share with the Windows machine something like this:

[directory name]
path = /path/to/directory
guest ok = yes
share  = yes
browseable = yes

you can also install SWAT if you want an GUI interface for samba. Its an HTML based program. so after install in your browser type: [http://localhost:901](http://localhost:901)
that should get into samba
if you want set global permissions you have to give root a password
type
#sudo passwd root
enter password

GOOD LUCK!

---

### Post by Roasted on 2008-03-22
> **Oldsoldier2003 said:**
> he already has samba up and running... but i guess adding shared folders on a desktop machine is a little easier- i've never bothered because I have a samba server set up and would never consider running samba on my workstation...

Why not? I have 2 computers... desktop and laptop. I set up my desktop as the samba server for the LAN here I have, so my mom and brothers can throw files onto my desktop to back them up. I also have a laptop, which simply runs XP Pro. 

But I use my desktop (the samba station) for whatever I want, despite having samba running. I've had no issues.

---

