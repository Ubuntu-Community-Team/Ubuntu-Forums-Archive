---
title: "how make ubuntu and windows connect for each other?"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by liulm on 2006-07-28
there are two computers in my office,which are used by myself.
the OS Windows 2000 was used in one of the computers,
the other used the OS ubuntu. they are unattached,
but now i want to make them connect for each other.
So I want to know how can make the connection?:confused:

---

### Post by nalmeth on 2006-07-28
What type of filesharing do you need?

Just a shared folder on each for Media?

Have you installed samba? First create MSHOME workgroup in Windows

then:
Applications -> Accessories -> Terminal

sudo apt-get update
sudo apt-get install samba

System -> Administration -> Shared Folders

This will open a samba config window, add the folder, and edit the properties as you see fit.

Is this what you are needing?

::EDITED:: 
Things have changed much with gnome in dapper, I suppose it's been too long since I've used it. My bad

---

### Post by VexD on 2006-07-28
nautilus??  o.O

---

### Post by liulm on 2006-07-28
thank you!but i have oter problem.
i did that,i can see the share file of ubuntu,but in ubuntu i cannot access the files of Windows.
i input smb://windows_ip no reflect.why?

---

### Post by nalmeth on 2006-07-28
Have you designated any folder to share from windows? If you have, they should show up.

Sadly, I can't help you with that, I don't know windows.

Did you create MSHOME from windows? Perhaps you have a firewall blocking samba's ports? 

I don't know, Sorry

---

### Post by liulm on 2006-07-28
Thank you !!
I designat a folder to share from windows, but they cannot show up.I donnot know how create MSHOME from windows.how ?
thank you!

---

### Post by drworm01 on 2006-07-28
I only know how to create MSHOME in WinXP, but hopefully the process is similar if not the same.
In "My Network Places" click on "Set up a home or small office network." This will open a wizard that'll lead you through the steps to creating a network. You can set up the network name there (default is MSHOME) and Ubuntu should be able to detect and access it if they're on the same network.
At least, that's worked for me. However I haven't been able to get my Windows computers to access Ubuntu even though Ubuntu can access and upload/download from their shared folders.

---

### Post by liulm on 2006-07-28
> **drworm01 said:**
> I only know how to create MSHOME in WinXP, but hopefully the process is similar if not the same.
In "My Network Places" click on "Set up a home or small office network." This will open a wizard that'll lead you through the steps to creating a network. You can set up the network name there (default is MSHOME) and Ubuntu should be able to detect and access it if they're on the same network.
At least, that's worked for me. However I haven't been able to get my Windows computers to access Ubuntu even though Ubuntu can access and upload/download from their shared folders.

my pc is Windows 2000,cannot find "Set up a home or small office network.",how do in 2000?

---

### Post by liulm on 2006-07-28
want windows access ubuntu,you do:

Application->Accessories->Terminal
 ------ open the Terminal,input
sudo
 -------input root password
apt-get install smbclient
gedit /etc/samba/smb.config
 -------open the smb.conf file
find security=user
-------save,close
then ,i think you can find ubuntu in your Windows pc.

---

