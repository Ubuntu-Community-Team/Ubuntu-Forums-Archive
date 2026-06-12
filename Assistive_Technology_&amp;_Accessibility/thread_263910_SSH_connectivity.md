---
title: "SSH connectivity"
date: 2006-09-23
forum: Assistive Technology &amp; Accessibility
---

### Post by crokett on 2006-09-23
I installed the ssh server. when I try to log in from a remote machine I get the errror:

no connection could be made because the target machine actively refused it

Where should I be looking to fix this?  I have the password authentication option enabled in the config file. Do I need to do anything with keys?

---

### Post by wieman01 on 2006-09-23
There is a good documentation:

[http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-4.html]("http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-4.html")

Your problem is related to authentication, etc. You need to teach the host machine to "trust" your client.

---

### Post by crokett on 2006-09-23
Thanks.  So just to make sure I understand from reading that doc... I create a public and private key pair.  Private key goes on my laptop and is used by my ssh client, public key file gets put the server and added to the key file?

---

### Post by wieman01 on 2006-09-23
Yes, this is correct. That's the way I have set it up as well.

---

### Post by crokett on 2006-09-24
Ok... so I did: ```
kgen -f <file> -t rsa
``` and got a <file> and a <file>.pub
then I did: ```
touch /home/<me>/.ssh/<akeyfile>
```
then I did: ```
cat <file>.pub >> <akeyfile>
```
then I modified sshd.config to point authorized keys to <akeyfile>
then I imported the <file> onto my ssh client.  still get the same error.  I have in /etc/ssh an ssh.config and an sshd.config.  Which does ssh use?  Both?  Do I need to add my laptop as a valid host or something?

---

### Post by wieman01 on 2006-09-25
_2 questions:_

1. Could you please post the exact contents of the error message?
2. Do you have a firewall (e.g. Firestarter) by chance? Sounds like you do.

---

### Post by crokett on 2006-09-25
Error message:
Connection Failed Connect() Failed.  Windows Error 10061: No Connection could be made because the target machine actively refused it.

As far as a firewall, unless Ubuntu installed it by default I didn't install it.  As far as I knew Ubuntu does not install a firewall.

---

### Post by wieman01 on 2006-09-25
What's your setup then? Is a Windows machine connecting to your SSH server? Frankly I don't have a clue (yet) why you have this kind of problem. But perhaps we get there while we are talking about. :-)

---

### Post by crokett on 2006-09-25
> **wieman01 said:**
> What's your setup then? Is a Windows machine connecting to your SSH server? Frankly I don't have a clue (yet) why you have this kind of problem. But perhaps we get there while we are talking about. :-)

Yup.  Setup is Ubuntu Dapper Drake desktop install with SSH server.  Client is Windows XP laptop with Bitvise Tunnelier client.  I imported the private key onto the client but still get the same error.  Also tried putty client, it errors out as well.  If it means anything, I tested this sitting at my ubuntu machine and I can start an ssh session from there.

I want to get this working so I can do some remote admin from in front of the TV - I'm lazy. ;)

---

### Post by wieman01 on 2006-09-25
Could check out this file?
> gedit /etc/ssh/sshd_config
Please post it.

---

### Post by crokett on 2006-09-25
Will do when I get home.   Shoulda thought of that this morning.  

Quick question... ssh_config is for client side config and sshd_config is for server_side?  Just wondering what the difference is.  I have both files.

---

### Post by wieman01 on 2006-09-25
Another thought: Have you enabled port forwarding on your router (although I cannot remember that you have to do it... not in front of my own computer...)?

---

### Post by wieman01 on 2006-09-25
> **crokett said:**
> Quick question... ssh_config is for client side config and sshd_config is for server_side?  Just wondering what the difference is.  I have both files.
Yes, that's right.

The thing is that the mentioned error message indicates that the client (Windows) cannot find a SSH service running on the machine or port. So I suspect that this has nothing to do with authentication but the fact that Windows simply cannot find any SSH service running on it.

Also check if your Windows machine has got a firewall...

---

### Post by crokett on 2006-09-25
> **wieman01 said:**
> 
Also check if your Windows machine has got a firewall...

I am such a knucklehead sometimes.... my telnet access to my ubuntu box worked so it never occurred to me the firewall was in the way.  I shut it down and now I am connecting just fine.  :)

---

### Post by wieman01 on 2006-09-25
:-) Happens... I know Firewalls can be a stumbling-block... Let us know if you have any other question relating to this topic.

---

