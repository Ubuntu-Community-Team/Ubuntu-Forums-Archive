---
title: "[SOLVED] No idea how to share linux printer with windows computers?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by teryowen on 2008-03-24
I have absolutely no idea where to start.

Ive heard of samba but even then i tried downloading that playing around but i have no idea of what im doing. Then i removed it and read some stuff on configuring smb.conf but no luck as i have no idea of what im doing.

All i want is to share my printer with the other windows computers which are connected to the same LAN. Any help would be appreciated thanks.

---

### Post by wolfvorkian1 on 2008-03-24
> **teryowen said:**
> I have absolutely no idea where to start.

Ive heard of samba but even then i tried downloading that playing around but i have no idea of what im doing. Then i removed it and read some stuff on configuring smb.conf but no luck as i have no idea of what im doing.

All i want is to share my printer with the other windows computers which are connected to the same LAN. Any help would be appreciated thanks.

Try this YouTube tutorial. It is about as clear as you'll find. 

[http://tinyurl.com/3avurg](http://tinyurl.com/3avurg)

---

### Post by teryowen on 2008-03-24
hmm i went through the video all the instructions and no luck, first problem was when i could see the shared files of the windows computers, and then my windows computers couldnt see the windows shared folder. and i still cant add a printer.

is there any way to make samba go back to defaults that it started with just so i can start from scratch i feel like the smb.conf file is too screwed up by now.

---

### Post by teryowen on 2008-03-24
WOOOHOOO, ye got the printers working finally. 

I just copied what i found on some website onto the smb.conf file and just played around with it.

this is the site: [http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-samba-servers.html](http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-samba-servers.html)

and what i added to the smb.conf
```

[global] 
workgroup = DOCS 
netbios name = DOCS_SRV 
security = share 
printcap name = cups 
disable spools= Yes 
show add printer wizard = No 
printing = cups  
[printers] 
comment = All Printers 
path = /var/spool/samba 
guest ok = Yes 
printable = Yes 
use client driver = Yes 
browseable = Yes
```

Thanks for the help.

---

