---
title: "apple connecting to ubuntu"
date: 2008-01-07
forum: Apple Intel Users
---

### Post by strip21 on 2008-01-07
This is going to sound like im mad. but anyway here it gose.

I have been given the task to install Ubuntu 7.10 server, and get all the clients to connect to it. This i have done. The problem i have is that there is a apple mac that for some reason can not connect to the server it can see it but not log on to it.

I'm running samba server and i think this is what the mac is seeing. Under the windows client i can set the log in details to the work group, pc name and domain settings (no PDC installed). Is this the same for mac, as in i need to find out what the pc name work group the mac is in or is there something i need to setup on the server?


Any comments please. By the way i don't know anything about apple software or how they work.

---

### Post by oskarloko on 2008-01-07
... I don't know exactly, but I'll try:

Just go with Finder to Net, then go to 'Go-> Connect to Server'


Or try activating Windows sharing ( it's Samba ) without sharing anything on Mac, but setting the options. Maybe the system will see the server, 

However, this is a MacOsX related question,not an Ubuntu one...

---

### Post by strip21 on 2008-01-08
Thanks for posting back to me. 

I have got Samba working on the server and the other Windows client working and connecting to the server. 
With the apple it can see the server but not connect to it, as its asking for a login details. Its just  that being a apple im not sure what to put in there ?

---

### Post by cyberdork33 on 2008-01-08
check your share configuration:
[http://easylinux.info/wiki/Ubuntu#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29](http://easylinux.info/wiki/Ubuntu#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29)

---

### Post by benanzo on 2008-01-08
Seeing as you're using this server in a multiuser environment, you're likely using 'security = user' in smb.conf.  This means that for access to the SMB shares you need to authenticate the users.  I am surprised that the Win clients are connecting without credentials but the Mac client is being prompted for them.  I would suggest you check your /etc/samba/smb.conf config file and consider setting 'security = share' which is the least secure, but easiest to manage.

Also, you might consider having a look at Webmin for a browser-based system administration panel.  It makes configuring a samba server painless.  However, I strongly advise you not to leave it running all the time.  Only start the service when you need it and shut it off when you're done since it's had some very serious security problems in the past.  Even if it hadn't, I would still be cautious about running an exposed service that could give complete access to the system 24/7.

[http://www.webmin.com/](http://www.webmin.com/)

Good luck!

---

### Post by strip21 on 2008-01-18
many thanks for your posts. 

I have tried the .......

[B]sudo apt-get check -f
[/B]
and i got 

[B]reading package - done
building dependency tree
reading state info - done[/B]

so im not sure if that has fixed or not. as for the smd.conf i have had a look in there and found that security = share already. I take it that this is not a good idear to have this set this way. 
Webmin is installed on the server as i felt this was better to use firefox than a remote desktop. 

When i try and log in to the server to see the file shares i get 

[B]The alias "servername" could not be opened, because the original item can not be found
[/B]
is there anything else i can do ????

---

### Post by cyberdork33 on 2008-01-18
> **strip21 said:**
> **The alias "servername" could not be opened, because the original item can not be found**
The that the verbatim message or did you insert "servername" for something else?

---

### Post by tgalati4 on 2008-01-18
[http://ubuntuforums.org/showthread.php?t=663277&highlight=connect](http://ubuntuforums.org/showthread.php?t=663277&highlight=connect)

---

### Post by strip21 on 2008-01-18
the "servername" = mouseint

---

### Post by strip21 on 2008-01-18
Thanks for the link. Dose it matter where 


[B]Make sure your /etc/samba/smb.conf file contains stuff like:

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = tdbsam guest

obey pam restrictions = yes

guest account = tgalati4
invalid users = [/B]

Gose in the smb.conf file

---

### Post by cyberdork33 on 2008-01-18
> **strip21 said:**
> Does it matter where it goes in the smb.conf fileIt doesn't matter where it goes, but you likely have some of those entries in the file already, so youmight want to check for them before you just add them again. 

I didn't need to know your servername really, I just thought that if that was the exact message you were getting, then you didn't enter your servername in some config file somewhere.

---

### Post by strip21 on 2008-01-18
Thats ok no problem. I have changed these lines

[B]passdb backend = tdbsam guest

obey pam restrictions = yes

guest account = tgalati4
invalid users = [/B]

But couldn't find theses

[B][tubuntu2_music_share]
path = /home/tgalati4/mp3
comment = Useful for sharing tracks
available = yes
browseable = yes
public = yes
writable = no

[windoze]
path = /mnt/windows
comment = useful for win98 files
available = yes
browseable = yes
public = yes
writable = no[/B]

With the Windows boxes i did have to add them into the samba user groups on the server before they could connect. I did this for the mac too. When i go to the Mac i can see the server but when i click on the server to login i get a window to log in, when i type in the details 

Workgroup = "company name"
User = "login name"
Password = ******************

then i get .... 
[B]
The alias mouse could not be opened because the original item can not be found[/B]

---

### Post by cyberdork33 on 2008-01-18
> **strip21 said:**
> 
[B][tubuntu2_music_share]
path = /home/tgalati4/mp3
comment = Useful for sharing tracks
available = yes
browseable = yes
public = yes
writable = no

[windoze]
path = /mnt/windows
comment = useful for win98 files
available = yes
browseable = yes
public = yes
writable = no[/B]

Those sections are where he has setup shares on the Ubuntu box. You need to make your share section similar to these examples to be accessible. For instance, if I were attempting to share my Pictures folder, I would make a section like this:
```
[Pictures]
path = /home/cyberdork33/Pictures
comment = cyberdork33's Pictures Folder
available = yes
browseable = yes
public = yes
writable = no
```

The alias error message is strange, try using "connect to" instead of clicking the alias.

---

