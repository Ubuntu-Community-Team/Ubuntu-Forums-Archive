---
title: "NFS slow, what could be the reasons ?  (folder sharing)"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-03-10
Hi, 

I use the :
```
10.1.1.60:/mnt/home	/home	nfs	rsize=8192,wsize=8192,timeo=14,intr
```
   
I dont know why on one pc it works fine and other, it's damn slow... 
  
The allows and deny conf files are identical ... 

Thank you 

Patrick

---

### Post by Pragmatist on 2006-03-10
Have you read the Ubuntu Howtos?
[https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29)
[https://wiki.ubuntu.com/NFSClientHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/NFSClientHowTo?highlight=%28nfs%29)

From reading the man page I'm not sure why your using **intr** and **timeo**
Also, you shouldn't need both the deny and the allow files.  The allow file is the more secure approach as you are defining who has access and everybody else doesn't have access.  The deny is the opposite.  So if you forget to list somebody in deny your screwed.  If you forget to list somebody in allow, they'll let you know about it :)

---

### Post by patrick295767 on 2006-03-12
[QUOTE=Pragmatist]Have you read the Ubuntu Howtos?
[https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/SettingUpNFSHowTo?highlight=%28nfs%29)
[https://wiki.ubuntu.com/NFSClientHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/NFSClientHowTo?highlight=%28nfs%29)

From reading the man page I'm not sure why your using **intr** and **timeo**
Also, you shouldn't need both the deny and the allow files.  The allow file is the more secure approach as you are defining who has access and everybody else doesn't have access.  The deny is the opposite.  So if you forget to list somebody in deny your screwed.  If you forget to list somebody in allow, they'll let you know about it :)[/QUOTE]
  
If you forget one IP in the allow and/or  deny file, no access via nfs is possible (on the server)... No access at all.
  
I m checking these 2 links ... thank you !
Indeed, there is no : "rsize=8192,wsize=8192," ;  I really cant recall why I used this ...  & who told me that ... (it worked during 6 months)
Let's make trials ....

---

### Post by patrick295767 on 2006-03-12
I tried with :
servername:dir /mntpoint nfs rw,hard,intr 0 0
  
And this is still slow... The X session freezes when workign or doing mozilla-firefox ... 
(I checked the hosts.allow and all right, no prob from there)
  
I dont know where it can come ... 

hmm...

---

### Post by Pragmatist on 2006-03-12
> f you forget one IP in the allow and/or  deny file, no access via nfs is possible (on the server)... No access at all.
 
Right.  That is why you use the allow file.  But again, you don't need BOTH of them.

>  Indeed, there is no : "rsize=8192,wsize=8192," ;  I really cant recall why I used this
They are in the man page where it says that you use these to greatly increase throughput, which should effect your speed.

What I would try, if I were you, is to rename your deny file to something like deny.bak or BACKUP_deny that way your just using the allow file.  Then, I would keep the line just like you had it originally except leave out the intr and timeo options so it looks like this:
10.1.1.60:/mnt/home	/home	nfs	rsize=8192,wsize=8192 
Not sure if this will work, but it shouldn't hurt.  Let use know what happens.

---

### Post by patrick295767 on 2006-03-12
Thanks Pragmatic  !!
I made experiments with the server and client ...
  
In my export, there was  only (rw)
I added then : (rw,sync)
   
  
Then, use in my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#10.1.1.60:/mnt/home /home nfs rw,user,hard,noauto,timeo=14,intr 0 0

10.1.1.60:/mnt/home	/home	nfs	rsize=8192,wsize=8192,timeo=14,intr

```
  
It solved the slow NFS !! 
  
I'll let you know if after few days, this is working still  & still stable after use
let's hope !!!
  
Thanks Pragm

---

### Post by patrick295767 on 2006-03-13
Second try today this morning & 
I got the nfs network again rather slow, but only for a 4GB files ... 
  Fvwm froze for this big file ... or maybe there was amule running on the server making network slow... 
  
I'll make a try tonight, & I hope it'll work without amule running.

Greetz

---

### Post by patrick295767 on 2006-03-26
SOLLVED :

On the client linux:  
I found that a regular use of : 
```
mount -t nfs IPaddress:/mnt/exports /home 
```
is enough to get thinks workign very fast !!
(no need of 8192 stuffs)
I did: 
ln -s /etc/init.d/mynfsscript.sh /etc/rc2.d/S79myscript.sh
 then content of   mynfsscript.sh
is only made of : ```
mount -t nfs IPaddress:/mnt/exports /home 
```
  
On the other hand, important that on the server linux, the use of 8192 and the nfs exports , 
and also autonfs can & should be used
The main and most important configuration is on the server linux

That was all !

Thank you very much for help 

Patrick

Greetings

---

### Post by patrick295767 on 2006-05-07
[QUOTE=patrick295767]SOLLVED :

On the client linux:  
I found that a regular use of : 
```
mount -t nfs IPaddress:/mnt/exports /home 
```
is enough to get thinks workign very fast !!
(no need of 8192 stuffs)
I did: 
ln -s /etc/init.d/mynfsscript.sh /etc/rc2.d/S79myscript.sh
 then content of   mynfsscript.sh
is only made of : ```
mount -t nfs IPaddress:/mnt/exports /home 
```
  
On the other hand, important that on the server linux, the use of 8192 and the nfs exports , 
and also autonfs can & should be used
The main and most important configuration is on the server linux

That was all !

Thank you very much for help 

Patrick

Greetings[/QUOTE]

  After a new installtino of linux client & server, this didnt work :-(
  
But I found out the trick & solution after google  ... 
  
I'll show up the important files & nfo to configure server & client : as follows in the next post of this thread :-)

---

### Post by patrick295767 on 2006-05-07
How to share your make "workstation (s)"  mounting a nfs server to your /home on your linux boxes :
=========================================================
  
**First, let's configure  the SERVER :**
  
/etc/exports
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).

/mnt/home IPaddressesforclient(rw,sync,no_root_squash)  IPclient2(rw,sync,no_root_squash) 
```
(dont use async, that'll mess up your data & you'll get risks for your data integrity)
   
/etc/hosts.allow
> # /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5), hosts_options(5)
#                   and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and 
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#

portmap: IP1 , IP2clients



lockd: IP1 , IP2clients
rquotad: IP1 , IP2clients
mountd: IP1 , IP2clients
statd: IP1 , IP2clients

  
/etc/hosts.deny
> # /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5), hosts_options(5)
#                  and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper. See portmap(8)
# and /usr/doc/portmap/portmapper.txt.gz for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

portmap:ALL

lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL


  
and the /etc/fstab should have : 
> IPserver:/mnt/home	/home	nfs	hard,rsize=8192,wsize=8192,timeo=14,intr	0	0
  
**Second, Let's configure the Client Linux Machine:**
to mount it when startup ; i use a script in /etc/rc...
  (I didnt use auto.nfs)
  
/etc/auto.master
> #
# $Id: auto.master,v 1.3 2003/09/29 08:22:35 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc	/etc/auto.misc --timeout=60
#/misc	/etc/auto.misc
#/net	/etc/auto.net

  
/etc/fstab
should contain: 
> IPserver:/mnt/home	/home	nfs	hard,rsize=8192,wsize=8192,timeo=14,intr	0	0
    
  
I looked some time to improve the nfs network performances & this worked for me !! :-)
  
Greetings, 
Patrick

---

### Post by patrick295767 on 2006-05-27
sometimes it can happen that the exports nfs are very slow :
  
On the server linux, I did : 
```
sudo bash
exportfs -fa
exportfs -fa
exportfs -ra
exportfs -ra
exportfs -ra
```
  maybe sometimes, to flush is kind of helping
  
It looks improving ... :-)
hmmm:rolleyes:
  
