---
title: "connect to shared folder"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by cooper on 2006-08-15
Hi Guys

After a struggle i have xubuntu running.

I would like to share a folder to be found on a windows network

I have gone into system file settings and added a folder

path /home/cooper
share with SMB
Name: test1

i can see the ubuntu connected to the netork under the domain.

when i try and open this i get asked for a username and password

this fails, im using my admin password that i used to set up the ubuntu but its not working.

---

### Post by aeiah on 2006-08-15
i believe you need to set up a user account on your ubuntu box that has the same username and password as the windows pc you're trying to connect to it with, and then connect with that. there are decent details in the samba howto threads, and in the thread detailing how to set up samba to share a drive with a vmware virtualised windows xp.

---

### Post by cooper on 2006-08-15
i have set up a user account with the same username that i use on the windows 2003 server im trying to connect from and still cant get in.

Have you a link to a tutoral i can use as i can find what i need to help me get past this.

Thanks

---

### Post by TooDamFast on 2006-08-15
same problem here!  i love these forums.  would like to see how fix the password problem.  links would be great!

---

### Post by dannyboy79 on 2006-08-15
You guys say you added a user, are you saying you added a smb user buy issuing the following command, smbpasswd -a user_name? Also, have you configured your smb.conf file? I am still pretty much a newbie but this is something I have working between my xbox, my ubuntu box, my xubuntu laptop, and my winxp box! I am at work right now but if you send me a private message with a specific question I'll try and respond later tonight. Good luck guys. Just so you both know, Goggle can answer every single question you will ever have!!!!! I have found an excellent link for you guys for setting a home network file and print server. Use what you need from this forum and disregard the rest but here is the link, [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/54415-fileserver-samba-printserver-cups-howto.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/54415-fileserver-samba-printserver-cups-howto.html). Talk to you later.

---

### Post by cooper on 2006-08-16
The guide you shown isnt setting up using a gui also will give you a static ip.

Im trying to network the drive to my windows 2003 server.

When this is networked wanting to be able to make a complete back up to the hardrive on the ubuntu.

I can see the ubuntu computer under view network places mmicrosoft network and in the doamin.

but when i try and access i dont know the user name and password

on the ubuntu computer i have gone in 

system -user and groups- add user and put the same username and password as the administrator password on the windows 2003 server.

when i try and access the ubuntu computer through the windows server i put this username and password in but its not valid.

can you see where im going wrong?

---

### Post by cooper on 2006-08-16
been trying to use the guide and i dont get it??

so i goto 


application

system 

shared folders

=====================

add folder

path home/cooper

share with smb

name backup

comments  back up of server

no tick - rezad only

tick - allow browsing folder


GENERAL WINDOWS SHARE SETTINGS

host: description backup

domain;  springmead

use win server "school"



============================================


as i have put in my last post the username and password for the server have been used to set up an account on the ubuntu computer.

can see the folder fropm the server just can access as its not acepting the password


:(

---

