---
title: "Ubuntu and file permissons"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by uyducu2k on 2006-06-22
I was thinking to install linux and with ubuntu's fame I have tried my luck.I used linux before so I thought ubuntu was easy.Here is the frustrations;
1.After I boot from live cd and click install button it didnt give me option to install it fat32 partiton it created linux partion on my fat32.I want to use fat32 partition for linux and I dont care performance issue.That way I can share files easily.
2.I have logged in and tried to use my Truemobile 1150 wireless modem(orinoco) and it didnt worked.I have read man pages and found wpa_* It complained about some conf file.I have created one and tried to save to /etc.Boom! I dont have enough rights to write! I have tried everything it didnt worked.I then jumped to useraccounts and groups and changed root password to root(I dont know what was it before) I switch to root user and saved that conf file but it didnt worked again.I have tried to see my other HDs(fat32) it said I dont have enough permissions...

To sum up,When I am logged in I want to have full rights.Isnt what passwords are for? I want to access all my HDs from linux.So if you help me to use my computer with Ubuntu I will appreciate because according to Ubuntu I dont have any rights on my pc except my home directory.Thanks.

---

### Post by th3james on 2006-06-22
Basically, this is one of the core coponents that makes linux so secure. You are not always logged in as an administrator, only root is admin, and therefore, only root has the power to break your system. However, obviously the average user needs to perform admin tasks. The way ubuntu deals with this is using something called sudo (or, SuperUser DO). This allows you to perform actions as 'root', by entering your password. Ubuntu, unlike most distros, does not allow logging in as root by default. To run a command as root in terminal you simply prefix the command with sudo, e.g.

sudo gedit

to run a program as root, you should prefix it with gksudo, as this is designed to run apps as root, e.g. for a root file manager

gksudo nautilus

As you need to provide a password to perform these actions, it makes linux a lot more secure, as you can't 'accidentally' perform an administrative action. Running nautilus as root should allow you to add or modify the file as you need to

---

### Post by x64Jimbo on 2006-06-22
You should install all your Linux partitions on ext2 and then install this plugin in Windows so you can mount and read them there:
[http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html")
In regards to your concerns about write permissions, th3james is right. It's silly to give access to all the critical system files to your user account. This practice is what has made Windows so vulnerable to malware over the years, and is why MS is working so hard to put a sudo-like system in their next version.

---

### Post by aysiu on 2006-06-22
[QUOTE=x64Jimbo]You should install all your Linux partitions on ext2 and then install this plugin in Windows so you can mount and read them there:
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)[/QUOTE]
You mean Ext3?

---

### Post by uyducu2k on 2006-06-23
Is there a any workaround to run filemanager as allways root?In order to see my files I hate to go to shell and gksudo nautilus.It is frustrating.Also could you help me to setup my wireless card Truemobile 1150.My network is WPA protected with shared key.Thanks.

I have run nautilus as root with gksudo.I still cant mount fat32 drivers.It gives me error "Unable to mount selected volume".I know it is secure but dont you think it is too much?I already issued gksudo command.In order to mount those volumes should I go back to shell and mount it by hand?If so what is the point of menu entry "Mount volume".

---

### Post by Apple 101 on 2006-06-23
Maybe you could create a shortcut that performs those commands for you?

---

### Post by catlett on 2006-06-23
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus) You can follow this guide but I thought it was in Alacarte menu editor under "system tools". Check alacarte first. Open it and hit on "system tools" see if "file browser (root)" is there. It is on mine but I don't know if that is because I created it with this procedure or if it was there by default.

---

### Post by uyducu2k on 2006-06-23
I still cant use internet with my wireless card.It is Truemobile 1150 which is orinoco clone.I cant mount my other HDS.I cant use forums,wiki etc to solve my problems,because with ubuntu I dont have net.It is frustrating to get win box get answer try,fail and ask again.I think I should try another distros that I can use my wireless card and access my HDs.I really cant belive that even if I run nautilius with gksudo command I still cant mount the HD.

---

