---
title: "writing to shared folders"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by iamkadryna on 2007-09-15
i have a windows xp machine and a ubuntu machine. i have my entire music collection on the ubuntu machine, and have sharing enabled. i can listen to any song i want using the windows machine, but  every time a drag new music into the shared folder from my windows pc it says cannot copy, floder is read only or full. when i shared the folder in ubuntu i unchecked read only. any ideas?

---

### Post by AndyCooll on 2007-09-15
Hmm ...not used Samba for awhile. However it maybe worth you going to the command line for this. Applications > Accessories > Terminal then typing the following:
```
gksudo gedit /etc/samba/smb.conf
```
That will open an editable config file. Towards the bottom of it is a list of your shared folders. Check that they read something similar to below:

[share]
  	comment = Shared Folder
  	path = /share
  	public = yes
  	writable = yes
  	valid users = system_username1 system_username2
  	create mask = 0700
  	directory mask = 0700
  	force user = nobody
  	force group = nogroup

Then restart Samba:
```
sudo /etc/init.d/samba restart
```

Now check if you can write to the folder.

:cool:

---

### Post by iamkadryna on 2007-09-16
the file had had similar lines at the end regarding the folder i was sharing except for:

valid users = system_username1 system_username2
create mask = 0700
directory mask = 0700
force user = nobody
force group = nogroup

i added those lines and the sharing went away. Error message on windows said something like group does not exist.

---

