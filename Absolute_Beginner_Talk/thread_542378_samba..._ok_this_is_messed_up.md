---
title: "samba... ok this is messed up"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-09-03
In my ubuntu laptop...
Places->Network->Cygnehome->antubuntu (ubuntu machine)->
Error Message Box> 
The folder contents could not be displayed.
Sorry, couldn't display all the contents of the "Windows Network: antubuntu"Left in an empty looking folder. I then click the back button (to Cygnehome), then click antubuntu again and it goes right into the share with no error message. 

It dose this every first time and every first time I open every directory. 

server smb.conf
> [global]
workgroup = CYGNEHOME
netbios name = Antubuntu
server string = %h (antsvr Samba Server)
encrypt passwords = yes
wins support = yes 
security = user 
username map = /etc/samba/smbusers 

[OpenShare]
path = /media/sda7/OpenShare
public = no
guest ok = no
browsable = yes
write list = ant2ne tony mandi antsvr #
valid users = ant2ne tony mandi antsvr #
#read only = no
writable = yes
printable = no
create mask = 0765

laptop smb.conf
> [global]
workgroup = CYGNEHOME
netbios name = Ant2ne
server string = %h (ant2ne Samba Client)
encrypt passwords = no
wins support = yes 
security = user 

---

### Post by GMachine_24 on 2007-09-04
> **ant2ne said:**
> In my ubuntu laptop...
Places->Network->Cygnehome->antubuntu (ubuntu machine)->
Error Message BoxLeft in an empty looking folder. I then click the back button (to Cygnehome), then click antubuntu again and it goes right into the share with no error message. 

It dose this every first time and every first time I open every directory. 

server smb.conf


laptop smb.conf

Uhm... ok.... first, hi.

Second, this line should be (I think)
[B]
server string = antsvr[/B]

(you put the name there and take out the %h)

same for your laptop.

**I'm pretty sure you can comment out (using #) the netbios name. Try it on both machines.**

[B]
You know every user who is going to have access to the share also needs a user name and password on the Samba server, right?[/B]

I always spell it **browseable** although I don't know if it matters.

I don't think you need "wins support".

If you are not using your laptop to share files (from your laptop), I don't think you even need to configure the smb.conf file on the laptop. You can just click on places>network servers>[network name]

andn you will have to enter your user name, your samba password and the name of the network (in this case **CYGNEHOME**).

I know this is a lot. I guess try one thing at a time, right?

--gm

---

