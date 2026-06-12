---
title: "Synaptic problem"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by Adramelech on 2006-03-17
HI

Im getting this error since a week or probably more.

W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)

All seems to work properly but isnt a security server important? was the server removed? Im worry about being an official ubuntu server with the security word on it, can someone explain me why this is happening and how can i fix it?.

thanx

---

### Post by Xecuter on 2006-03-17
Try "sudo apt-get update" and then try it again.

---

### Post by Aewheros on 2006-03-17
You propably have the wrong repository adress....

Re-add it, or edit */etc/apt/sources.list* manually.

---

### Post by Adramelech on 2006-03-17
FIXED 

thank your guys

If someone interested i did it this way.

I did sudo apt-get update and got a GPG error so I follow the idea on this site  [http://www.psychocats.net/linux/sources:](http://www.psychocats.net/linux/sources:)


Back up the sources.list: sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 

Then edit the sources.list by typing sudo gedit /etc/apt/sources.list and delete everything. 

sudo apt-get update with your empty repositories list. 

Finally, sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list 
sudo apt-get update

=)

---

