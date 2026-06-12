---
title: "how do i mount a windows share with samba?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Mangledbmx on 2006-07-25
hey, im trying to mount a few shared folders on a windows computer on my network. what commands do i need to use to do this? do i need to edit samba's config file? and is so what do i need to change.

ive read several tutorials but none helped. 


PLZ HELP ME OUT HAHA

thank you

---

### Post by Mangledbmx on 2006-07-25
help.... me...... im ......... withering....... oh god why!

---

### Post by GarlicFish on 2006-07-25
First check your windows PC to get the workgroup name

On your Ubuntu system, edit /etc/samba/smb.conf
edit the following lines as a starting point, this will share out all home areas:
```
workgroup = workgroupname

[homes]
   comment = something to identify home shares
   browseable = yes

   writable = yes

   create mask = 0644

   directory mask = 0755
```

next set a samba password for at least one of your users
```
sudo smbpasswd -a [username]
```

on your windows box, check basic comms
```
ping [server ip adress]
e.g. ping 192.168.0.1
ping [servername.domainname.blah (FQDN)]
e.g. ping bob.mydomain.com
ping [ping servername]
e.g. ping bob
```

you should be able to ping the short name of your server, if not change the primary DNS suffix on your windows client or use the servers IP address in the next command

```
net use * \\servername\[linux account name] /user:[linux user account] [password]
```

this should map the next available drive letter to your linux home area

check you can read and write files

If that all works, you can start mucking about with manually creating shares, network neigbourhood browsing and all that jazz.

---

