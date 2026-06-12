---
title: "might not be setting my permisions right"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by TekJunkie2k3 on 2006-12-22
Hey guys. I'm having some trouble setting permissions in ubuntu. I've managed to setup some samba shares but I can't write to them. I've set them up using webmin and specified which users could read and which could write but I'm still not able to write to my directories unless I manually go into each directory and turn it on for all users and groups(which i was trying to avoid). I thought that maybe because they were created by root that that was the problem. I tried changing the ownership with chown but I keep getting an error telling me that the directory isn't available. I'd really hate to have to go into each diretory and turn on all permissions since I've created many folders. I've been using ubuntu for just about a week and I'm still really new to this whole server and permissions thing. thanks.

---

### Post by seijuro on 2006-12-22
I haven't used samba myself but it does sound like you are correct in assuming the issue is because the directories were created by root. Most likely the user and group for the directory is root so if you don't enable read/write to all only root user or things in the root group will be able to access it. Did you try running chown with sudo? becuase it was made by root you can't chown it w/o root permissions. Another method is bring up nautalis(spell) with root permissions gksudo nautalis(spell) then go to the directory right click on it click properties and you should be able to change them graphically in the permissions tab.

---

### Post by dbbolton on 2006-12-22
you have to have identical username/password on the other computer(s) in order to modify the shared files.

or you could just make a copy of those files and do whatever you want with them

---

### Post by TekJunkie2k3 on 2006-12-22
> **seijuro said:**
> I haven't used samba myself but it does sound like you are correct in assuming the issue is because the directories were created by root. Most likely the user and group for the directory is root so if you don't enable read/write to all only root user or things in the root group will be able to access it. Did you try running chown with sudo? becuase it was made by root you can't chown it w/o root permissions. Another method is bring up nautalis(spell) with root permissions gksudo nautalis(spell) then go to the directory right click on it click properties and you should be able to change them graphically in the permissions tab.

For some reason sudo chown doesnt work. I keep getting an error telling me the directory doesnt exist. nautalis works however. Is there a was to change permissions and have it affect everythign in that directory as well? I transfered all my media files onto the server for backup and I dont want to have to go throuh each folder and set permissions. Thanks.

---

