---
title: "SSH Key Help"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by stormblue on 2006-08-11
I'm trying to get my SSH key's to work.

I've generated the keys and have both my public and private keys in place.

I have changed my port to 2575.  I can connect using SSH using the -p argument.

I can't get scp or ssh-copy-id to work. I think it has to do with port 2575 and I've tried to define it both in terms of -p port and IP:port and neither works.

Any ideas on how to get started to get this to work?

---

### Post by subzero79 on 2006-08-11
Are you trying to get an ssh server to work?

if it so..then are this lines in /etc/ssh/sshd_config

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile /home/user/.ssh/authorized_keys

uncommented?

Then in the ~/.shh/ rename your public key(generally id_rsa.pub or id_dsa.pub) to "authorized_keys"

---

### Post by stormblue on 2006-08-11
The server is up and running. I can connect to it.  Thank for the tips.  I'll see if I can get it to work.

here is from my config file

```
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys
```

How do I get my public key onto the server.  I tried using scp, but I couldn't get it to work.  What does the %h mean?

---

### Post by patrick295767 on 2006-08-11
It can happen also sometimes you may need to remove the key to restart from beginning:
```
cd 
rm -rf .ssh    # remove the key and .ssh folder warning
ssh pcdistant
```

---

### Post by stormblue on 2006-08-11
Patrick,

I don't think that's the solution, as I haven't even put the key on the server. Which I believe I'm supposed to do with scp, but am unable to do.  The public key goes on the server correct and the private key stays on the client machine, right?

---

