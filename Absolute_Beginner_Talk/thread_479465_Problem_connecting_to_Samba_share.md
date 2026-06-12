---
title: "Problem connecting to Samba share"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by donheff on 2007-06-20
I have a beginners samba problem that I solved once but can't remember how.  I have two Ununtu boxes one on a 10.10.10 network with my windows PCs and one on a 192.168.1 network serving as a webserver.  I set them both up to share a public directory.  The one on the 10.10.10 works fine but when I try to connect to the new Feisty box on 192 I get the log in prompt but when I  enter the user name and password but don't get logged in - I just get the loggin box back.

I remember this happening on the older box but somehow fixed it in the past.  Could this simply be a result from the Feisty server not being on the same subnet as the XP boxes?  If so, is there a configuration change that will allow my to share across the subnets?

---

### Post by josesanders on 2007-06-21
How exactly are you trying to connect?  If you have a web server, you shouldn't have to log in at all.

I did have that problem, though, using Samba.  I followed these guides, and everything works now:
[http://www.go2linux.org/node/98](http://www.go2linux.org/node/98)
[http://starkos.industriousone.com/mounting-windows-shares-ubuntu](http://starkos.industriousone.com/mounting-windows-shares-ubuntu)

---

### Post by donheff on 2007-06-21
> **josesanders said:**
> How exactly are you trying to connect?  If you have a web server, you shouldn't have to log in at all.

I did have that problem, though, using Samba.  I followed these guides, and everything works now:
[http://www.go2linux.org/node/98](http://www.go2linux.org/node/98)
[http://starkos.industriousone.com/mounting-windows-shares-ubuntu](http://starkos.industriousone.com/mounting-windows-shares-ubuntu)

I can access the Web server fine and can use ssh and vnc.  The server just handles family web site chores so it is not heavily utilized and has a lot of disk space.  I want to open up a share to serve as a backup for my family XP box.  I know I shouldn't be opening up those ports on a box accessible to the Internet but I am only opening them to the internal subnet, not to the Internet.  I will take a look at those guides and see if they help.

---

### Post by donheff on 2007-06-22
> **josesanders said:**
> How exactly are you trying to connect?  If you have a web server, you shouldn't have to log in at all.

I did have that problem, though, using Samba.  I followed these guides, and everything works now:
[http://www.go2linux.org/node/98](http://www.go2linux.org/node/98)
[http://starkos.industriousone.com/mounting-windows-shares-ubuntu](http://starkos.industriousone.com/mounting-windows-shares-ubuntu)
Thanks.  The first link appears to be off the air - at least for now.  The second shows how to mount an XP share on Linux but I want to access an Ubuntu share from XP.  Again, I am doing it successfully on a different box (different version of Ubuntu also)  the same subnet but not on Feisty on the different subnet.

---

### Post by josesanders on 2007-06-22
The first link seems to be up now.

I don't think it's an issue of being on a different subnet, since I had the same problem with everything on the same subnet.

---

### Post by donheff on 2007-06-22
> **josesanders said:**
> The first link seems to be up now.

I don't think it's an issue of being on a different subnet, since I had the same problem with everything on the same subnet.

I keep getting a server not found error on the first link.  Is it possible the one you are connecting to is slightly different than the posted link?  -  [http://www.go2linux.org/node/98](http://www.go2linux.org/node/98)

---

### Post by josesanders on 2007-06-23
I'm sorry, but I keep clicking on the link in my post and in your replies, and it is fine.  I'll just post what they say:

First install Samba:

$ sudo apt-get install samba

Then edit the configuration file:

$ sudo gedit /etc/samba/smb.conf

Enter this into the file:

[global]
workgroup = MSHOME   <-- Change this to your workgroup (all users should be on the same workgroup)
netbios name = UBUNTU_SERVER  <-- This is the name of the computer as seen by the network
security = SHARE
auth methods = guest
domain master = No
wins support = Yes

[share1]
comment = mi home
path = /home/ggarron  <-- Change this to the location of the files that you want to share.  I recommend not using your home directory, since the permissions for that directory aren't supposed to allow shared access
read only = No
guest ok = Yes

Then just restart Samba and hopefully you can map the network drive on the remote system

---

### Post by donheff on 2007-06-25
> **josesanders said:**
> I'm sorry, but I keep clicking on the link in my post and in your replies, and it is fine.  I'll just post what they say: ...


[global]
workgroup = MSHOME   <-- Change this to your workgroup (all users should be on the same workgroup)
netbios name = UBUNTU_SERVER  <-- This is the name of the computer as seen by the network
security = SHARE
auth methods = guest
domain master = No
wins support = Yes

Then just restart Samba and hopefully you can map the network drive on the remote system

Weird, Verizon must be blocking the server for some reason -- I can't get to it.  Your quote pointed me in the right direction.   Both my  global and user share configurations were screwed up.  I hadn't checked carefully enough with what I had done before on the Fedora box.  It is working fine now.  

Thanks for the help,

Don

---

### Post by bigken on 2007-06-25
sudo smbpasswd -a yourname
sudo smbpasswd -e yourname

---

