---
title: "file sharing in home network"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by cmongini on 2006-01-29
hi,
im trying to share files in a home network ( laptop with xp, pc with ubuntu) 
the computers are connected via ethernet, ping each other,but i can´t get samba to work. (followed without success the instructions found on [http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438))
it could be a download problem (i might not have been able to download all the necessary files because of network problems) . so the question. is there an other EASY alternative? i thought of making one computer an FTP server for the other, but i didn´t find any gui linux application that would allow an easy configuration! (i installed ubuntu some days ago...)any hints? thanks

---

### Post by alamba on 2006-01-29
Sure you can use ftp. All you need is a small ftp server on your windows box and a client like gftp on ubuntu. However, i've been using samba since ages and it's not too difficult to get it working and it's really very convienient. Much more so than ftp. 

Also, someday u might want to use that samba box to be a domain controller ;-)

Akshay

---

### Post by cmongini on 2006-01-29
have you suggestions for which program? if i install the ftp server on linux, which program would you suggest? 
i would like to use the samba i´ve been mucking around for 5 hours yesterday, but after following carefully the setup instructions the computers could see each other in the network, ( for example on the windows i could see the ubuntu server, but if i double click on the icon, the response was that the network path could not be found!!)

---

### Post by patrick295767 on 2006-01-29
[QUOTE=cmongini]hi,
im trying to share files in a home network ( laptop with xp, pc with ubuntu) 
the computers are connected via ethernet, ping each other,but i can´t get samba to work. (followed without success the instructions found on [http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438))
it could be a download problem (i might not have been able to download all the necessary files because of network problems) . so the question. is there an other EASY alternative? i thought of making one computer an FTP server for the other, but i didn´t find any gui linux application that would allow an easy configuration! (i installed ubuntu some days ago...)any hints? thanks[/QUOTE]
  
As I am doing, in my home network, there is 3 ubuntu linux machines, it's possible to set up  a small server pc that'll share the /home/ for all other linux machines ... (via nfs)
  
If you'd like this option, I may help you, I master this now ...  & like it very much !!
-it took me some time to find out how.

Kind regards, 

Pat'

---

### Post by cmongini on 2006-01-29
yes this would be great...do you think it would work also between an ubuntu and an xp....i´m really an enthusiast of ubuntu but at the moment it´s too early for me to swich on totally as i firsr want to test all the applications i need...
best regards
clau

---

### Post by mgmiller on 2006-01-29
I have 1 ubuntu machine and 4 windows xp machnines in my home network and use samba without problems.  The main things are to make sure you have installed all of samba from the synaptic package manager (both samba and smbfs) and then make sure that all machines are on the same work group, and finally to create a samba user and password.  Here are some more specific instrucitons on all of this:

Install samba and smbfs from synaptic package manager.
Next
sudo gedit edit /etc/samba/smb.conf

you need to change the default work group from MSHOME to HOME
further down in the file you can make the share writable by changing no to yes.
# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

    Save the edited file 

you need to also add users to samba

sudo smbpasswd -a system_username

this first command is to create a user name and password.
For example:
The command "sudo smbpasswd -a marty"  will create user marty and then prompt several times for a password. just type it in when asked.

issue command to restart samba:
sudo /etc/init.d/samba restart  

At this point it should work.  The following is just for further instructions.

##I did not need the following##
sudo gedit /etc/samba/smbusers

insert the following line into the new file
system_username = "network username"
##I did not need the above##

    To edit network user

sudo smbpasswd -a system_username

    To delete network user

sudo smbpasswd -x system_username

Q: How to share home folders with read only permission (Authentication=Yes)?

   1. Read General Notes
   2. Read How to install Samba Server for files/folders sharing service?
   3.

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo gedit /etc/samba/smb.conf

   4. Find this line

...
;   security = user
...

   5. Replace with the following lines

   security = user
   username map = /etc/samba/smbusers

   6. Save the edited file (sample)
   7. Read How to add/edit/delete network users?
   8.

