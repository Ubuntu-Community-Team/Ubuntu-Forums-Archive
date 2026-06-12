---
title: "I have aLinuxServerTower:HowToChange/Home/user Directory To Nfs_shared_server?"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-10
I have aLinuxServerTower:HowToChange/Home/user Directory To Nfs_shared_server?
  
I would like that the data of my pc on the network are all located on the server that is sharing folders via nfs.
(that's working nicely this nfs sharing folder) 
   
Is there sthg to add in the .Xsession or .bashrc .????
Is there an admin who could help me ?

Thank you very much

Kind regards, 

Patrick

---

### Post by Joe_lurker on 2005-11-10
You need to have the exports set up on the server first.  Then add a line to your local /etc/fstab file like:
```
<server>:/home  /home nfs  rw,rsize=8192,wsize=8192,timeo=14,intr 0 0
```
Replacing <server> with your nfs server name or ip address.  Test it using 'sudo mount /home'.  BTW you should do this from the console, not X.  When the logon screen appears press ctrl+alt+f1 to switch to a console.  You can then jump to other consoles with alt+f? with ? being 2 - 6.

Once you are satisfied reboot and see that it was mounted succesfully.

Mounting this will mount OVER your current home directory so you will not be able to see your local home files.  Thay are not overwritten, just hidden.  That makes it sort of tricky if you need to copy files over.  To see your local files you need to unmount the server: 'sudo umount /home'.

-Joe

---

### Post by patrick295767 on 2005-11-10
My fstab looked like thsi :
----- Client PC 192.x.x.16 --------
/etc/fstab:
----------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0

and so on
and:

192.x.x.15:/mnt/sda5 /mnt/folder5 nfs rw,hard,user 0 0
192.x.x.15:/mnt/sda9 /mnt/folder9 nfs rw,hard,user 0 0

from : 
[http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)
----------------------------
  
Thank you very much for ur help !!!

I'll try tonight !!

Patrick

---

### Post by patrick295767 on 2005-11-10
[QUOTE=Joe_lurker]You need to have the exports set up on the server first.  Then add a line to your local /etc/fstab file like:
```
<server>:/home  /home nfs  rw,rsize=8192,wsize=8192,timeo=14,intr 0 0
```
Replacing <server> with your nfs server name or ip address.  Test it using 'sudo mount /home'.  BTW you should do this from the console, not X.  When the logon screen appears press ctrl+alt+f1 to switch to a console.  You can then jump to other consoles with alt+f? with ? being 2 - 6.

Once you are satisfied reboot and see that it was mounted succesfully.

Mounting this will mount OVER your current home directory so you will not be able to see your local home files.  Thay are not overwritten, just hidden.  That makes it sort of tricky if you need to copy files over.  To see your local files you need to unmount the server: 'sudo umount /home'.

-Joe[/QUOTE]
   
Ahhh...
  
I trust you for the:
> rw,rsize=8192,wsize=8192,timeo=14
I have no idea what they could do...
      
For the mounting, I'll use the /etc/fstab and also put these mount command lines ... in a startup script. @S15 ...
([http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7) (down))
  

Thanks a lot !

Patrick

---

### Post by Joe_lurker on 2005-11-10
>  rw,rsize=8192,wsize=8192,timeo=14
You can read the man page to find out what these options do plus see all of the other options: 'man nfs'

If you are still having trouble please also post the file '/etc/exports' from the server.  This is the most important file.  Also for permissions you will need your users and groups to have the same UID and GID on the server and client - just putting that forward.  I remember the trouble I had setting up my first nfs server:)

-Joe

---

### Post by patrick295767 on 2005-11-11
[QUOTE=Joe_lurker]You can read the man page to find out what these options do plus see all of the other options: 'man nfs'

If you are still having trouble please also post the file '/etc/exports' from the server.  This is the most important file.  Also for permissions you will need your users and groups to have the same UID and GID on the server and client - just putting that forward.  I remember the trouble I had setting up my first nfs server:)

-Joe[/QUOTE]
  
I tried !!!
Exactly, I am fighting with permissions !!!
  
I got some troubles with mounting the /home/users
 now, it's done via rc2.d
  
I'll try again and will ask u about How to Make similar UID / GID
i have same user_names  on both pc boxes.
  
... to be continued 
I am gonna try again and let u know 
  
I have troubles now with my X session that doesnt want to start 'cos permissions
and also the rox-filer 
that says permissions prob to access the 
~/.choice/MIME... /text_plain
I dont really know cos everthg looks right 
  
I used chown
chmod 
like crazy to set up all right the permissions 
everything looks okay for permissions but X doestn want to start 
  
I 'll try now to add in /etc/fstab the nfo u gave cos I used 
nfs            user,defaults,rw,noauto          0            1
  
So, let's try ur options now !

---

