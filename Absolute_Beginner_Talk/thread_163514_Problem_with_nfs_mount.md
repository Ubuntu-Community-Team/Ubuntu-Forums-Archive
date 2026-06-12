---
title: "Problem with nfs mount"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by byenary on 2006-04-21
Hellow beans & cups,

I have a issue with using nfs to access ubuntu from another ubuntu
Got this files configured on server
On the 192.168.123.124 (nfs-server)

/etc/exports

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/home/elios/dump     192.168.123.125(rw)


/etc/hosts.allow

portmap: 192.168.123.125
lockd: 192.168.123.125
rquotad: 192.168.123.125
mountd: 192.168.123.125
statd: 192.168.123.125

rpcinfo -p

portmap: 192.168.123.125
lockd: 192.168.123.125
rquotad: 192.168.123.125
mountd: 192.168.123.125
statd: 192.168.123.125


so looking good i suppose




When using the 192.168.123.125 machine and do a
mount 192.168.123.124:/home/elios/dump /mnt/dump

This seems to work but i dont get write access ?

& this line in fstab does not make it happen either
192.168.123.124:/home/elios/dump  /mnt/dump nfs 0 0



Thx Byn

---

### Post by patrick295767 on 2006-04-21
It's coming from the pc sharign the folder ... write access... 
(I have to check on my pc ... to know where is the prob... in ur config ... looks okay ;..but :confused: 

for the client; 
only : 
mount -t nfs IPaddress:/mnt/...   /mnt/clientfolder
is enough
  
[COLOR="Black"][SIZE="3"][I]Take care :
You have to have same /etc/shadow 
/etc/passwd ...
woudl be recommanded ...
(it's for the number of user ) ;) ;) ;) [/I][/SIZE][/COLOR]
taht can help (but I dont recall if it's neceessary ... )

Greetz

---

