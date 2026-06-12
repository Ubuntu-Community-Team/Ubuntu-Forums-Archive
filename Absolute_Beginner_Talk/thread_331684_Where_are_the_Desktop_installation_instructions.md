---
title: "Where are the Desktop installation instructions???"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by bazsl on 2007-01-04
I was able to install and configure 6.10 server for static IP addressed, multiple NICs and Samba without too much trouble thanks to the Server Guide. However, I can find only the most cursory instructions for configuring networking (which does not work) and nothing about installing and configuring Samba. Is there another manual?

My first problem is to get connected to the network. I went into System | Administration | Networking and configured both NICs for static IP addresses using the same settings that I used for 6.10 server (except for the last digit of the IP addresses) and restarted. When I try to ping any other computer on the network I get "destination host unreachable".

Can someone point me to the right manual or suggest why I cannot connect to the network?

Thanks

---

### Post by bazsl on 2007-01-04
I did get networking to work (just after I posted my message naturally) but I still need to find the isntructions to get Samba installed and working. Can I do that from a terminal windows using the instructions in the Server Guide? Thanks again.

---

### Post by macogw on 2007-01-04
You should be able to do it from the terminal.  Just ctrl alt f1 and you'll get a big blank terminal like you see in the server.

---

### Post by bazsl on 2007-01-05
Thanks. I now have Samba running in Desktop.

---

### Post by macogw on 2007-01-05
By the way, where'd you find out how to do Samba?  I got a call last week from one of the techs at work asking if I knew how to set it up.

---

### Post by bazsl on 2007-01-05
The Ubuntu Server Guide has a pretty good chapter on configuring Samba. The one thing that is missing is an example of what has to be added to smb.conf to share a specific directory. I configured Samba once before on a CentOS system and they had some samples in the smb.conf file as comments that helped me so I used the same examples in Ubuntu and it worked. To get what I wanted required the following steps.

Add the Samba usernames and passwords that I needed using:

smbpasswd -a username

Add the following lines to smb.conf

interfaces = eth0
interfaces = eth1

[tmp]
  path = /temp
  writeable = yes
  valid users = user1, user2

The two interfaces = lines are required because I have two NICs and want Samba to bind to both of them. If you have a single NIC I believe you can omit both of those lines. The [tmp] entry and the lines that  follow show how to share a directory that is writeable and only accessible to the listed users. HTH.

---