Use : nfsstat to check ur nfs state
   
=======
pitty, the flush do not improve really the nfsstat ... :-(
==============
site about auto.nfs / exports ... 
[http://linuxcourse.rutgers.edu/lessons/lesson5/sec_9.html](http://linuxcourse.rutgers.edu/lessons/lesson5/sec_9.html)

---

### Post by Jason_25 on 2006-05-28
Hey thanks for the mini how-to.  I haven't had to use any tweaks or performance tuning and it is pretty flawless so far.  It's amazingly faster and more consistent than samba.  Add to that being more secure, and I'm sold on it.

---

### Post by patrick295767 on 2006-05-28
[QUOTE=Jason_25]Hey thanks for the mini how-to.  I haven't had to use any tweaks or performance tuning and it is pretty flawless so far.  It's amazingly faster and more consistent than samba.  Add to that being more secure, and I'm sold on it.[/QUOTE]
  
Thanks !! 
I hope it'll keep working great in your case.
  
Sometimes, slow nfs can appear after months or years ...
It can happen to other distro's too ...
  
Greetz

---

### Post by patrick295767 on 2006-05-28
My question is now : 
**nfs-kernel-server or  nfs-user-server  ** ???

which one to use in order to get good performances !?
  
Greetz

> bon, repartons du début si tu le veux bien..

désinstalle :
- 'tcpd'
- 'portmap'
- 'nfs-user-server' ( à préférer a nfs-kernel-server )
- 'nfs-common'

fait une mise à jour de tes dépendances :
'apt-get update'( voire 'apt-get dist-upgrade' s'il y a des mises à jours qui ne veulent pas s'installer)

installe les packages l'un après l'autre, et arrête toi dès qu'il y a le moindre méssage d'erreur. Dans l'ordre, installe :
- 'portmap'
- 'tcpd'
- 'nfs-user-server' ( a préférer a nfs-kernel-server )
- 'nfs-common' (si tu veux la partie client de nfs, sinon, ca ne sert a rien a priori)

-------------------------------------
Troisième loi de Greer :
Un programme informatique ne fait jamais ce que vous voudriez qu'il fasse, ... il fait seulement ce que vous lui dites de faire.
  
>  - la commande "rpcinfo -p [serveur_nfs]" donne la liste des serveurs qui
> s'appuient sur RPC, avec la version du protocole supporté. NFS en fait
> partie. Sur un noyau 2.4, "rpcinfo -p | fgrep nfs" me donne :
>     100003    2   udp   2049  nfs
>     100003    3   udp   2049  nfs
>     100003    2   tcp   2049  nfs

  
> The userland NFS server is slow and has been deprecated for essentially forever in favor of kernelspace.

I don't know what you were missing, but it looked like you were having portmapper issues, which would cause long timeouts.
  
Other link : 
[http://nfs.sourceforge.net/](http://nfs.sourceforge.net/)

---

### Post by Jason_25 on 2006-05-28
I use the kernel-server.  I bet it has the best performance.  As for slowing down over time, nothing could be worse than samba.  I was getting fluctuating 200KB/sec wireless downloads from an ethernet server with samba, and i'm getting 1.7-2.2 MB/sec with a WG311T wireless G on kubuntu with NFS.

---

### Post by patrick295767 on 2006-05-30
[QUOTE=Jason_25]I use the kernel-server.  I bet it has the best performance.  As for slowing down over time, nothing could be worse than samba.  I was getting fluctuating 200KB/sec wireless downloads from an ethernet server with samba, and i'm getting 1.7-2.2 MB/sec with a WG311T wireless G on kubuntu with NFS.[/QUOTE]
  
Hi Jason, 

Thank you for your support concerning my slow nfs problem. 
The problem I have is actually very complex. I dont know what could be the reason. In thsi thread, I mainly explained how to make a standart simple Nfs sharing bu t but in some cases this has to be optimized . 
Please find below all the informations concerning the optimization and the better understanding of this frequent problem destined to " experts " : [http://www.ubuntuforums.org/showthread.php?t=183636](http://www.ubuntuforums.org/showthread.php?t=183636)
I hope you can help me !!

Thank you!! 

Patrick

---

### Post by Jason_25 on 2006-05-31
Well are other file transfers on your network slow?  Such as FTP, SSH (will be a little slower), or the dreaded samba.  Is one or both of the computers on wireless? You may need to do some tweaking such as changing channels or other router-specific settings.

---

### Post by patrick295767 on 2006-06-10
[QUOTE=Jason_25]Well are other file transfers on your network slow?  Such as FTP, SSH (will be a little slower), or the dreaded samba.  Is one or both of the computers on wireless? You may need to do some tweaking such as changing channels or other router-specific settings.[/QUOTE]
  
I worked then on it , and it was working !!
(It was only the nfs slow. 
The rest was all fine.)
  
I made some changes some time ago on the server and it was working !! :-)
  It was on the server that got slow. I thought it was okay. I installed Dapper and forgot to back up my server config ...
I think that I know the problem I changed the files in /etc/hosts.allow /etc/exports ... 
I am testing it now
I ll let you know the working solution !
  
Thank you !

[http://redhat.activeventure.com/73/customizationguide/s1-nfs-mount.html](http://redhat.activeventure.com/73/customizationguide/s1-nfs-mount.html)

---

