---
title: "home network woes"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by sk0r on 2006-11-18
ok, i am running mepis 6.0, my wife's rig is running ubuntu 6.10 edgy.  both machines are running BEAUTIFULLY, but i am unable to browse the network.  From the ubuntu box, i can SEE the mepis box, but i cannot move files at all.  from the mepis box, i CANNOT see the ubuntu box at all.   i have been googleing and trying everything i can find...to no avail.  so that's where i stand, unable to retrieve my files i backed up onto my wife's box.  Tongue

any help would be MOST appreciated

-ron

---

### Post by paulmilliken on 2006-11-18
You have several options for communicating between computers, including:
1.  ssh or sftp
2.  samba (the default type of networking for windows computers)
3.  nfs
etc...

I think you were attempting to use samba.

Almost certainly, the reason you cannot see your Ubuntu computer is that you don't have the samba server installed.  Type "ps axu | grep smbd" on your Ubuntu computer and if you get no output then you need to install smbd.  To do this go to System | Administration | Synaptic Package Manager.  Then search for smbd.

Once you have installed smbd you need to edit a file called /etc/samba/smb.conf to share one or more of your directories (do this as root eg. type "sudo gedit /etc/samba/smb.conf" or similar for whatever text exitor you prefer).  The smb.conf file is well commented with examples of how to share a directory or printer etcetera.  However, the smb.conf file is long and has a lot of options so you might want to search for other information on the internet describing how this file works.

Also, try comparing the output of "ps axu | grep smbd" and "less /etc/samba/smb.conf" between your two computers and note the differences.

Paul

---

### Post by zgornel on 2006-11-18
An alternative to Samba is NFS and it is more linux related. Samba is more widely used for linux-windows interoperability but in the end both NFS and Samba do the same things. Try this NFS tutorial: [http://learnlinux.tsf.org.za/courses/build/net-admin/ch12.html](http://learnlinux.tsf.org.za/courses/build/net-admin/ch12.html), it might help.

---

