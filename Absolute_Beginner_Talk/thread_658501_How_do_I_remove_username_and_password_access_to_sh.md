---
title: "How do I remove username and password access to shared folders"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by razorbak on 2008-01-04
I have shared a folder over my network but when I try to access it frommy vista PC I have to enter a user name and password (which I don't remember havingset up actually).
How do I remove the username password protection??

Thanks

---

### Post by bunnynuts on 2008-01-04
I hope that this will be of some help. I'm assuming that you are attempting to access a samba share with windows. If this is the case you should be able to edit the samba config file and allow guests setting "guest ok = yes".

Additionally, there is a way to match the samba user with the windows user (passwords must be the same and there is something with the work group on the windows machine). I haven't done this for a long time so I will have to get back to you on that part. 

Let me know if this is (or is not) what you are looking for.

---

### Post by razorbak on 2008-01-04
yes this is what I am trying to do.

I did what you suggested but still the same
How do I set up smb users?
I have tried typing:

sudo smbpaswd -a <username>

but after entering a password a reentering it I get a failed to modify password message

---

### Post by bigken on 2008-01-04
also type this sudo smbpasswd -e <username>

---

### Post by bunnynuts on 2008-01-04
EDIT: Someone else recently had the same question and received a very concise/helpful answer
[http://ubuntuforums.org/showthread.php?t=658056](http://ubuntuforums.org/showthread.php?t=658056)



It has been too long since I have played with my samba config...so in looking up how to access it on a local network I came upon the following:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Is a bit old, but I couldn't find anything disagreeable. I believe that in the config file that Stormbringer has, under 'MyFiles' where guest ok = no if you change that one to 'yes' then your share is accessible by all on the network without passwords. However I have not ever wanted to allow such so I'm not certain. The rest of his post shows you how to allow windows to access the share without entering the password again. 

If there are problems with this or you have questions just ask and it will likely motivate me to start playing with my own files again (which is what I really enjoy about linux).

---

### Post by razorbak on 2008-01-05
> **bigken said:**
> also type this sudo smbpasswd -e <username>

tried that and:

USER@AMDLINUX:~$ sudo smbpasswd -e dv2535
[sudo] password for USER:
Failed to find user dv2535 in passdb backend.

---

### Post by bigken on 2008-01-05
its sudo smbpasswd -a <username> then sudo smbpasswd -e <username>

its smbpasswd not smbpaswd

---

### Post by razorbak on 2008-01-05
Yes passwd is what  I typed and nothing much happened

---

### Post by bigken on 2008-01-05
when you type sudo smbpasswd -a yourname 

you should be asked to type new smb password:

type your password nothing will show just type it

ken@stratocaster:~$ sudo smbpasswd -e ken 
Enabled user ken.
ken@stratocaster:~$ sudo smbpasswd -a ken 
New SMB password:
Retype new SMB password:

---

### Post by razorbak on 2008-01-05
AAAAHHHGGGGHHHGHHG!

I hadn't created the users in UBUNTU!!

Getting there slowly

Thanks

---

