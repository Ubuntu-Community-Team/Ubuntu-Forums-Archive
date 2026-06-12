---
title: "Nob:How to make/HOME/USERS directory (SERVER PC) on all PC of network ? (adminstuffs)"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-22
-

---

### Post by adwait on 2005-11-22
Mount it from the network on all the pcs.......

---

### Post by patrick295767 on 2005-11-22
Hi,

1/I am using your method since some time (2 weeks)
and my tricks to use it are as follows:
I mount via the root the folder on the pc (distant to server):
/etc/rc2.d/S76script_mount.sh
mount IP:/mnt/hda6/home/user 



and my /etc/fstab is as follows:
192.168.123.100:/mnt/hda6/home/user1/home/user1 nfs rw,rsize=8192,wsize=8192,timeo=14 0 1

or 
192.168.123.100:/mnt/hda6/home/user1 /home/user1 nfs rw,default,user,rsize=8192,wsize=8192,timeo=14 0 1


I noticed that my root hasnt permissions to access this folder 
even if my ls -l gives :
/home/user/
rwx-rx-rx

I guess I am not using like I should my /etc/fstab. Sthg is wrong in my configuration of my /etc/fstab.
I tried with auto but it's not mounting automatically at the linux box startup (switch on).


2/ also, when my server pc is off and if my bad chance the IP address changes, I have to rechange the /etc/fstab and script to set the New IP address. (on 3 pc's)
My DHCP on my router is not the best maybe but I like it for guest pc's (linux) at home.

Is there possible to set a DHCP with HOSTNAME under linux ?
I actually try the whole week. but no results. I have tried this dhcp.conf & dhcp3.conf
stuffs but I am not able to do it.
I tried one month ago and same result. 
Too difficult maybe for a newbie.
I read that a DNS server for DHCP is possible to set up but It's not clearly explain in internet or I am tooo novice for it yet.

If you could reply, already thank you very much !!!!!

Greetings 

[email]Patrick295767@hotmail.com[/email]

---

### Post by patrick295767 on 2005-11-22
Since no one knows, Is the samba server the best way in my case ,????

([http://www.tldp.org/linuxfocus/Francais/May2002/article247.shtml](http://www.tldp.org/linuxfocus/Francais/May2002/article247.shtml))

---

