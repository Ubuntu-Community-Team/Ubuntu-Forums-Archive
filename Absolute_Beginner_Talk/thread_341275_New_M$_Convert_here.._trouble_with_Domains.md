---
title: "New M$ Convert here.. trouble with Domains"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Lukifer122 on 2007-01-18
Good morning to all!

I've read quite a few threads about people switching, but I'm making the move from XP to Ubuntu for different reasons.  I've simply grown bored with M$,  and am looking to expand my horizons.  The ability to integrate with our NT domain was a big plus, and as soon as I saw Evolution, I was hooked. No more outlook.. yay!

Evolution is working just fine, I've managed to tie into a few printers so far (still working on the rest), terminal services lets me remote desktop to other XP machines in the office (and servers), and the clean interface is making me very happy. :D

Where I'm running into troubles is joining the domain, accessing file shares on the servers, and getting a few other printers to work. ](*,)  <-- feels kind of like this.

I've been reading all about joining a domain, but I'm afraid that I'm not experience enough with linux just yet to really understand it all. Here's the thread I'm using as a guide: [NT Domain Authentication]("http://ubuntuforums.org/showthread.php?t=540")

This thread states, "Now, the first thing we are doing is setting up samba/winbind to work with the domain, so do a nano /etc/samba/smb.conf and insert the following lines". First of all, I did make backups of all the files to be touched, and  I can open the file, but I'm not sure where to insert the lines.. does it matter?

 Next, when trying to save the file, I'm told "Error Writing /etc/samba/smb.conf: Permission Denied." I thought perhaps I needed to be logged in as root for this, but when I try to login, I'm told that the user cannot log in from this screen or something like that.  

Do i need to modify the permissions on the smb.conf file, or is it a user rights issue? 

My next issue will be getting our IBM As400 server terminal software working on here, but that will wait until I get everything else running.  If I can get this all working as needed, we'll be starting to switch workstations to linux..  no more WinXP! 

I'm sure there are people here who can answer my questions, and/or point me in the right direction...  I'm not afraid to read/learn, or play with this workstation (and potentially break something; it's a standalone test box anyways). 

Thanks for taking the time to read all this!
-Luke

---

### Post by Tomosaur on 2007-01-18
Editing files as root is a common cause of confusion. While I don't know much about samba specifically at all, the permissions problem is easily solved:
```

sudo nano /etc/samba/smb.conf

```
The password it asks for is the one you use to log on. The key is to use the 'sudo' command, this grants you root permissions for a limited time. Any time you are asked to edit anything which is 'above' your home directory, you will need to use sudo. Many adminisitrative programs also require it.

---

### Post by jvc26 on 2007-01-18
In linux you are never logged in as the admin. Therefore in order to edit system files (which are all read only so you cant screw up your system without deliberately doing it ;)) You need to use 'sudo' for more info on sudo read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Therefore the command you have been given:
nano /etc/samba/smb.conf
Would be more helpfully told as:
```

sudo nano /etc/samba/smb.conf

```
It will then ask you for your password, put it in and you can edit the file.
If you want to do a graphical edit (i.e. using an app with a GUI text editor as nano is a console based one, try out:
```

gksudo gedit /etc/samba/smb.conf

```

"insert the following lines"
Um... this may well depend what are the lines you are trying to insert?
Also another point of information if you want to know why you should use gksudo rather than sudo for a graphical application check out:
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo) - there is a vital difference.

Hope that helps :)
Il

---

### Post by Lukifer122 on 2007-01-18
SUDO: Ok, I'll try that out, thanks.  I remember being told about SU priveleges long ago.. I was getting some crash courses in Black Cat linux.. some russian distro. :P I dont speak russian at all, so I didnt last very long. haha..


The lines I need to insert into the smb.conf are as follows (according to the tut. in the other thread): 
workgroup = MYDOMAIN
idmap uid = 10000-20000
idmap gid = 10000-20000
template shell = /bin/bash
template homedir = /home/%D/%U
winbind enum users = yes
winbind enum groups = yes
winbind cache time = 10
winbind separator = +
security = domain
password server = *
winbind use default domain = yes

Obviously, I'd need to change the mydomain to my actual domain name.. does it need the FQDN here?  

"Password server = *?" I'm not sure I understand that one either.. does the * need to be replaced with the server name, or left as is?

Thanks for the quick replies and the information. :)
-Luke

---

