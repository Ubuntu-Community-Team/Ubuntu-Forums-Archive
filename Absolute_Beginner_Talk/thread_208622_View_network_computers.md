---
title: "View network computers?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by FLCLFan on 2006-07-03
How do i view the computers on my network(all the computers have windows xp) with Xubuntu?

---

### Post by HeDanny on 2006-07-04
I would very much like to know this as well. This computer I am typing from is pure Xubuntu.  I just checked and I have samba installed.  That is what you need to talk to Windows XP, yes?  Do I need to turn Samba on or something?

I can not see the other PCs at all from this machine, nor does this machine show up in my workgroup on the winXP machines.

---

### Post by Apple 101 on 2006-07-04
*gksudo gedit /etc/samba/smb.conf*

Set your workgroup where it has the option for it.  It is set to the non-imaginative "workgroup" name.

---

### Post by Dazaablack on 2006-07-04
Careful for some reason when i installed dapper 6.06 it set the default workgroup to MSHOME. (the default for win xp home).
The default for xp pro is WORKGROUP).

I take it you are trying to get a file off a MS server/workstation on YOUR NETWORK.

Easy. Select Places, then Network Servers from the Ubuntu bar thingee.

If you want to setup shares from the Ubuntu machine for the windows machines to access (which is what i got). Then you gotta edit the smb.conf file in /etc/samba/

There are so many tutorials on how to do this.
Heres one i found useful:
[www.samba.netfirms.com/addusers.htm#restart](www.samba.netfirms.com/addusers.htm#restart)

please note the dude going through it is using SuSE or Redhat/Fedora.
So obviously when you restart you dont need to run the /etc/rc.d/init.d/smb restart

you just 

sudo /etc/init.d/samba restart

Heres an idea on how to share a folder on the network (from my smb.conf)
[ftp]
comment = stuff
path = /home/leech/ftp/
writable = yes
browseable = yes
valid users = daz,leech

this is a folder on my FTP site its shared on the MS network as a share called FTP.
 
PS if you know how to fix my cdrom problem let me know. I think its dead!

---

### Post by HeDanny on 2006-07-09
After much fiddling I managed to finally somehow get my xubuntu machine onto "PASTURE" (the name of my windows workgroup).  U have been at it so long I am not quite sure what it was I did that finally made it work..  I will have to back up my SMB.conf so I do not have to go thru this again! :)

I now has another problem.  All the computers running XP can see and browse my xubuntu machine, but I can not find an ap in xubuntu that allows me to browse the XP computers.  The file browser is is THUNAR.  Is network browsing in Thunar somewhere and I can not fint it? or do I need something else.

The ultimate goal here is to be able to play media that is on my main XP machine on here.  I can't really do that if I cant browse to it. heh.

---

### Post by Apple 101 on 2006-07-09
Look at this page: [http://wiki.linuxquestions.org/wiki/Samba](http://wiki.linuxquestions.org/wiki/Samba)

---

### Post by koshari on 2006-07-09
put an entry in the fstab file to automaticly mount the windows share you want to use for media at boot time, 

also use cifs to mount the share, 

then you will have no problems with the 10000 file limitation of smb mount, 

then chmod the mount with 777 or what ever permissions you want and thuunar will treat it simply as a local folder.

oh and you can install linneigborhood through synaptic to browse samba networks,

---

