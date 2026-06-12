---
title: "File Server"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-12-09
Is there some guide on how i can setup a file server for peer to peer that i can use around my house its going to be ona  7.10 setup so can someone please help me

---

### Post by cmnorton on 2007-12-09
I don't know if there is a guide, although Ubuntu documentation is really good, and you could look there and Google SAMBA.

How secure do you want this to be? Who would be accessing the file server? What kinds of clients will access these shares? I am asking questions like these, because, once you've set up SAMBA, answers to these questions would be a start in setting up shares. 

If SAMBA is not already running on a 7.10 client, then you can probably download what you need through Synaptic and then start configuring it. There's lots of info on the internet on configuring the SAMBA conf files. Offhand, I've forgotten how you get to Samba in Ubuntu through the GUI, unless it's through Administration-->Servers. I'm not at an Ubuntu system right now.

---

### Post by fedex1993 on 2007-12-09
it will mostly be just me and my other 2 desktops. i just want to read and write and copy to 2 directories MUSIC and ISO. the computers are all in the same room i just want to acess those files

---

### Post by Threbus5 on 2007-12-10
Hi,

HermanAB already answered your earlier post for the same subject.

Here are the links that he suggested:
--------------------------------------------------------------------------------

[http://us3.samba.org/samba/](http://us3.samba.org/samba/)
[http://us3.samba.org/samba/docs/man/...TO-Collection/](http://us3.samba.org/samba/docs/man/...TO-Collection/)
[http://news.samba.org/users/samba_at_home_how_to/](http://news.samba.org/users/samba_at_home_how_to/)
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)


Why not set one of the machines to share a directory and select on the client to access that IP from the Places menu option? Ubuntu should then force you to choose a shared file type and install SAMBA share if necessary.


Good luck

---

### Post by BillDozer on 2007-12-10
Is it for a Linux clients only, then I would go with NFS. Check out this link for installing [https://help.ubuntu.com/7.10/server/C/network-file-system.html]("https://help.ubuntu.com/7.10/server/C/network-file-system.html").

Otherwise go for SAMBA.

---

### Post by hyper_ch on 2007-12-10
Do you need secure connections (encrypted ones)? If so you could use SSH/SSHFS/SCP

If not, you can use NFS or SAMBA.

---

### Post by fedex1993 on 2007-12-10
> **BillDozer said:**
> Is it for a Linux clients only, then I would go with NFS. Check out this link for installing [https://help.ubuntu.com/7.10/server/C/network-file-system.html]("https://help.ubuntu.com/7.10/server/C/network-file-system.html").

Otherwise go for SAMBA.

net work file system seems alot better for me thank you alot. Know i can finally get my server/desktop2

---

### Post by fedex1993 on 2007-12-10
well can i mount a NFS directory to a partition of /media/(randomname)

---

### Post by hyper_ch on 2007-12-11
Are both systems linux?

---

### Post by fedex1993 on 2007-12-11
n ever mind solved i found out after some help

---

