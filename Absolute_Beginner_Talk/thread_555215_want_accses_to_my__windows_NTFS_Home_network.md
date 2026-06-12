---
title: "want accses to my  windows NTFS Home network"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Kedster on 2007-09-19
I have a home network that I use with windows and half my fam still uses windows but and i want to be able to connect to the network drives What i have setup is a desktop computer downstairs with a few drive in it and a few partitions that equal about 3/4 of a terabyte and they are setup so i can be upstairs on my lap top and use them. when im on widows to set them up i run a network setup cd that i made and then i go into a file browser and go to "map a network drive" and then go to the specific place "in my network places" and select it and give it a drive letter then i can access it. I want to be able to access those network drives on ubuntu I NO HOW TO USE THE COMMAND LINE but please separate the code frome the output please otherwise i get really confused and i fail at it im still a beginner so step by step would be good. if there is a GUI(Guided User Interface) 


PS:I would like other to benefit from ur knowledge i really think this is a problem for ppl and i would like the most beginner to be able to use this (like someone thats Amish lol)so terms like GUI or CLI(command line input or interface) explain those and things like that otherwise this is not and absolute beginner foarm

---

### Post by Kedster on 2007-09-19
bump

---

### Post by jimrz on 2007-09-19
you should be able to access using Samba (the client is installed by default and if you want your lappy to act as a server that is easily installed via Synaptic). just make sure that "Workgroup" specified in your /etc/samba/smb.conf (I beleive the default is MSHOME, but that is easy to change) is the same as your win network's Workgroup/Domain
```
cp /etc/samba/smb.conf /etc/samba/smb.conf-original
```
always good idea to backup conf files before editing...jic
```
sudo gedit /etc/samba/smb.conf
```
change your "Workgroup" to match your network's

also, if you plan to play video over the network using Samba, you will need to mount the target share on your ubuntu machine to get proper results.

---

### Post by Kedster on 2007-09-19
Do you have to do any thing else

---

### Post by Kedster on 2007-09-19
whats the root so u can save and download things there like how do u find them with out the places thing on the side

---

### Post by Techno.Scavenger on 2007-09-19
In my system smbclient was not installed yet, so here is what you will do:
> 
sudo su
apt-get install smbfs
reboot


Now, relog-in. Do mount the Windows share, like: 

> 
mkdir /mnt/windows_share
mount -t smbfs -o username=your_windows_username,uid=user_id_of_normal_linux_user //windows_hostname/share_name /mnt/windows_share


Where uid can be found in /etc/passwd

Regards,
TechnoS

---

### Post by psusi on 2007-09-19
You can just browse to it from the places menu on your desktop.

---

### Post by Kedster on 2007-09-19
THANK U very much i love these fourms there no problem that cant be sloved lol

---