sudo testparm
sudo /etc/init.d/samba restart

Q: How to share home folders with read/write permissions (Authentication=Yes)?

   1. Read General Notes
   2. Read How to install Samba Server for files/folders sharing service?
   3.

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo gedit /etc/samba/smb.conf

   4. Find this line

...
;   security = user
...

   5. Replace with the following lines

   security = user
   username map = /etc/samba/smbusers

   6. Find this section


   7. Replace with the following lines

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

   8. Save the edited file (sample)
   9. Read How to add/edit/delete network users?



Once started, any changes you make to /etc/samba/smb.conf, need to be put in place by restarting the service - just swap the word "start" with "restart" 

command to start or stop or restart:
/etc/init.d/samba start

---

### Post by mgmiller on 2006-01-29
I have 1 ubuntu machine and 4 windows xp machnines in my home network and use samba without problems.  The main things are to make sure you have installed all of samba from the synaptic package manager (both samba and smbfs) and then make sure that all machines are on the same work group, and finally to create a samba user and password.  Here are some more specific instrucitons on all of this:

Install samba and smbfs from synaptic package manager.
Next
sudo gedit  /etc/samba/smb.conf

you need to change the default work group from MSHOME to HOME (or whatever your windows work group is)
further down in the file you can make the share writable by changing no to yes.
# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

    Save the edited file 

you need to also add users to samba

sudo smbpasswd -a system_username

this first command is to create a user name and password.
For example:
The command "sudo smbpasswd -a marty"  will create user marty and then prompt several times for a password. just type it in when asked.

issue command to restart samba:
sudo /etc/init.d/samba restart  

At this point it should work.  The following is just for further instructions.

##I did not need the following##
sudo gedit /etc/samba/smbusers

insert the following line into the new file
system_username = "network username"
##I did not need the above##

    To edit network user

sudo smbpasswd -a system_username

    To delete network user

sudo smbpasswd -x system_username

Q: How to share home folders with read only permission (Authentication=Yes)?

   1. Read General Notes
   2. Read How to install Samba Server for files/folders sharing service?
   3.

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo gedit /etc/samba/smb.conf

   4. Find this line

...
;   security = user
...

   5. Replace with the following lines

   security = user
   username map = /etc/samba/smbusers

   6. Save the edited file (sample)
   7. Read How to add/edit/delete network users?
   8.

sudo testparm
sudo /etc/init.d/samba restart

Q: How to share home folders with read/write permissions (Authentication=Yes)?

   1. Read General Notes
   2. Read How to install Samba Server for files/folders sharing service?
   3.

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo gedit /etc/samba/smb.conf

   4. Find this line

...
;   security = user
...

   5. Replace with the following lines

   security = user
   username map = /etc/samba/smbusers

   6. Find this section


   7. Replace with the following lines

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

   8. Save the edited file (sample)
   9. Read How to add/edit/delete network users?



Once started, any changes you make to /etc/samba/smb.conf, need to be put in place by restarting the service - just swap the word "start" with "restart" 

command to start or stop or restart:
/etc/init.d/samba start

---

### Post by cmongini on 2006-01-29
thanks for the suggestions...unfortunately itis still not working! 
it is probably a download problem, every time i use the synaptic he tells me that there are still some old files that can´t be downloaded...so probably also a part of samba....

---

### Post by patrick295767 on 2006-01-29
[QUOTE=cmongini]yes this would be great...do you think it would work also between an ubuntu and an xp....i´m really an enthusiast of ubuntu but at the moment it´s too early for me to swich on totally as i firsr want to test all the applications i need...
best regards
clau[/QUOTE]
  
Between windows & linux, U'd need samba ... 
more difficult

  
linux linux : NFS server .. .
  
I go to bed... I'll repy to you tomorrow .. .
Greetz

---

### Post by cmongini on 2006-01-29
i found the possibility of going thru places "connect to server" this works! 
thanks anyway and good luck!

---

