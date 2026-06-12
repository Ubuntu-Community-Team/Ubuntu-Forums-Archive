---
title: "Samba - Help"
date: 2012-05-02
forum: Any Other OS
---

### Post by chimi_12 on 2012-05-02
Good afternoon to all!

I have installed a CentOS 5 server, which is used to host data from one system (an old system) that was developed in FoxPro, so its databases are simple files. These files remain on the CentOS in a folder that is shared over the network using samba. Only one user was configured to access this folder, because what we wanted was not to allow free access to the folder.

The windows PC's (WinXP) that working with the system, have mapped the folder using a network drive that plugs after every reboot and remember user data and password to reconnect the unit.

So far so good, the bad thing is that (and still do not understand why) in the Windows PC's, network drives mapped apparently "lose" data access to the shared folder on the server, so you have to go back to configure the network drive and the shortcuts to executables, first happened with a few and then it happened again but this time in 10 pc's at once.

Still do not know if the windows PCs that have the problem or if the samba server has a trouble and reject connections. 

I hope you can guide me a little with this problem. Greetings!

---

### Post by chimi_12 on 2012-05-08
Well, think it was a domain problem. I changed the smb.conf file to make the samba server to be part of the same workgroup as all PC's. :lolflag:

Now the windows PC's have no problems.

---

