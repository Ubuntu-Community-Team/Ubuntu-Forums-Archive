---
title: "SSH help"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by kcallison on 2007-09-14
I have a file server running 6.06.1.  I just set up the sshd.  I want to use PuTTY from Windows XP to remotely log into my server.  What do I have to do to get the public key over to Windows?

Thanks, 

kcallison

---

### Post by scxtt on 2007-09-14
download puttygen for windows and generate an rsa/dsa key that you can put in the ~/.ssh/authorized_keys file on the Dapper openssh server.

---

### Post by kevdog on 2007-09-14
The public key goes on the server .....

The private key goes on the client ....

Putty uses its own modified format that is slightly different than the openssh format (dont ask me how).

So this is what I would do

If on the server do the following:
ssh keygen -t rsa -b 2048

The b argument is bits -- you can use 1024 or 2048

Two keys will be generated inside ~/.ssh -- id_rsa and id_rsa.pub

Then
cd ~/.ssh
cat id_rsa.pub > authorized_keys

Copy or just move the id_rsa key onto a USB stick and bring it over to the windows box.
From within windows start the putty key gen program (I forget what its called exactly).  Import your private id_rsa key inside putty (you will get a warning about incompatible format, and then it will ask if you want to convert the key to putty's format.  Select yes).  

Save the public and private key -- I renamed them to id_rsa_putty and id_rsa_putty.pub so I dont confuse the two different keys.   In order to make the public key I think you have to export the public key (Im doing this from memory so I cant remember exactly).  Anyway copy the id_rsa_putty.pub key back on the USB stick and then back over to the ~/.ssh directory.  

Then inside the ~/.ssh directory
cat id_rsa_putty.pub >> authorized_keys

Now basically I dont know if you want this or not, but you have two private keys that will work on the machine -- id_rsa and id_rsa_putty.  Usually you dont want more than one key to work, however the reason for this is b/c of the way putty deals with the keys.  

The id_rsa key is for linux/cygwin machines -- You would use it for example  to ssh to the server itself while on the server -- ie ssh localhost  (Often useful for testing when things go bad).  

The id_rsa_putty private key is to use with putty while on windows machine.

An alternative to windows putty, would be to install cygwin on windows, however this doesnt give you the graphical startup, is not a portable program (meaning if you ever wanted to ssh in from a totally different box other than the two client/host machines, you couldnt copy cygwin onto a USB stick ***DISCLAIMER -- you can but its a pain, whereas with putty's small size, this is easily a portable application), however using cygwin on windows is as close as you can get to linux, and you dont need to do this messy key translation.

I hope everything makes sense

---

### Post by hyper_ch on 2007-09-14
why use keys at all?

In putty you just connect with an existing system user and password and it works... the keys are only needed - IMHO - if you want to login without password.

---

### Post by kcallison on 2007-09-14
kewl.  Thanks for the help.

kcallison

---