### Post by patrick295767 on 2005-11-11
By the way, ... we (me & girlfriend) liked your cats !
that's ours !

Pat'

---

### Post by patrick295767 on 2005-11-11
```
rw,rsize=8192,wsize=8192,timeo=14
```
  
is workign !!!
  
Even rox-filer works too !! 
  
Everythg works but only the Office crossover doesnt work.
I tried to remove the .crossover file  (cos sometimes it helped)  but that's not working.
that's very strange 'cos on nfs-server-home/user it's not working and
for regular /home/user (not nfs) it's workign ...
  
Please could you help me ??
  
Thank you very much 

Patrick

---

### Post by patrick295767 on 2005-11-11
I found !!!
  
So, everything works super very fine !!
  
Thank you very much !!

  The crossover office is rather slow to start but after it works quite normally.
  
The Server Tower is now ready

thks 

[email]Patrick295767@hotmail.com[/email]

---

### Post by Joe_lurker on 2005-11-12
Glad I could help.  Let me know if you need anymore help.

-Joe

---

### Post by patrick295767 on 2005-11-19
Hi Joe, 

Thank you first for sharing your knowledge !
  
1/I am using your method since some time (2 weeks)
and my tricks to use it are as follows:
I mount via the root the folder on the pc (distant to server):
/etc/rc2.d/S76script_mount.sh
mount IP:/mnt/hda6/home/user 
  
   
  
and my /etc/fstab is as follows:
192.168.123.100:/mnt/hda6/home/celina	/home/celina	nfs	rw,rsize=8192,wsize=8192,timeo=14	0	1
  
or 
192.168.123.100:/mnt/hda6/home/celina	/home/celina	nfs	rw,default,user,rsize=8192,wsize=8192,timeo=14	0	1
  
  
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
I read that a DNS server for DHCP is possible to set up but It's not clearly explain in  internet or I am tooo novice for it yet.
  
If you could reply, already thank you very much !!!!!
  
Greetings from belgium and cats too !
  
[email]Patrick295767@hotmail.com[/email]

---

### Post by patrick295767 on 2005-11-21
Is there someone who knows the answer ??

thank you very much !!

---

### Post by BathroomNinja on 2005-11-22
This looks like it may be the solution to my problem.
I have 3 Ubuntu systems.  
2 Desktops, 1 laptop.

I want to be able to login on any system and access the same files and have the same rights on all computers.  Right now, I have one of the desktops sharing /home/wendy/Documents with NFS.  The Laptop automounts this folder to it's own local /home/wendy/Documents when it boots.

The problem is when I save a file to that folder using the laptop, only the laptop can edit.  The desktop can only read the file but not edit.  I can't figure out how to get the desktop and laptop to use the same users.  It sounds like what you are doing solves this problem.  Could you give a little more info on how you did this?

---

### Post by patrick295767 on 2005-11-23
[QUOTE=BathroomNinja]This looks like it may be the solution to my problem.
I have 3 Ubuntu systems.  
2 Desktops, 1 laptop.

I want to be able to login on any system and access the same files and have the same rights on all computers.  Right now, I have one of the desktops sharing /home/wendy/Documents with NFS.  The Laptop automounts this folder to it's own local /home/wendy/Documents when it boots.

The problem is when I save a file to that folder using the laptop, only the laptop can edit.  The desktop can only read the file but not edit.  I can't figure out how to get the desktop and laptop to use the same users.  It sounds like what you are doing solves this problem.  Could you give a little more info on how you did this?[/QUOTE]
  
Could we stay in contact in order to make it !!?? 
  
Once we finally are able to do it wihtout any prob', we could make an How To for that. 
  
Could you show me ur /etc/fstab & /etc/exports ?
 
The biggest problem in our case is tthe permissions 
and auto mounting the NFS sharing at the startup of PC   
(without script and using hte password stuffs located in /root/sthg folder)
  
[email]patrick295767@hotmail.com[/email]
(be)

---

### Post by patrick295767 on 2005-11-23
My server harddisk has : /home/ then users folder
+ /home/nfs_shared_users_folder
    
My /etc/fstab has:
192.168.123.100:/mnt/hda6/home/user /home/celina nfs rw,default,user,rsize=8192,wsize=8192,timeo=14 0 1
  
And I use 
/etc/exports
==> /home/   (rw) stuffs ... 
  have a look there : [http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)
     
  
I 've got troubles to mount two :
IP:/home/user and so on 
IP:/home/home/nfs_shared_users_folder  
 
Mounting a startup doesnt work !
  
COncerning permissions: 
I recommand you :
```
[HTML]rsize=8192,wsize=8192,timeo=14 [/HTML]
```
 It'll help you for permissions ... (not perfect yet but much better)
  
We both need help !!
 
Pat'

---

### Post by patrick295767 on 2005-11-23
Someone can help us for our PC used as server for /home/users on all our pc's ??

---

