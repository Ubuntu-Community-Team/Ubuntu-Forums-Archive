---
title: "Accessing ubuntu from windows - pwords"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Chewy22 on 2006-11-15
Hi,

I can access ubuntu from Windows XP over a network by typing (in Windows) eg- \\linuxbox but it asks me for a username and password.  Now, I do have a login username and password for the linux box, so is that the username and password that I'd use?  Because if it is... It doesn't work... Can anybody help?

Thanks in advance!

Regards,
Chewy

---

### Post by joshsherman on 2006-11-15
First off, I'm no Samba expert, but I can point you in the right direction.  Typically all the user account stuff is set up within the samba config (possibly located at /etc/smb/smb.conf).  Look into that.  I know you can set it up to use your Linux user accounts to authenticate, or use a different file to house the users and password, or without any authentication at all.

Best of luck, and please pardon my vaugueness on the matter.

---

### Post by dannyboy79 on 2006-11-15
yes, you need to add a samba user. are the usernames and passwords the same on each computer? if not, I would strongly suggest doing this cause if not than you're gonna need to create a user on your ubuntu box that matches the username on your winbloz box. the way you add a samba user is by doing this from a terminal session, sudo smbpasswd -a usernamehere, then it'll ask you for a password twice. after that do sudo smbpasswd -e usernamehere. that'll enable that user. now this user you add to the smb password database has to already be a user on the ubuntu box, hence why i suggested that you make sure the users are the same on winbloz and ubuntu (and password for that matter) once you do this, you're going to want to do, sudo /etc/init.d/samba restart, then sudo /etc/init.d/samba reload. what all these steps have done is added a user for your ubuntu box to authenticate against. if I were you I would just suggest looking for a samba guide as it tells you how to setup your entire smb.conf file which isn't in /etc/smb/smb.conf as the other user thought, it's located within /etc/samba/smb.conf, he was close and did say he was only guessing. anyway, there is a great guide which i used here, [http://www.debianhelp.co.uk/samba.htm](http://www.debianhelp.co.uk/samba.htm). it's for debian which is what ubuntu was built on I believe. good luck, i am at work so if you have more q's I might not be able to answer them until later as I really should be working on what I am getting paid for. he he.

---

### Post by Super King on 2006-11-15
This is the guide I used and it worked great:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)

---

### Post by Chewy22 on 2006-11-15
Hi everyone,

Thanks for your speedy answers!  Anyway, I've followed the guide suggested by *Super King*.  The only problem is when I type **sudo smbpasswd -a system_username** and enter in a password for it, it says: **Failed to initialise SAM_ACCOUNT for user thedell. Does this user exist in the UNIX password database?  Failed to modify password entry for user system username**  What do I do from here?  I'm sorry about all this, I'm a total n00b to Ubuntu.  Hopefully I'll learn a few tricks along the way!

Thanks guys!
Chewy

---

### Post by Chewy22 on 2006-11-15
Sorry everyone! I've figured it out by following [http://www.debianhelp.co.uk/samba.htm](http://www.debianhelp.co.uk/samba.htm) properly.  I didn't realise that you had to type "sudo" before every command and that # makes the command.. umm.. "inert".  I only figured it out after reading the smb.conf file and discovered all the documentation has # before it! ](*,) thanks for all your help!

Regards,
Chewy

---

