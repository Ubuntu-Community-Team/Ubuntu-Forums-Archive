---
title: "NFS mount help!"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by adt41287 on 2007-05-27
i keep getting this error when trying to mount from a nfs server

mount: 192.168.1.111:/media/sda1 failed, reason given by server: Permission denied.

here is the line from my  /etc/exports file from the server:
```
/media/sda1 192.168.1.1/24(rw,no_root_squash,async)
```

and also my /etc/fstab file from the nfs client:
```
192.168.1.111:/media/sda1 /media/movies nfs rsize=8192,wsize=8192,timeo=14,intr
```

i get that error when i run the command 
```
sudo mount /media/movies
```

note: /media/movies is already created on the client.

thanks in advance!!

---

### Post by deadgobby on 2007-05-27
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by adt41287 on 2007-05-27
i went through it all and edited hosts.allow, hosts.deny, and hosts file and restarted services and still did not seem to help still getting the permission denied :(

found in another post that they got it working by restarting their computer, im off to do that and let you know how it goes

---

### Post by adt41287 on 2007-05-27
still no luck :(

---

### Post by adt41287 on 2007-05-28
*bump*

---

### Post by bodhi.zazen on 2007-05-28
Are you running a firewall on either box ?

If so disable them and re-try

If it works without the firewall you need to then configure your firewall(s).

---

### Post by adt41287 on 2007-05-28
i do not have any firewalls installed on either

---

### Post by bodhi.zazen on 2007-05-29
Well, i do not see any obvious problem with what you posted ....

So ...

Did you install the nfs server ?  What OS are you using a a client ? server ?

Can you ping the server from the client ?

can you post your hosts.allow and hosts.deny ?

---

