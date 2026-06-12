---
title: "Samba-file sharing usename pasword problem?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by CShane on 2007-06-03
I have just installed Ubuntu 7.04 (Feisty Fawn) on a Dell PowerEdge 1900.  I want to use it as a server for 4 XP Machines.  Samba is install on the Ubuntu box.  

Both Computer A and B are running XP. On both XP machines I can see the Ubuntu Server in explorer view network group and I can access the server on Computer A but not Computer B.  If I change the smb.conf file to include the following code:

```
 map to guest  = bad user
guest account =  smbguest
```

Computer B is able to access the Ubuntu Server.  Computer B can only access the folder with 

```
guest ok = yes
```

I used the walk thourgh from here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Servers#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Servers#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

to get Conmputer A to access the folders using these setting from the above link.

How to share group folders with read/write permissions (Authentication=Yes) 
```

sudo mkdir /home/group
sudo chmod 777 /home/group/
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
gksudo gedit /etc/samba/smb.conf
```
Find this line 
...
;  security = user
...
Replace with the following lines 
 ```
 security = user
  username map = /etc/samba/smbusers
```

Append the following lines at the end of file 
```

[Group]
  comment = Group Folder
  path = /home/group
  public = yes
  writable = yes
  valid users = system_username1 system_username2
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup
```

using the above code settings on different folders I am able to get Computer A to access the Folder.

Computer B is prompted for a user name and password.  I set-up user names and passwords on the Ubuntu box to match the XP machine logon and password.  (I think this is where I am going wrong)  I used the 

$ sudo smbpasswd -a username
$ sudo smbpasswd -e username

to setup the user name and password.

I also tried using webmin to set the user name and password.  I do not have a GUI on the Ubuntu server so I use lynx as the web browsers.

It seems to me that I am doing something wrong with setting up the username and passwords.

Some random facts that may help Dx the problem:

in smb.conf file

[INDENT]security = user[/INDENT]
[INDENT]passdb backend=tdbsam[/INDENT]
[INDENT]obey pam restriction = yes[/INDENT]
[INDENT]usename map = /etc/samba/smbusers[/INDENT]

when I use the whereis smbusers nothing is returned.  Does this mean the smbusers file does not exisit or is it just my lack of knowledge in using whereis?

Thanks for the help in advance.

---

### Post by dstew on 2007-06-04
Did you add the samba users as system users first?```
sudo useradd new_user
sudo smbpasswd -a new_user
```After that, you **create** the smbusers file by editing:```
sudo nano /etc/samba/smbusers
```Put in the line```
new_user = "network username"
```Save the new file and exit the editor (I think you use ctrl-X, or ^X as nano says). The network user name will usually be different than the system user name, and the smbusers file us used by Samba to map one to the other.

As far as the whereis command, maybe try locate instead```
locate smbusers
```Whereis has a default search path that might avoid looking in some directories. However, if you did not create the file, it won't be there.

---

### Post by CShane on 2007-06-05
Hi dstew Thanks for your help on this matter.

I tried the sudo useradd new_user and got something along the lines user already exists.

I tried the locate smbusers and got nothing but, locate would not return anything.  I tried using the command locate with  several files I knew was on the server and nothing was returned.  I then decided to read up on the command and found on page 114 of (SAMS) Ubuntu Unleashed book that the locate command searches an index on a database which by default is updated at 4:20 am.  Since this is not a production machine yet I have been shutting it off at night.  Although I did work on it till 4 am several times.  I just need another 20 mins.  The book suggested running the command updatedb as a super user to manually update the database.  After doing this the locate command worked.  I then knew for sure there was no smbusers file.  I then did as dstew suggested and created the smbusers file and only added one user.  I restarted samba with the init.d command.

I then tested Computer B.  I am still prompted for a user name and password but this time they work.  I only have to do this once.  If I try opening a different folder I am not prompted for a username password unless I reboot Computer B.  I tired accessing the Ubuntu server from Computer C and D and they both work.  I am prompted for the username and password but, the different usernames work.  I only added one user to the smbusers file and I do not need to use that username to access the folders.  Therefore, I am not sure what fixed the problem. Adding the smbusers file or running the updatedb command or maybe neither.  

Since I have time before I need to put this server into production I am going to try deleting the smbusers file to see if that was the fix just to further my knowledge.  Then on the other hand if it’s not broken do not try to fix it.

---

### Post by dstew on 2007-06-05
It was creating the smbusers file that made it work. The updatedb is only used by locate.

---

### Post by CShane on 2007-06-05
Thanks for the help.  I off to having more fun with Ubuntu.


:popcorn:

---

