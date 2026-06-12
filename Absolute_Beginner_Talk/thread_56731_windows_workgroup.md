---
title: "windows workgroup"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by fleaboss on 2005-08-13
hi, i just finished setting up my first ubuntu server, i wanted it to be a file sharing server amoung other things on the windows network. 
the only problem is that one of the computers is listed under a different workgroup, it is running xp and im not sure how im supposed to change it. any help appreciated.

---

### Post by crane on 2005-08-13
[QUOTE=fleaboss]hi, i just finished setting up my first ubuntu server, i wanted it to be a file sharing server amoung other things on the windows network. 
the only problem is that one of the computers is listed under a different workgroup, it is running xp and im not sure how im supposed to change it. any help appreciated.[/QUOTE]

 Are you saying you want to change the workgroup on the ubuntu server (samba) or the other computer? If the other what OS is it running?

---

### Post by fleaboss on 2005-08-13
i am trying to change the workgroup on the other comp. a windows xp.

---

### Post by Sam on 2005-08-14
```
$ sudo gedit /etc/samba/smb.conf
```
Find this:
```
# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = WORKGROUP
```
Replace WORKGROUP with what you want.

---

