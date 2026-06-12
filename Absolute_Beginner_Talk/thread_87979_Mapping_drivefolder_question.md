---
title: "Mapping drive/folder question"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by denhouse on 2005-11-09
Hello All, 

I'm new to Ubuntu Linux and I have a simple, probably stupid question. What is the command that you use in Windows to "map" a drive in Linux?
I've been using Windows for about 10 years so forgive me if I used the incorrect terminalogy.
I have two seperate drives in one machine, not partitions, the primary drive (hda1) is what Ubuntu is installed on and is formatted as extended 3. The secondary drive (hdb1) is formatted as vfat and that is the one that I would like to access from my other Windows machines. I have this drive shared and have smb installed and a password set up for that as well. When I try to "map" to this drive windows is asking for a user name and password, when I input the username and password that I set up in smb, it does not take it, it just asks for the same thing again.
The path that I'm using in windows is "\\<machine name>\media\windows" as that is the access path that is displayed in Disk Manager.

I have tried 3 other versions of Linux all on this machine, but Ubuntu is the easiest one that I have found to set up and use. My machine is a junker by Windows standards (333Mhz processor, 256 MB Ram, 4 Mb video...etc). With Win2K installed is just creeps along, but with Ubuntu installed it runs much faster.

Thanks in advance for any assistance.

---

### Post by Stormspace on 2005-11-09
If I am understanding this correctly you want to access a second drive on the same machine? If that is the case what you want to do is Mount the drive. In other linux distros I've also added a line to the fstab file so that a second drive is mounted at boot. At any rate it might give you something to look for by doing a search for mount instead of map. :)

---

### Post by Stormspace on 2005-11-09
I reread your post and I'm sorry I misunderstood. What you are looking for is samba. Samba is used to share directories with windows PC's on the same network. I don't know anything about Samba on unbuntu, but I have configured it with Centos and Mandrake. So you need to search on using Samba with ubuntu. Once Samba is installed you just have to edit your smb.config file to create the shares you need.  Samba is available here: [http://us3.samba.org/samba/](http://us3.samba.org/samba/) 

I would try to install samba with "sudo apt-get install samba" first however.

---

### Post by denhouse on 2005-11-09
Thanks for both suggestions.

What I want to do is get to the vfat drive on my Ubuntu Linux box from a Windows machine. The vfat drive is mounted and I can read and write to it on that machine, but I want to access it from a Windows machine that is on the network at home.
I have Samba installed. I did the command from the last post, thanks for that info, and it says that I have the newest version installed.

Thanks again.

---

### Post by Stormspace on 2005-11-09
[QUOTE=denhouse]Thanks for both suggestions.

What I want to do is get to the vfat drive on my Ubuntu Linux box from a Windows machine. The vfat drive is mounted and I can read and write to it on that machine, but I want to access it from a Windows machine that is on the network at home.
I have Samba installed. I did the command from the last post, thanks for that info, and it says that I have the newest version installed.

Thanks again.[/QUOTE]

I don't have the exact syntax available with me now, but if you look at your smb.config file there should be some examples listed on setting up your share. You might also want to right click on the folder and see if ubuntu has any sharing options available there. (I seem to remember seeing something last night when I was pulling my hair out over a Wine installation.) :)

---

### Post by denhouse on 2005-11-09
Thanks to all for your assistance.
I found the answer thanks to a friend of mine that is also running Ubuntu and reading many of the forum posts.
I had to edit my smb.conf file; add the line that gives access to the drive. Once that was done, when I connected to my Linux machine from my Windows machine the drive was there.

Now I'm a happy Linux or Ubuntu user! :D

---

### Post by Stormspace on 2005-11-09
I was surfing the ether and saw this at ubuntuguide.org :

Q: How to share folders the easy way?

Read General Notes 
Read How to install Samba Server for files/folders sharing service? 
Right click on folder -> Share folder

Shared folder -> Share with: Select "SMB"
Share properties -> Name: Specify the share name

---

