---
title: "openssh-server Key Authentication With Putty Problem"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-10-03
I have a server (which is also my desktop computer) running openssh-server. I am trying to secure it using public/private key pairs. It is working fine in Ubuntu but i am totally stuck when it comes to using Putty (On my Windows boxes) to connect. I have it set up so you need an Authenticated KeyPair to login to SSH.

How do i go about generating a public key and private keypair (Hopefully i can take my Private key about on my USB Pen Drive so i dont need 5 Keypairs) using Putty on Windows (XP)?

---

### Post by bodhi.zazen on 2007-10-03
You need to import the key to putty :

[http://linux-sxs.org/networking/openssh.putty.html](http://linux-sxs.org/networking/openssh.putty.html)

---

### Post by kevdog on 2007-10-03
Just off the top of my head.

Here is what I would do
You leave the public key (and private since it doesnt matter) on the server.  The public key is denoted by id_rsa.pub or id_dsa.pub and the private key is id_rsa or id_dsa depending if you used the rsa or dsa algotithm to generate your key pairs.

Take the private key (id_dsa), copy it to your USB stick and then bring it over to your windows machine.  I remember something about putty having to convert the openssh format key into its own format.  Open up the puttykeygen program and import your private key that you have brought over to your machine.  It might say it needs to convert the key to its own format -- select yes, and then save it under a different name such as id_rsa_putty.

All you need to do now is use the id_rsa_putty key when using putty or winscp to connect to the ubuntu server.

I think that should cover it.

Another way to do it would be to make the putty ssh key pair, copy the public key to your USB stick and bring that to your USB server.  Put the public key in .ssh directory.  Then cat id_rsa.pub >> authorized_keys (which basically appends the putty key to the authorized keys file).  Note that the putty key might be called something other than id_rsa.pub.

---

### Post by master_kernel on 2007-10-03
Import the key in PuTTY.

---

### Post by bobbocanfly on 2007-10-03
Got it. Thanks. Forgot about just copying the original key i had made. Thanks again.

---

### Post by BlizzofOZ on 2008-03-18
> **kevdog said:**
> Just off the top of my head.

Here is what I would do
You leave the public key (and private since it doesnt matter) on the server.  The public key is denoted by id_rsa.pub or id_dsa.pub and the private key is id_rsa or id_dsa depending if you used the rsa or dsa algotithm to generate your key pairs.

Take the private key (id_dsa), copy it to your USB stick and then bring it over to your windows machine.  I remember something about putty having to convert the openssh format key into its own format.  Open up the puttykeygen program and import your private key that you have brought over to your machine.  It might say it needs to convert the key to its own format -- select yes, and then save it under a different name such as id_rsa_putty.

All you need to do now is use the id_rsa_putty key when using putty or winscp to connect to the ubuntu server.

I think that should cover it.

Another way to do it would be to make the putty ssh key pair, copy the public key to your USB stick and bring that to your USB server.  Put the public key in .ssh directory.  Then cat id_rsa.pub >> authorized_keys (which basically appends the putty key to the authorized keys file).  Note that the putty key might be called something other than id_rsa.pub.


I did the above... created a id_rsa, id_rsa.pub and authorized-keys and CAT id_rsa.pub to authorized_keys.

Next is where my confusion comes in... which file do I copy to my usb device?  I think it is the private id_rsa file, correct?  Can I connect my usb drive to the server?  How do I see it and how do I copy the file to the drive?  
Can I copy the file to my usb drive using Samba?  I tried this but I get an error of:
"Cannot copy id_rsa: Access is denied   Make sure the disk is not full or write-protected and that the file is not currently in use"
I am able to copy the id-rsa.pub file over, so my guess is a permissions problem on that file.

Next, once on the usb drive, I can connect to my Win XP computer and open the id_rsa file with puttygen?

---

### Post by BlizzofOZ on 2008-03-18
Anbody help my questions above?

---

### Post by bodhi.zazen on 2008-03-19
The easiest way to get the key to the server is with ssh-copy-id

```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@host
```

Then import the id_rsa private key to putty using the link I gave in my post above. You will need to save the putty key with the same name, ie id_rsa so take care not to overwrite the origional.

---

### Post by kevdog on 2008-03-19
> I am able to copy the id-rsa.pub file over, so my guess is a permissions problem on that file.

Next, once on the usb drive, I can connect to my Win XP computer and open the id_rsa file with puttygen?

My permissions on my id_rsa key are 600, my id_rsa.pub permissions are 644 so I guess you could temporarily try changing permissions:
cd ~/.ssh
chmod 644 id_rsa

Copy the id_rsa file to your USB stick and import it into putty-gen.  You are on the right track!

---

