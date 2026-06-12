---
title: "networking to pc"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by frenchsquared on 2007-12-30
OK say I have a home network with 5 computers all but 1 pc
I can see all the computers on the network from ubuntu 
however they want a: 
username
domain
password

so how do I figure out what these are

I can log onto one computer its a dell but it is running WAMP
and is a server so anyone can access it
no password needed

---

### Post by HereInOz on 2007-12-30
I think, if you are attempting to access a Windows share from Ubuntu, then the machine on which that Windows share resides needs to be set up with a username and a password.

The standard install of XP will only give you a username, and no password, and I think, from previous experience, that this will cause you difficulties.

I use the workgroup name of the Windows network as the domain name, and enter the username and password for the Windows machine.  If you set up the same username and password on each Windows machine, this will obviously make life a lot easier.

---

### Post by frenchsquared on 2007-12-30
that works for the dell server but not on the other machines, must be vista will play with them

so Can I make the windows machines see the ubuntu?
how do I create a shortcut to the folders on the dell?
the dell is my network share used to move everything

---

### Post by HereInOz on 2007-12-30
You should get a folder on your desktop when you connect to the Windows share.  If you want to mount that share permanently, and have it available as a network file source, check out:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

This will allow you to fire up your Ubuntu machine and see the Windows share on the Dell as the folder you specified.

To see the Ubuntu files from the Windows machines, check out:

[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

and/or:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

This is another good resource for mounting Windows shares: 

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

Hope this helps.

---

