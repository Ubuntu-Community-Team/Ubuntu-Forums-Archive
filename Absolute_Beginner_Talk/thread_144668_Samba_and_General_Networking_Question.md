---
title: "Samba and General Networking Question"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by zgerrz on 2006-03-14
I've been having issues with connecting to shares from my WinXP comp to my Linux box. I enter the netbios name as defined in my smb.conf but I keep getting access denied.

So instead I entered \\192.168.1.101 and voila, instant access to my Linux shares from my WinXP comp. I don't care why the whole hostname resolution is screwed up, I'm fine with accessing my shares this way.

My question is, what is the equivalent command in Linux so that I can view my WinXP shares from my Linux box? In other words, how to view the shares of my WinXP comp by entering an IP address? What to enter in the address field in Nautilus would be a great help.

---

### Post by KingBahamut on 2006-03-14
Go 

Places > Connect to Server....> Change Drop down to Windows Share > supply nessecary information. 

you can use the IP address if you like to setup the share , but once thats done itll put a shortcut on your Desktop for that share. 

If you need instructions via commandline I can give you those too.

---

### Post by zgerrz on 2006-03-15
Command line instructions would be great too.

As long as I can access other computers by their IP addresses I'm good.

Thanks.

---

### Post by KingBahamut on 2006-03-15
apt-get install smbfs 

then you can 

mount -t smbfs -o username=name,password=password //machinename/sharename /mnt/smbshare

---

### Post by zgerrz on 2006-03-15
Can I use the "hosts deny" or "hosts allow" option for each individual share? Meaning, I want to be able to deny viewing and writing access to specific IPs on my network and only allow other IPs to view and write to a specific share.

---

### Post by derelict on 2006-03-15
Yes, you can, in serveral ways:
```

[myshare]
hosts allow = 192.168.2.0/24 server.home.yourdomain
hosts allow = 192.168.1. EXCEPT 192.168.1.1
hosts deny = 192.168.3.100 badcomputer terriblecomputer

```

more on man smb.conf

---

### Post by zgerrz on 2006-03-15
Awesome, everything is configured perfectly now.

Thanks for your help guys.

---

### Post by jstueve on 2006-03-15
[QUOTE=zgerrz]Awesome, everything is configured perfectly now.

Thanks for your help guys.[/QUOTE]

if you want name resolution, enable wins support for your samba server.

in smb.conf:
```

wins support = yes

```

---

