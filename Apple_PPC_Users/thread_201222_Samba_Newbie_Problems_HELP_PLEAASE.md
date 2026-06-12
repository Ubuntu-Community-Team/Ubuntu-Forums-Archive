---
title: "Samba Newbie Problems HELP PLEAASE"
date: 2006-06-21
forum: Apple PPC Users
---

### Post by jakestah7 on 2006-06-21
I have an dapper imac. I want to share a folder so that I can write papers; ect. on the imac and then get them off from the other two computers. I can read and write to the shared folders on the other two pc's. The pc's and samba are on the same  workgroup name but, when I try to access the IMAC as like a server from other comp's on the network it asks for a password/username. I am a newbie so I don't really know what's going on. I thought the permissions on the folder might have to be read/execute/write checked for all groups, i tried that It didnt work. Can someone help me PLEASE (long story but I need to be able to do this kinda bad and I am mad I cant figure it out)

---

### Post by gerbman on 2006-06-21
Look at your /etc/samba/smb.conf file on the server, and find the line that starts with "security = ..." (it might be commented out). Change this line to look like the following:```
security = user
```This requires accessing users to have an account on the server. Next, create a Samba account for the accessing user with```
sudo smbpasswd -a username
```where "username" is your username. Last, restart Samba (not sure if this is needed, but it can't hurt):```
sudo /etc/init.d/samba restart
```Does that get you anywhere?

---

### Post by jakestah7 on 2006-06-22
Well now from the other computers I can log in as my username on the imac and password and then I can access not only the shared folder but the home folder and desktop but then once I have logged in from one of the other computers then the imac cannot see the the other computers I need to have NO username password to access the imac like if the imac was running windows

---

### Post by gerbman on 2006-06-23
[QUOTE=jakestah7]Well now from the other computers I can log in as my username on the imac and password and then I can access not only the shared folder but the home folder and desktop but then once I have logged in from one of the other computers then the imac cannot see the the other computers I need to have NO username password to access the imac like if the imac was running windows[/QUOTE]Got your message. Try this:

1) Set "security" to "share" in /etc/samba/smb.conf```
security = share
```2) Add the following options to the share definition```
path = /path/to/folder
available = yes
browseable = yes
public = yes
writable = yes

```3) Set the permissions on the folder to allow reading/writing by everyone```
sudo chmod 777 /path/to/folder
```4) Restart Samba```
sudo /etc/init.d/samba restart
```Be warned, this is a **very** insecure sharing method.

---

### Post by crankcaller on 2006-06-23
> Be warned, this is a very insecure sharing method.

I'm about to do the same between my laptop & Desktop (maybe. lol)
How insecure?  is the shared folder wide open to the net if i say take my laptop to a cafe with wifi.
My home network is behind a router with firewall.

---

### Post by gerbman on 2006-06-23
[QUOTE=crankcaller]is the shared folder wide open to the net if i say take my laptop to a cafe with wifi.[/QUOTE]If you set it up so that everyone at home has read/write access with no username/password, then yes, people on a public network should have read/write access as well. Putting the server behind a router and firewall should help security dramatically, but there's no replacement for usernames and strong passwords. There's probably a way to do public/private key authentication with Samba (removing the need for usernames and passwords) but I don't know how to do it. My recommendation is to stick with "security = user" and create accounts for the Windows machines that will be accessing the server. In Windows, you should only need to map the shared folder/drive once, so I don't see why usernames and passwords are an annoyance.

---

